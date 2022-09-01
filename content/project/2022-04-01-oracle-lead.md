---
title: oracle 笔记-排序和递归查询
author: yuanfan
date: 2022-04-01T22:12:08+0800
slug: oracle-lead
categories:
  - R
tags:
  - R
draft: no
---

<font face="微软雅黑">

<!--more-->

本以为同一种语言（SQL）写多了，脑子要生锈。现在想想，是我懒得动脑筋罢了。

# 案例一

同一个客户多次购买商品的行为称之为复购。实际业务中需求不一样，“复购”的定义也会不一样。但是俺只是记个笔记，所以把问题简化如下。

>现已知客户每次购买商品的时间，求客户最后一次复购与最后一次复购之前的最近一次购买之间的间隔时长。如下表所示，相当于是当客户ID（customer_id）为1234时，求最后一次复购时间`2021-05-16 19:58:02`与最后一次复购之前的最近一次购买时间`2020-04-30 15:30:30`之间的间隔时长。

|list_id|customer_id|insert_time|
|:--:|:--:|:--:|
|1|1234|2021-05-16 19:58:02|
|2|1234|2020-04-30 15:30:30|
|3|1234|2020-01-01 01:01:01|
|4|5678|2021-07-08 09:00:00|
|5|4567|2021-01-01 14:56:56|
|6|4567|2021-01-01 09:01:02|

我原先不知道 ORACLE 里面有`lead`这个函数，所以把这一步拆成了几个临时的中间表，直到今日请教同事小花别的问题顺带问了这个，才知道可以写得如此简便。

```{sql}
select t.*,
--按customer_id分组，按insert_time倒序排序并生成序号
       row_number() over(
         partition by t.customer_id 
         order by t.insert_time desc) rank,
--lead(t.insert_time, 1)表示取出按insert_time往后偏移一位的数据   
       lead(t.insert_time, 1) over(
         partition by t.customer_id 
         order by t.insert_time desc) as goal_time
  from tmp_table t;
```

执行上面的脚本后，会得到下表，之后按照`rank = 1`且`goal_time is not null`筛选就可以得到最后一次复购的记录，两个时间相减即可得到所求间隔时长。

|list_id|customer_id|insert_time|rank|gaol_time|
|:--:|:--:|:--:|:--:|:--:|
|1|1234|2021-05-16 19:58:02|1|2020-04-30 15:30:30|
|2|1234|2020-04-30 15:30:30|2|2020-01-01 01:01:01|
|3|1234|2020-01-01 01:01:01|3||
|4|5678|2021-07-08 09:00:00|1||
|5|4567|2021-01-01 14:56:56|1|2021-01-01 09:01:02|
|6|4567|2021-01-01 09:01:02|2||

# 案例二

现有 M、N 两组数据，这两组数据中都有两个字段，一个是代码（code），一个是名称（name），区别在于 M 组数据中的代码字段都是正常的序号，而 N 组数据中的代码字段都是“9999999”。问题如下：

>现在需要在 N 组数据的基础上，根据 N 组中的名称去匹配 M 组中的名称，若能匹配上 M 组中唯一一条数据，则获取对应的名称及代码，若是能匹配上 M 组中多条数据，同样获取对应的名称及代码且分多行展示。其中，“匹配”的定义暂定为N组名称与M组名称有包含关系。

需要匹配数据的 N 组数据大致如下：

|code_N|name_N|
|:--:|:--:|
|9999999|桂林市中西医结合医院|
|9999999|西电集团医院|
|9999999|宾县人民医院|
|9999999|福州总医院|

等待匹配数据的 M 组数据大致如下：

|code_M|name_M|
|:--:|:--:|
|0000001|桂林市第五人民医院(桂林市中西医结合医院)|
|0000002|中国西电集团医院|
|0000003|来宾县人民医院|
|0000004|宜宾县人民医院|
|0000005|南京军区福州总医院|
|0000006|南京军区福州总医院分院|
|0000007|南京军区福州总医院第九五分院（南京军区莆田九五医院）|

参照“匹配”的定义，匹配后的效果应如下：

|code_N|name_N|name_M|code_M|
|:--:|:--:|:--:|:--:|
|9999999|桂林市中西医结合医院|桂林市第五人民医院(桂林市中西医结合医院)|0000001|
|9999999|西电集团医院|中国西电集团医院|0000002|
|9999999|宾县人民医院|来宾县人民医院|0000003|
|9999999|宾县人民医院|宜宾县人民医院|0000004|
|9999999|福州总医院|南京军区福州总医院|0000005|
|9999999|福州总医院|南京军区福州总医院分院|0000006|
|9999999|福州总医院|南京军区福州总医院第九五分院（南京军区莆田九五医院）|0000007|

同事小花给的脚本，仍然是基于 ORACLE 的 sql ：

