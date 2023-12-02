---
title: 怎样快速了解数据库中的表
author: yuanfan
date: 2023-11-17T23:13:59+0800
slug: system table
categories:
  - R
tags:
  - R
draft: no
---

<!--more-->

在与数据打交道的日常工作中，有时候我们需要快速了解数据库中的一张或几张表，然后才能去探索和分析数据，但也有些时候我们需要快速了解整个数据大仓库中的一个“层”。在一切开始之前，需要先简单梳理一下数据分层的基本概念。

如下图所示，在一个数据中心（或称数据平台）上，源自不同业务系统数据库的数据将会集中存储到一起，在经过加工后，供给不同的业务方使用。

1. 将不同数据库（DataBase）中的数据通过 ETL（extract 抽取、transform 转换、load 加载）同步到 ODS 层（Operational Data store），其中需根据不同数据库的特性、需求的永久或临时、实时或离线等特点选用不同的 ETL 方式。

2. 再将 ODS 层的数据加工到 DW 层（Data Warehouse），通常按照不同的业务系列对散乱的数据做基础的整合，便于在不同的需求中可以重复利用。

3. 继续将 DW 层的数据加工到 DM 层（Data Market），根据每个独立的需求开发数据，通常将结果储存在有固定命名规范的事实表中。

4. 最后将 DM 层的数据从后端供应给前台使用。

<details>
<summary>查看绘图的代码</summary>
<pre><code>

```r
library(DiagrammeR)
grViz(diagram = "digraph {
  graph[rankdir = LR]
     
  node[shape = rectangle]
     DB1[label = 'DB1\n 数据库1']
     DB2[label = 'DB2\n 数据库2']
     DB3[label = 'DB3\n 数据库3']
  node[shape = circle]
     ODS[label = 'ODS层\n 数据存储']
     DW[label = 'DW层\n 数据仓库']
     DM[label = 'DM层\n 数据集市']

 {DB1, DB2, DB3} -> ODS[label = 'ETL']
 ODS -> DW -> DM 
}")
```

</code></pre>
</details>

