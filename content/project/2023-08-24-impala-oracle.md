---
title: IMPALA 与 ORACLE 在一些函数上的异同
author: yuanfan
date: 2023-08-24T20:54:49+0800
slug: impala-oracle
categories:
  - R
tags:
  - R
draft: no
---



<!--more-->

由于日常工作干活时总会遇见一些令人惊叹的坑，大概就是“这居然也行”、“这居然都不行”之类的。在 IMPALA 和 ORACLE 中，有时候实现同一种功能的函数名不一致，函数名一致的所支持的范围又不一致，于是特地整理出来一些接触过的，免得有些坑反反复复踩。为便于复现，先按如下数据分别在 IMPALA 和 ORACLE 中建立一个临时表[^1]。

[^1]:此处又想吐槽，俺平时写各种文档都是在 Rstudio 里面写，如果是写的 R 代码的话，按住 ctrl+Shift+A 键可以格式化代码。然鹅，Rstudio 支持 sql 语法高亮，却不支持 sql 代码格式化。

|id|type|name|value|
|:--:|:--:|:----:|:--:|
|1|A|太阳|100|
|2|A|月亮|80|
|3|A|太阳|0|
|4|B|NULL|10|

分别查看 IMPALA 和 ORACLE 的版本信息，**左边是 IMAPALA，右边是 ORACLE。**

<div style="display: flex;">

<div style="width: 49%">

```sql
select version();
```

impalad version 3.2.0-cdh6.3.2
</div>

<div style="width: 2%">
</div>

<div style="width: 49%">

```sql
select * from v$version;
```

Oracle Database 11g 
</div>

</div></div>

# 建表

有一点需注意，由于 IMPALA 和 ORACLE 各自的特性，两者对于 DDL（Data Definition Language）、DML（Data Manipulation Language） 语句的定义范围不完全一致[^2]。键者使用 ORACLE 数据库时，其实是用 PL/SQL Developer 连接数据库，可以在 SQL 窗口中执行删表（drop）、建表（create）、插入数据（insert）等操作。而在使用 IMPALA 这个查询引擎时，其实是使用 HUE 界面的前台查询窗口，也可以使用服务器的 IMPALA SHELL 后台窗口。

