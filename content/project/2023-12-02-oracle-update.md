---
title: 在 ORACLE 中 UPDATE（更新）一张表
author: yuanfan
date: 2023-12-02T10:59:28+0800
slug: oracle-update
categories:
  - Living
tags:
  - R
draft: no
---

<!--more-->

事情是酱紫的，本菜鸟最近需要在一个性能不咋好的 ORACLE 数据库中更新一张表，此表原有6500万条数据、94个字段，此次更新需要再增添2个新字段。日常工作中自然谁都希望能用上性能好、效率高的工具，但遇到别的情况抱怨也无济于事，只好耐心面对。完成此事有两个必须顾虑的限制条件：

+ 时间限制，原表每天凌晨自动写入前一天的业务数据，因此更新此表的持续时间不能超过晚上12点。
+ 空间限制，不能直接一次性更新此表，会把回滚段占满，也要注意占用临时表空间的各种情况[^1]。

[^1]:空间限制是我在瞎碰乱试的过程中各种翻车后才深刻感受到的。本来这件事是不需要我来做的，原本干的活有个中间环节要追溯历史数据，这件事应该是让其他人帮忙弄，然鹅我深知这一等可能会被拖很久很久所以才自己上手。又由于我之前没做过类似的事，于是从具体干活思路到写更新数据的代码，每一步都需要先发到群里让其他人先看看，冇问题才继续。

在做一切尝试之前，先试着了解一下原表及索引占用的空间大小。假设原表名称是`T_FACT_NEWBUSINESS`。

```sql
--查看表占用的内存
select sum(t.bytes) / 1024 / 1024 / 1024
  from user_segments t
 where t.segment_type = 'TABLE'
   and t.segment_name = 'T_FACT_NEWBUSINESS';
   
--查看此表的索引名称
select t.uniqueness, t.index_name, t.*
  from all_indexes t
 wheret.table_name = 'T_FACT_NEWBUSINESS';
--查看此表索引占用的内存
select sum(t.bytes) / 1024 / 1024 / 1024
  from user_segments t
 where t.segment_type = 'INDEX'
   and t.segment_name like '%IDX_T_FACT_NEWBUSI%';

--查看此表对应的那片表空间剩余内存，这决定了可以瞎折腾的上限   
select t.tablespace_name, sum(t.bytes) / 1024 / 1024 / 1024
  from user_free_space t
 where t.tablespace_name in
       (select p.tablespace_name
          from user_segments p
         where p.segment_name = 'T_FACT_NEWBUSINESS')
 group by t.tablespace_name;   
```

# 方法一 以空间换时间

方法一：先不动原表，直接新建一个含有全量数据的临时表，然后改名，最后重建索引和重新赋权。

此方法在第一步就宣告失败，因为刚执行没多久就被告知，ORACLE 在执行 `CREATE TABLE AS SELECT` 语句时会先将查询结果存储在临时表空间，直接这么干可能会把临时表空间占满。后来我试了下用并行，也是报错说临时表空间不足。

```sql
--1. 新建临时表
create table table_fact_newbusiness_bak0 as 
select p1.*, p2.column_a, p3.column_b
  from t_fact_newbusiness p1
  left join table_A p2 on p1.ida = p2.ida
  left join table_B p3 on p1.idb = p2.idb;
  
/*核对临时表和原表数据是否一致*/

--查看建表语句
select dbms_metadata.get_ddl('TABLE','T_FACT_NEWBUSINESS','用户名') from dual;
--查看索引名称
select t.uniqueness, t.index_name, t.*
  from all_indexes t
 where t.owner = '用户名'
   and t.table_name = 'T_FACT_NEWBUSINESS';
--查看建索引的语句
select dbms_metadata.get_ddl('INDEX', '索引名称') from dual;
select t.index_name, dbms_metadata.get_ddl('INDEX', t.index_name)
  from all_indexes t
 where t.owner = '用户名'
   and t.table_name = 'T_FACT_NEWBUSINESS';
--查看原表的权限被赋给了哪些用户
select * from user_tab_privs t where t.table_name = 'T_FACT_NEWBUSINESS';

--2. 删除原表索引（全部删除）
drop index idx_t_fact_newbusiness_01;

--3. 将原表改名
alter table  t_fact_newbusiness rename to t_fact_newbusiness_bak1;
--4. 将新表改名
alter table  t_fact_newbusiness_bak0 rename to t_fact_newbusiness;
--5. 为新表重建索引（全都重建）

--6. 重新赋权
grant select on T_FACT_NEWBUSINESS to USER1;

--7. 收集表信息
```