![](https://yuanfan.rbind.io/images/2023/2023-11-17-01.png)

一般情况下，DW 层和 DM 层会是同一个数据库下的不同用户，这样在 DM 用户下访问 DW 层的表不需要跨数据库。

需要注意的一点是，由于实际工作中也会根据开发、测试、运维等流程隔离出开发环境、测试环境、生产环境，不同的环境对应的服务器 IP 地址和端口号也不同，通常互相不能连通，而这三个环境下的表也未必是完全一致的，如果要使用最真实的数据，应该是去了解生产环境上的表。

于是乎，当我们确凿无误地知晓需要登录哪个环境下的哪个用户去了解相关的表以后，问题的解决方向才初露端倪。

# ORACLE

ORACLE数据库有一系列系统表（system tables），可用于查询库中各类对象的元数据信息。我们可以通过查询系统表来批量获取表信息，快速梳理各数据表中内容，如表的字段名称、字段含义、字段类型、精度以及索引、主键外键，还有表之间的关系。

其官网上有介绍[系统表](https://docs.oracle.com/database/timesten-18.1/TTSYS/systemtables.htm#TTSYS346)的文档。按照不同的权限范围，系统表又分成了 DBA、ALL、USER 三种，分别对应可查看整个数据库、可查看当前用户可访问的一切数据、只可查看当前用户下的数据。当我们登录数据库用的是 DM 层用户，又想查看 DW 层的表时，应该选择查看 ALL 这一类系统表。

## 表与列（all_col_/all_tab_）

如果有足够权限的话，就可以在执行下面这段脚本后，得到整个 DW 层的所有表名、表注释、字段名、字段注释、字段类型等信息。

```sql
select t.owner,
       ac.COLUMN_ID,
       t.table_name,
       c.comments,
       ac.DATA_TYPE,
       ac.DATA_LENGTH,
       ac.NULLABLE,
       t.column_name,
       t.comments
  from all_col_comments t
  left join all_tab_comments c on t.table_name = c.table_name
                              and t.owner = c.owner
  left join all_tab_columns ac on t.owner = ac.OWNER
                              and t.table_name = ac.TABLE_NAME
                              and t.column_name = ac.COLUMN_NAME
 where ac.COLUMN_ID is not null
   and ac.DATA_UPGRADED = 'YES'
   and t.owner = 'xxx_DW' -- 查看 DW 层
--and t.table_name like '%FACT%' -- 查看事实表
 order by t.owner, t.table_name, ac.COLUMN_ID;
```

|OWNER|COLUMN_ID|TABLE_NAME|COMMENTS|DATA_TYPE|DATA_LENGTH|NULLABLE|COLUMN_NAME|COMMENTS|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|xxx_DW|1|DW_FACT_TABLE|记录表|NUMBER|22|Y|ID|序列号|
|xxx_DW|2|DW_FACT_TABLE|记录表|VARCHAR2|22|Y|CODE|单号|
|xxx_DW|3|DW_FACT_TABLE|记录表|VARCHAR2|10|Y|TYPE|类型|

## 表关系（all_dependencies）

如果有足够权限的话，执行类似以下代码查看 DW 层中的某个表来源于哪些表。

```sql
select *
  from all_dependencies t
 where t.owner like '%DW%'  -- DW 层用户
   and t.name like '%FACT%'  --表名
   and t.referenced_owner like '%XXX%'; --相关用户
```

|OWNER|NAME|TYPE|REFERENCED_OWNER|REFERENCED_NAME|REFERENCED_TYPE|REFERENCED_LINK_NAME|DEPENDENCY_TYPE|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|DM|PKG_xxx_ANTI_FRAUD|PACKAGE BODY|SYS|STANDARD|PACKAGE||HARD|
|DW|ETL_DW_FACT_xxx|PROCEDURE|xxx|T_xxxT|TABLE||HARD|

或者反过来，执行类似以下代码查看 DW 层中的某个表被用在了哪些程序或存储过程中。

```sql
select *
   from all_dependencies t
  where t.referenced_owner like '%DW%' -- DW 层用户
    AND T.referenced_name like '%DW_FACT%'; --相关表名
```

|OWNER|NAME|TYPE|REFERENCED_OWNER|REFERENCED_NAME|REFERENCED_TYPE|REFERENCED_LINK_NAME|DEPENDENCY_TYPE|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|DM|ETL_DM_xxx_LIST|PROCEDURE|DW|DW_FACT_xxx|TABLE||HARD|
|DM|DM_PL_xxxx|PROCEDURE|DW|DW_FACT_xxx|TABLE||HARD|

## 权限（all_tab_privs）

执行类似以下代码查看表的一些权限分别被赋权给了哪些用户。

```sql
select *
  from all_tab_privs t
 where t.privilege in ('SELECT', 'UPDATE', 'DELETE', 'ALTER') --权限
   and t.table_name like '%DW_FACT%'; --表名
```

## 索引和约束

```sql
select * from all_constraints t where t.owner like '%DW%' ;
select * from all_indexes t where t.owner like '%DW%' ;
```

# IMPALA

用 [SHOW 命令](https://impala.apache.org/docs/build/html/topics/impala_show.html#show_databases)或[DESCRIBE 命令](https://impala.apache.org/docs/build/html/topics/impala_describe.html)查看单个对象的信息。不知道怎么批量查询，可能是因为对象信息都是单独存储的？

```sql
--查看所有数据库用户名
SHOW databases;
--查看某个用户下的表
SHOW TABLES in database_name;
--查看带有某关键词的表名
SHOW TABLES '*dim*|*fact*';
--查看某个用户下的某个表有哪些字段
DESCRIBE database_name.table_name;
--查看表的统计信息
show table stats database_name.table_name;
--查看列的统计信息
show column stats database_name.table_name;
```

剩下的就是花时间和精力用脑子去记了。