[^2]:[IMPALA DDL](https://impala.apache.org/docs/build/html/topics/impala_ddl.html)。[ORACLE DDL](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/Types-of-SQL-Statements.html#GUID-FD9A8CB4-6B9A-44E5-B114-EFB8DA76FC88)。

<div style="display: flex;">

<div style="width: 49%">

```sql
--drop table default.impala_table;
create table default.impala_table (id int, type string, name string, value int);
insert into default.impala_table
values
  (1, 'A', '太阳', 100),
  (2, 'A', '月亮', 80),
  (3, 'A', '太阳', 0),
  (4, 'B', null, 10);





select * from default.impala_table;
```

|id|type|name|value|
|:--:|:--:|:----:|:--:|
|1|A|太阳|100|
|2|A|月亮|80|
|3|A|太阳|0|
|4|B|NULL|10|

</div>

<div style="width: 2%">
</div>

<div style="width: 49%">

```sql
--drop table oracle_table;
create table oracle_table (id int, type varchar2(8), name varchar2(8), value int);
insert all 
  into oracle_table (id, type, name, value)
  values (1, 'A', '太阳', 100) 
  into oracle_table (id, type, name, value)
  values (2, 'A', '月亮', 80) 
  into oracle_table (id, type, name, value)
  values (3, 'A', '太阳', 0) 
  into oracle_table (id, type, name, value)
  values (4, 'B', null, 10)
select * from dual;

select * from oracle_table;
```

|ID|TYPE|NAME|VALUE|
|:--:|:--:|:----:|:--:|
|1|A|太阳|100|
|2|A|月亮|80|
|3|A|太阳|0|
|4|B||10|

</div>

</div></div>

键者最近踩了一个内存溢出的坑，在 HUE 查询窗口中直接使用 DDL 语句删表、建表，从前台的结果看很快，往往也就耗时几秒、几分钟，然而从后台的日志看变成了几小时。原因是后台对每一次删表、建表记录的持续时长是从执行语句开始一直到整个查询窗口关闭为止。HUE 的特点就是，在查询窗口中执行语句产生的后台查询处理程序，不会在执行得到结果以后就立刻关闭，这是为了方便用户后续仍然需要检索结果。但是这样的话，不明真相的人去看后台日志可能会吓一跳。总而言之，得到的结论是最好只在前台 HUE 中写普通的查询语句，而写 DDL 语句改为登录后台进行操作。整个建表的步骤就改成了如下这样。

1. 登录 Linux 服务器，输入`impala-shell`命令打开窗口
2. 依经验设置内存限制，例如`set MEM_LIMIT = 10g;`，也可以先问问管理集群的人能用多少资源。
3. 建表。如果在 HUE 执行`create table 表名`建表，使用`show create table 表名`可以看到其实是默认`STORED AS TEXTFILE`，即行式存储格式。而 IMPALA 还有`STORED AS PARQUET`，即列式存储格式，更适合于针对列的大规模聚合查询。
4. 往表中插入数据。

**IMPALA 对数据类型限制十分严格，= 号两边的数据类型不匹配会报错。**而在 ORACLE 中不会。


```sql
--执行后报错
--AnalysisException: operands of type INT and STRING are not comparable: t.id = '1'
SELECT * from default.impala_table t WHERE t.id = '1';
 
--执行后得到结果
select * from oracle_table t where t.id = '1';
```

# 1.常用日期函数

[Impala Date and Time Functions](https://impala.apache.org/docs/build/html/topics/impala_datetime_functions.html)

<div style="display: flex;">

<div style="width: 49%">

```sql
# int 转换为 string
select cast(123 as string);

# 转换日期格式，或者提取年月日、时分秒
select from_unixtime(unix_timestamp('2022-01-01'), 'yyyyMM') ;

# 日期相减，天数
SELECT DATEDIFF(TO_DATE('2023-03-09'), TO_DATE('2023-02-03'));
# 日期间隔，月份数
select months_between(to_date('2023-03-09'), to_date('2023-02-03'));

# 增加月份
select add_months(to_date('2022-01-01'), 3);

# 分别取月度、季度、年度的第一天
SELECT trunc(NOW(), 'MM');
SELECT trunc(NOW(), 'Q');
SELECT trunc(NOW(), 'yyyy');
```
</div>

<div style="width: 2%">
</div>

<div style="width: 49%">

```sql
# int 转换为 varchar
select to_char(123) from dual;

# 转换日期格式
select to_char(date '2022-01-01', 'yyyyMM') from dual;

# 日期相减，天数
select date '2023-03-09' - date '2023-02-03' from dual;
# 日期间隔，月份数
select months_between(date '2023-03-09', date '2023-02-03') from dual;

# 增加月份
select add_months(date '2022-01-01', 3) from dual;

# 分别取月度、季度、年度的第一天
select trunc(SYSDATE, 'mm') from dual;
select trunc(SYSDATE, 'Q') from dual;
select trunc(SYSDATE, 'yyyy') from dual;
```
</div>

</div></div>

# 2.拼接（concat）

在 IMPALA 和 ORACLE 中都有字符串拼接函数，各有各的限制。

+ 按列拼接，将不同列的字段拼接到一起。
  - IMPALA 中由`concat()`和`concat_ws()`函数实现，两者均限定只能拼接字符型数据，其他类型进行转换，并且缺失值也要转换（比如`ifnull(t.name, '')`），可拼接多个字段，其中前者默认拼接的字符串之间没有分隔符号，而后者可以指定特殊字符作为分隔符号。
  - ORACLE 中由`concat()`函数实现，不限定可拼接的数据类型，但是限定最多只能拼接两个字段，默认拼接的字符串之间没有分隔符号。

<div style="display: flex;">

<div style="width: 49%">

```sql
# 拼接三个字段，其中的 int 需要转换为 string
select concat(t.type, t.name, cast(t.value as string))
  from default.impala_table t;
  
# 指定拼接字符串由-连接  
select concat_ws('-', t.type, t.name, cast(t.value as string)) as new_col
  from default.impala_table t;
```

|new_col|
|:--------:|
|A-太阳-100|
|A-月亮-80|
|A-太阳-0|
|NULL|

</div>

<div style="width: 2%">
</div>

<div style="width: 49%">

```sql
# 用多个 concat 函数嵌套来实现拼接三个字段
select concat(concat(t.type, t.name), t.value) as new_col
  from oracle_table t;
  
# 用多个 concat 函数嵌套来实现由-符号连接  
select concat(concat(concat(concat(t.type, '-'), t.name), '-'), t.value) as new_col
  from oracle_table t;
```

|NEW_COL|
|:------:|
|A-太阳-100|
|A-月亮-80|
|A-太阳-0|
|B--10|

</div>

</div></div>

+ 按列拼接字段后，再按行去重。普通的去重方式就是在 SELECT 子句中加上 DISTINCT，这在 IMPALA 和 ORACLE 中都行得通。然鹅，键者无意中发现 IMPALA 里面 SELECT 子句中生成的新字段，可以放到 GROUP BY 子句中，从而起到去重的效果。一般情况下 GROUP BY 子句的执行顺序都是在 SELECT 前面的，而 IMPALA 中这点不再是一条铁律。

<div style="display: flex;">

<div style="width: 49%">

```sql
select concat_ws(t.type, t.name) as new_col
  from default.impala_table t
 group by new_col;
```

|new_col|
|:------:|
|NULL|
|A太阳|
|A月亮|

</div>

<div style="width: 2%">
</div>

<div style="width: 49%">

```sql
select distinct concat(t.type, t.name) as new_col 
  from oracle_table t;
  
```

|new_col|
|:------:|
|A太阳|
|A月亮|
|B|

</div>

</div></div>

+ 分组后，按行拼接。在 IMPALA 中用 `group_concat()`函数实现，在 ORACLE 中用 `wm_concat()`函数实现。

<div style="display: flex;">

<div style="width: 49%">

```sql
select t.type, group_concat(distinct t.name) as new_col
  from default.impala_table t
 group by t.type;
```

|type|new_col|
|:----:|:----:|
|B|NULL|
|A|月亮,太阳|

</div>

<div style="width: 2%">
</div>

<div style="width: 49%">

```sql
select t.type, wm_concat(distinct t.name) as new_col
  from oracle_table t
 group by t.type;
```

|TYPE|NEW_COL|
|:----:|:----:|
|A|太阳,月亮|
|B|NULL|

</div>

</div></div>

# 3.OVER 开窗函数 

在 IMPALA 和 ORACLE 中都有开窗函数，基本语法是`function() over(partition by 分组字段 order by 排序字段)`，这样放在 SELECT 子句后面会生成一个新字段。**下面用到的函数分别在 IMPALA 和 ORACLE 中执行时，生成的新字段内容是一致的。**

## 分组排序

分组排序在日常工作中用得较多，关于排序（order by）都是默认升序（asc），缺失值序号在前（nulls first）。

+ `row_number()`，每一行得到一个序号，且序号数值唯一。
+ `dense_rank()`，若多行数据内容相同，得到相同的序号，不跳过任何序号数值。
+ `rank()`，与`dense_rank()`相比，会跳过序号数值。


```sql
select t.*,
       row_number() over(partition by t.type order by t.name asc) rank1,
       dense_rank() over(partition by t.type order by t.name asc) rank2,
       rank() over(partition by t.type order by t.name asc) rank3,
       -- 按条件分组，改为倒序排序
       row_number() over(partition by case when t.value >= 80 then '80' else null end order by t.name desc) rank4,
       -- 同上，且改为缺失值序号在后
       row_number() over(partition by case when t.value >= 80 then '80' else null end order by t.name desc nulls last) rank5
  from default.impala_table t;
```

|id|type|name|value|rank1|rank2|rank3|rank4|rank5|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|1|A|太阳|100|1|1|1|2|2|
|3|A|太阳|0|2|1|1|2|1|
|2|A|月亮|80|3|2|3|1|1|
|4|B|NULL|10|1|1|1|1|2|

## 分组聚合


```sql
select t.*,
       count(t.value) over(partition by t.type) cnt,
       max(t.value) over(partition by t.type) max,
       min(t.value) over(partition by t.type) min,
       avg(t.value) over(partition by t.type) avg,
       sum(t.value) over(partition by t.type) sum
  from default.impala_table t;
```

|id|type|name|value|cnt|max|min|avg|sum|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|1|A|太阳|100|3|100|0|60|180|
|2|A|月亮|80|3|100|0|60|180|
|3|A|太阳|0|3|100|0|60|180|
|4|B|NULL|10|1|10|10|10|10|

## 位移

+ `lag(column, offset, default)`，往前移动取值，需指定对应取值的字段名、位移量、默认值。
+ `lead(column, offset, default)`，往后移动取值，参数同上。
+ `first_value()`，取第一个值。
+ `last_value()`，取最后一个值。


```sql
select t.*,
       lag(t.id, 1, 0) over(order by t.id) lag_id1,
       lead(t.id, 1, 0) over(order by t.id) lead_id2,
       first_value(t.id) over(partition by t.type) first_value,
       last_value(t.id) over(partition by t.type) last_value
  from oracle_table t;
```

|id|type|name|value|lag_id1|lead_id2|first_value|last_value|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|1|A|太阳|100|0|2|1|3|
|2|A|月亮|80|1|3|1|3|
|3|A|太阳|0|2|4|1|3|
|4|B|NULL|10|3|0|4|4|

## 滑动窗口

在 over 中指定 rows between 参数可从不同行数的滑动窗口中取值。

+ `n preceding`，n 为数字，表示从当前行的前 n 行开始取值。
+ `unbounded preceding`，表示从第一行开始取值。
+ `current row`，表示取当前行的值。
+ `n following`，n 为数字，表示取值截止到当前行的后 n 行。
+ `unbounded following`，表示取值截止到最后一行。


```sql
select t.*,
       avg(t.value) over(order by t.id rows between 1 preceding AND 1 following) as avg1,
       avg(t.value) over(order by t.id rows between unbounded preceding and current row) avg2,
       avg(t.value) over(order by t.id rows between current row and unbounded following) avg3
  from oracle_table t;
```

|id|type|name|value|avg1|avg2|avg3|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|1|A|太阳|100|90|100|47.5|
|2|A|月亮|80|60|90|30|
|3|A|太阳|0|30|60|5|
|4|B|NULL|10|5|47.5|10|

# 4.其他

键者梳理两者异同主要是翻文档，再就是问问新必应。

+ IMPALE <https://impala.apache.org/docs/build/html/topics/impala_functions.html>。
+ ORACLE <https://www.oracletutorial.com/oracle-basics/>。

## COUNT VS. NDV

键者按照一张清单表计算一些汇总数据，需要对某一个字段按照不同条件筛选后计算出去重个数，于是在 SELECT 语句后面会有几十个`count(distinct case when )`之类的新增字段，这段 SQL 在 HUE 界面上执行时会报下面这样的错：

>Could not connect to hxx.hadoop:21050(code THRIFTTRANSPORT):TTransportException('Could not connect to hxx.hadoop:21050',)

放到 impala shell 中执行也会报错:

>Socket error 104: Connection reset by peer

这两个错误都是与内存溢出相关的错误，用 EXPLAIN 命令查看也没看出个所以然。但是 EXPLAIN 其他能正常执行的SQL语句，能看到每个步骤有 cardinality 等于一个数字，而有错的这个每个步骤都显示`cardinality=unavailable`。将 `count(distinct)`改成 `ndv()`后，就没报错了。然鹅，令俺始终迷惑不解的是，以前用一张千万级的清单表跑数也没出现过这种情况，这次才只是百万级的数据。同样的数据和逻辑放到 ORACLE 里面能够执行出结果，但是耗费时间会多出许多倍。如果是挪到 R 中用 data.table 来实现，比如`data[, by = .(), .(num1 = uniqueN(id[条件]))]`也会很慢。

## 子查询

IMPALA 中子查询只能写在 FROM / WHERE 子句后面，不能写在 SELECT 子句后面。

## 求方差、标准差

在 IMPALA 和 ORACLE 中相同的是，计算总体或样本的方差、标准差函数名一致。

+ `var_pop()`，总体方差（population variance）
+ `var_samp()`，样本方差（sample variance）
+ `stddev_pop()`，总体标准差（population standard deviation ）
+ `stddev()/stddev_samp()`，样本标准差（sample standard deviation）

相异的是，IMPALA 中计算中位数的函数是`appx_median()`，所得结果为输入数值中接近中间点较大的值，ORACLE 中计算中位数的函数是 `median()`，所得结果为接近中间点的两个数值的平均值。


```sql
select variance(t.value) var,
       var_pop(t.value) var_pop,
       var_samp(t.value) var_samp,
       stddev(t.value) stddev,
       stddev_pop(t.value) stddev_pop,
       stddev_samp(t.value) stddev_samp,
       appx_median(t.value) median
  from default.impala_table t;
```

|-|var_pop|var_samp|stddev_pop|stddev_samp|median|
|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
|**IMPALA**|1868.75|2491.6666666666665|43.229041164476456|49.91659710623979|80|
|**ORACLE**|1868.75|2491.66666666667|43.2290411644765|49.9165971062398|45|

## 求分位数

在 ORACLE 中计算分位数，如下根据0、10、80、100等4个数字计算中位数。

+ `percentile_cont()`函数计算的结果为45，显然是在10和80之间取了平均值。
+ `percentile_disc()`函数计算的结果为10，是在10和80之间取较小的10。


```sql
select 
percentile_cont(0.5) within group(order by t.value asc) as perc_cont, 
percentile_disc(0.5) within group(order by t.value asc) as perc_disc
  from oracle_table t;
```

在 ORACLE 中，`percentile_cont()`和`percentile_disc()`函数也可以结合 OVER 开窗函数一起使用，除此以外还有。

+ `ntile()`，按排序结果划分出指定数量的类，并赋予每一行类别序号。
+ `cume_dist()`，计算小于等于当前行数值的行数占组内总行数的百分比 
+ `percent_rank()`，同上相比，百分比的分子只看小于当前行数值的行数，分母为组内总行数但不包含当前行。


```sql
select t.*,
percentile_cont(0.5) within group(order by t.value asc) over(partition by t.type) as perc_cont, 
percentile_disc(0.5) within group(order by t.value asc) over(partition by t.type) as perc_disc,
ntile(2) over(order by t.value asc) as ntile,
cume_dist() over(order by t.value asc) as cd,
percent_rank() over(order by t.value asc) as prank
  from oracle_table t;
```

|ID|TYPE|NAME|VALUE|PERC_CONT|PERC_DISC|NTILE|CD|PRANK|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|3|A|太阳|0|80|80|1|0.25|0|
|4|B||10|10|10|1|0.5|0.333333333333333|
|2|A|月亮|80|80|80|2|0.75|0.666666666666667|
|1|A|太阳|100|80|80|2|1|1|

IMPALA 中似乎没有`percentile_cont()`和`percentile_disc()`这两个直接计算分位数的函数，可以如下迂回实现。


```sql
with t1 as(  
select t.*,
       cume_dist() over(order by t.value asc) as cd,
       percent_rank() over(order by t.value asc) as prank
  from default.impala_table t)
select min(case
             when cd >= 0.5 then
              value
           end) as cd_50,
       min(case
             when prank >= 0.5 then
              value
           end) as prank_50
  from t1;
```

|cd_50|prank_50|
|:----:|:----:|
|10|80|

## 行列转换

ORACLE 支持用[pivot](https://www.oracletutorial.com/oracle-basics/oracle-pivot/)和[unpivot](https://www.oracletutorial.com/oracle-basics/oracle-unpivot/)函数做行列转换，IMPALA 中似乎暂时没有特定函数支持行列转换，需要迂回实现。

## 递归查询

ORACLE 支持递归查询，IMPALA 似乎暂时也没有特定函数支持递归，可能需要迂回实现。

## 检索元数据

在 IMPALA 中通过 [SHOW 命令](https://impala.apache.org/docs/build/html/topics/impala_show.html)来查看各种元数据，或称 impala 对象。


```sql
# 查看 default.impala_table 的建表语句
show create table default.impala_table;

# 查看当前数据库中的所有表名
show tables;
# 查看名称中含 impala 的表
show tables like '*impala*';

show databases;
```

在 ORACLE 中需要从各个特殊的表里查看元数据，或称 oracle 对象。


```sql
# 查看 ORACLE_TABLE 的建表语句，注意需要大写
select DBMS_METADATA.GET_DDL('TABLE','ORACLE_TABLE') from USER_TABLES;

# 查看当前用户下每张表的表名、状态、行数等信息
select * from user_tables;
# 查看数据库中所有用户下的表
select * from all_tables;
# 查看每张表的字段信息
select * from t_query_column t where t.table_name = upper('xxx');

# 根据所有列的列名或注释进行检索
select *
  from all_col_comments t
 where t.owner = '用户名'
   and t.comments like '%关键词%';
   
# 查看 oracle 对象的依赖关系
# 比如查看 A 用户下名称中含有 FRAUD 的存储过程，其中引用 B 用户下的所有表
select *
  from all_dependencies t
 where t.owner like '%A%'
   AND t.name like '%FRAUD%'
   and t.referenced_owner like '%B%';
```

## group by rollup

若在 ORACLE 中 group by 子句后面加上 rollup ，可在分组聚合时加上一行按所有数据聚合的结果。而在 IMPALA 中似乎从[7.2.2版本开始才引入rollup](https://docs.cloudera.com/runtime/7.2.2/impala-sql-reference/topics/impala-group-by.html)。


```sql
select t.type, sum(t.value) as sum
  from oracle_table t
 group by rollup(t.type);
```

|TYPE|SUM|
|:----:|:----:|
|A|180|
|B|10|
||190|

## 全量更新

1. 通过 impala 建表，可以分别建在 kudu 或者 hive 上面。

  - 建在 kudu 的表必须有主键（primary key），似乎可以约束数据的唯一性。
  - 仅限于impala2.8或更高版本中，可以在 kudu 表中使用update（更新）、delete（删除）任意数量的行。
  - 但是建在 hive 上面的表没有主键，不支持使用 update（更新）、delete（删除），更新表只能 drop（删除整张表，包括表结构和所有数据）、truncate（仅删除整张表的数据，保留表结构）、insert（插入数据）。也就是说只能全量更新，或者不断插入数据，可能会重复插入数据，不能增量更新。

2. impala 中插入数据后不需要 commit（提交），似乎在数据开发时需要严格控制脚本的调度顺序，避免出现并发的问题。而 ORACLE 中如果往表中插入数据后没有执行 commit，会锁表，但这样也算是控制了并发问题的出现。

3. impala 不支持修改表的元数据。如果只是想改变某个字段的精度，也需要创建一个新表，然后将原表的数据导入新表中，再将原表删掉重建，如此折腾一番。