```{sql}
select distinct tt.code_N,
                tt.name_N,
--用 regexp_substr 匹配正则表达式,最后一个参数‘i’表示不区分大小写        
                regexp_substr(tt.hospital_name, '[^,]+', 1, level, 'i') as name_M
  from (select n.code_N,
               n.name_N,
--用 instr 函数取 name_N 在 name_M 中的位置，判断前者是否包含在后者中
--用 wm_concat 函数将匹配到的 name_M 拼接到一起
               (select to_char(wm_concat(distinct m.name_M))
                  from m_hospital m
                 where instr(m.name_M, n.name_N) > 0) hospital_name
          from n_hospital n) tt
-- connect by prior 是 oracle 中递归查询的写法         
connect by tt.code_n = prior tt.code_n
       and level <= length(tt.hospital_name) -
           length(regexp_replace(tt.hospital_name, ',', '')) + 1;
```

上面的 sql 语句并没有一次性把能匹配上的代码和名称都取出来，只是简化版本。实际业务中存在一个name_N对应几千个name_M的特殊情况，不加限制的话会报一个“ORA-22183：操作数值超出系统的限制”的错。

## connect by prior

递归中的“递”字是指传递。比如“曾祖父-->祖父-->父亲-->本人-->儿子-->孙子-->曾孙”表示了血缘关系的传递，转换成表格，用 NAME 表示当代，PARENT 表示当代的父亲。

|RANK|NAME|PARENT|
|:--:|:--:|:--:|
|1|曾祖父|-1|
|2|祖父|曾祖父|
|3|父亲|祖父|
|4|本人|父亲|
|5|儿子|本人|
|6|孙子|儿子|
|7|曾孙|孙子|

+ 假如从“本人”这一代开始往上递归查询

`start with`表示查询的起点。

`connect by prior t.parent = t.name`表示把查询到的当代（NAME）传递给当代的父亲（PARENT），相当于不断递归查找上一代，`prior`在`=`的哪一边，就是把查询到的内容传递给哪一边。

`level`是 ORACLE执行递归查询后默认生成的序号，查询起点的序号默认记为1，每递归一次序号增加1。倘若下面的代码最后一行加上`and level < 3`，执行出来的结果就会只有两行。

```{sql}
select t.name, t.parent, level
  from tmp_table3 t
 start with t.name = '本人'
connect by prior t.parent = t.name;
```

执行上面代码后，可以得到：

|NAME|PARENT|LEVEL|
|:--:|:--:|:--:|
|本人|父亲|1|
|父亲|祖父|2|
|祖父|曾祖父|3|
|曾祖父|-1|4|

+ 假如从“本人”这一代开始往下递归查询

`connect by t.parent = prior t.name`表示把查询到的当代的父亲（PARENT）传递给当代（NAME），相当于不断递归查找下一代。

```{sql}
select t.name, t.parent, level
  from tmp_table3 t
 start with t.name = '本人'
connect by t.parent = prior t.name;
```

执行上面代码后，可以得到：

|NAME|PARENT|LEVEL|
|:--:|:--:|:--:|
|本人|父亲|1|
|儿子|本人|2|
|孙子|儿子|3|
|曾孙|孙子|4|

+ 自己与自己递归

当案例二第一层查询匹配出来的结果是：

|code_N|name_N|hospital_name|
|:--:|:--:|:--:|
|9999999|宾县人民医院|宜宾县人民医院,来宾县人民医院|

然后自己与自己递归，会得到递归生成的序号：

```{sql}
select distinct  code_N,
       tt.name_N,
       tt.hospital_name,
       level
  from table tt
connect by tt.code_N = prior tt.code_N
--计算 hospital_name 中','的数量
       and level <= length(tt.hospital_name) -
           length(regexp_replace(tt.hospital_name, ',', '')) + 1;
```

递归生成序号的结果是：

|code_N|name_N|hospital_name|level|
|:--:|:--:|:--:|:--:|
|9999999|宾县人民医院|宜宾县人民医院,来宾县人民医院|2|
|9999999|宾县人民医院|宜宾县人民医院,来宾县人民医院|1|

根据得到的序号，取出 hospital_name 中按逗号分隔的逗号前后的内容：

```{sql}
select distinct  code_N,
       tt.name_N,
       tt.hospital_name,
       level,
--取出逗号前后的内容
       regexp_substr(tt.hospital_name, '[^,]+', 1, level, 'i') as name_M
  from table tt
connect by tt.code_N = prior tt.code_N
--计算 hospital_name 中','的数量，限制递归次数
       and level <= length(tt.hospital_name) -
           length(regexp_replace(tt.hospital_name, ',', '')) + 1;
```

得到的结果是：

|code_N|name_N|hospital_name|level|name_M|
|:--:|:--:|:--:|:--:|:--:|
|9999999|宾县人民医院|宜宾县人民医院,来宾县人民医院|2|来宾县人民医院|
|9999999|宾县人民医院|宜宾县人民医院,来宾县人民医院|1|宜宾县人民医院|

# 思考题