# 方法二 以时间换空间

方法二：新建一个只有新增字段的临时表，然后从临时表中循环取数更新到原表中去。

如果依然直接把全量数据拿来执行，跑到快晚上12点也没结束……并行的话，也会报错临时表空间不足。迫不得已改成先跑一部分，比如先试试更新一两百万数据，看看效率几何，再推算更新全部数据的时间。

建一个临时表，预先存储新增的两个字段，先按时间范围来限制数据量。

```sql
create table tmp_2column as 
select p1.item_id, p2.column_a, p3.column_b
  from t_fact_newbusiness p1
  left join table_A p2 on p1.ida = p2.ida
  left join table_B p3 on p1.idb = p2.idb;
 where p1.insert_time >= date '2023-07-01';
```

接着在原表上增加两个新字段以及字段注释。

```{sql}
alter table t_fact_newbusiness
add column_a varchar2(22)
add column_b varchar2(15);
comment on column t_fact_newbusiness.column_a is '字段名称a';
comment on column t_fact_newbusiness.column_b is '字段名称b';
```

写个循环更新数据，限定每5000条提交一次，不然的话不作限制又会把回滚段占满。可是这样也还是很慢。

```sql
declare
  v_cnt number := 0;

  cursor c_item is
    select t.item_id
      from t_fact_newbusiness t
     where t.column_a is null
       and t.insert_time >= date '2023-07-01';

begin
  for i in c_item loop
    v_cnt := v_cnt + 1;
  
    --更新两个新增字段
    update t_fact_newbusiness t1
       set column_a = (select p1.column_a
                         from tmp_2column p1
                        where p1.item_id = t1.item_id),
           column_b = (select p2.column_b
                         from tmp_2column p2
                        where p2.item_id = t1.item_id)
     where t1.item_id = i.item_id;
    if mod(v_cnt, 5000) = 0 then
      --每满5000条提交一次
      commit;
    end if;
  
  end loop;
  --提交剩余的行
  commit;
end;
```

在更新的细节上，改成将字段取值提前。这样倒是快了一点，但是保守估计1小时只能更新完22万条数据，6500万全更新完需要295个小时，肝疼……

```sql
declare
  v_cnt               number := 0;
  v_channel           varchar2(22);
  v_newbiz_scene_desc varchar2(15);

  cursor c_item is
    select t.item_id
      from t_fact_newbusiness t
     where t.column_a is null
       and t.insert_time >= date '2023-07-01';
       
begin
  for i in c_item loop
    v_cnt := v_cnt + 1;
  
    select column_a, column_b
      into v_column_a, v_column_b
      from tmp_2column
     where item_id = i.item_id;
  
    update t_fact_newbusiness t1
       set column_a = v_column_a,
           column_b = v_column_b
     where t1.item_id = i.item_id;
    if mod(v_cnt, 5000) = 0 then
      commit;
    end if;
  end loop;
  --提交剩余的行
  commit;
end;
```

# 方法三 时空间均衡？

在方法二的基础上，先在`tmp_2column`这个临时表上建个索引，然后就可以达到1秒更新一万条数据。

```sql
create index idx_tmp_2column on tmp_2column(item_id);
```

最后还剩下一个肝疼的问题，那就是需要不断地修改时间范围先 `drop table` 再 `create table` 这个临时表……

啊，冬天坐在电脑前肝博客真得太冻手了，俺要继续神隐了。