这是一道没有必要思考的思考题，因为小花已经找到了例子可以直接从反面锤死我的想法，而且我也还是没有想出答案。题目如下：

>表 table1 中有 case_id 和 item_id 两个字段，一个 case_id 可能对应一个或多个 item_id。表 table2 中有 item_id 和 change_id 两个字段，若是按照业务逻辑，两者可能存在一对多、一对一、多对一、多对多等四种关系。表 table3 中有 change_id。如果想要把表 table1 和 table3 关联上，中间必须关联上 table2。我猜想若是根本就不存在一个 case_id 对应多个 item_id 且每个 item_id 都有一个一对一的 change_id 的情况，那么是不是可以直接略过 table2 而是直接让 table1 和 table3 关联呢？

示例数据如下：

|table1.case_id|table2.item_id|table3.change_id|rank1|rank2|rank3|note|
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|case1|item1|change1|1|1|1|一对一|
|case1|item2|change2|2|2|2|一对一|
|case1|item3|change3|3|3|3|一对多|
|case1|item3|change4|3|4|4|一对多|
|case1|item4|change5|4|5|5|多对一|
|case1|item5|change5|5|5|6|多对一|
|case1|item6|change5|6|5|7|多对一|

我的解题思路是将三个表关联起来以后，去找是否存在这样的情况。一个 case_id 会对应多个 item_id，只要证明其中的 item_id 和 change_id 的关系为“仅一对一”、“既有一对一也有一对多”、“既有一对一也有多对一”、“既有一对一也有一对多和多对一”的情况都没有数据，就算是完成了。第一步，先按 case_id 分组、按 item_id 排序得到 rank1，再按 case_id 分组、按 change_id 排序得到 rank2，最后按 case_id/item_id 分组、按 change_id 排序得到 rank3。第二步，对 rank1、rank2、rank3 取最大值得到 m_rank1、m_rank2、m_rank3。第三步，通过比较到 m_rank1、m_rank2、m_rank3 三者之间的关系来判断是不是任何包含“一对一”的情况都不存在。

```{sql}
select *
  from (select max(rank1) m_rank1, max(rank2) m_rank2, max(rank3) m_rank3
          from (select t1.case_id,
                       t2.item_id,
                       t3.change_id,
                       --生成连续的序号，被排序的值一样时得到一样的序号
                       dense_rank() over(partition by t1.case_id order by t2.item_id asc) rank1,
                       dense_rank() over(partition by t1.case_id order by t3.change_id asc) rank2,
                       --生成连续的序号，被排序的值一样时得到不一样的序号
                       row_number() over(partition by t1.case_id, t2.item_id order by t3.change_id asc) rank3
                  from table1 t1
                  join table2 t2 on t1.item_id = t2.item_id
                  join table3 t3 on t2.change_id = t3.change_id )
         where rank1 > 1)
--存在一个案件仅一对一
  where m_rank1 = m_rank2 and m_rank2 = m_rank3  
--存在一个案件既有一对一，也有多对一
  or  (m_rank1 > m_rank2 and m_rank1=m_rank3)
--存在一个案件既有一对一，也有一对多
  or (m_rank1 < m_rank2 and m_rank2=m_rank3)
--存在一个案件既有一对一，也有多对一,也有一对多
--???
```

以上是一个繁琐且失败的答案。

最近工作上有一个任务总让我感到很迷（迷茫、迷失、迷路）。之前开发了一个模型，每天凌晨跑前一天的数据，现在要改成实时调用的。所谓“实时”可以接受的时限是三秒，一秒内计算出特征，一秒内根据特征调用模型得到结果，一秒内做一些特殊处理并将结果返回。周一的时候，在测试环境跑特征这步要十分钟，对我来说往存储过程里面填点 sql 计算特征还行，让我提升执行效率真是各种抓瞎，迷了一周才鼓捣完。要是换个对数据库知识很熟悉的人，也许一天或者几小时就处理完了，可是我实在是缺乏那些常识啊喂。

同事们讨论问题的时候讲什么物化视图、序列、消息之类的概念我都不懂，其他同事之前为另一个模型写的实时计算特征的例子我也看不懂。我的常识里只有若是查询一个数据量很大的表建了索引会比没建索引跑得快，所以我这个死脑筋在踩坑的时候才会想到要是不用关联有几亿条数据的 table2 就好了。

但是我发现自己不知何时已经修正了脑子里一个很不好的思维习惯，以前每每遇到困难挫折的时候便会怪过去的自己怎么不更加努力一点、不多长点心等等，这次我没怪自己，就只是一直很迷很迷地干活而已。

***[梯田+爸我回来了（Live）](https://www.bilibili.com/video/BV14Q4y1i7ZA?p=1&share_medium=iphone&share_plat=ios&share_session_id=2455D6D0-1B33-4829-BD37-79C91B382FDB&share_source=WEIXIN&share_tag=s_i&timestamp=1648826489&unique_k=kTuKpHK)***