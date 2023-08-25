---
title: "用 data.table 做数据处理的笔记"
author: yuanfan
date: 2023-08-08T20:41:07+0800
slug: data.table
categories:
  - R
tags:
  - R
draft: no
---

<!--more-->



虽然键者平日用 data.table 包做数据处理[^1]，可是正因为较为熟悉，要用时仅零零散散地根据问题搜答案，竟然从未系统地学习过它。正好最近没想好学点撒，看此包[更新日志](https://rdatatable.gitlab.io/data.table/news/index.html)作者维护得还很勤快，在开发中的1.14.9版本将会有许多新的提升，尽管此包文档现在有一百多页……总结和梳理也可以帮助自己有所提升。

>本篇笔记使用的 data.table 包的版本是1.14.8。

在一切开始之前，先创建一个 data.table 格式的数据集，方便后续复现。


```r
library(data.table)
set.seed(2023)
dt <-
  data.table(
    column1 = c(1:24),
    column2 = rep(LETTERS[1:6], 4),
    column3 = sample(1:100, 24),
    column4 = sample(50:100, 24)
  )
head(dt)
```

```
##    column1 column2 column3 column4
## 1:       1       A      80      80
## 2:       2       B      47      98
## 3:       3       C      72      93
## 4:       4       D      26      97
## 5:       5       E      44      79
## 6:       6       F      65      82
```

# 第一章 i, j, `:=`, `.()`, by, on

据键者的理解，data.table 包最基础的功能便是本章标题这六点，囊括了增、删、改、查、分组聚合和表关联。此包可以一次性对每个 data.table 类的数据框做多项操作，均由`[]`来串联每项操作并依次逐一实现。如下以 echarts4r 的基本语法为例来对比说明一下串联每个步骤的含义。

+ 在 echarts4r 中以`|>`串联每个步骤，`dt |> e_charts(column1) |> e_bar(column3)`这一小段代码就是由`|>`符号串联了三个步骤，`引入数据|>设置横轴变量|>设置绘制柱图的纵轴变量`。

+ 在 data.table 中以`[]`串联每个步骤，`dt[column2 == 'A', ][order(column3)][1:6]`这段代码由`[]`符号串联了三个步骤，`dt[筛选 column2 为 A 的行][按 column3 升序排序][查看前6行数据]`。

## 1.1. 用`i`、`j`完成对行、列的查询

在`dt[i, j]`中，i 代表行，j 代表列，通常可以用代表行、列的序号来查看或选择行、列，对行的内容上做进一步筛选时需要指定具体的列名称。

+ 使用行、列序号查看数据。


```r
# 查看一行数据
dt[1]
dt[1, ]

# 查看多行数据
dt[1:4]
dt[1:4, ]

#查看多行多列数据，注意使用向量时 c 是小写，大写会报错。
dt[c(1, 24), c(1, 3)]
```

+ 使用行、列名称查看或筛选数据。


```r
# 根据行的内容，单选
dt[column2 == 'A', c('column2', 'column3')]

# 多选
dt[column2 %in% c('A', 'B'), c('column2', 'column3')]

# 反选
dt[!column2 %in% c('A', 'B'), c('column2', 'column3')]

# 多个条件筛选时，注意一下与(&)、或(|)、非(!)的次序
dt[!column2 %in% c('A', 'B') & column3 >= 50, c('column2', 'column3')]

# 筛选数值范围，包括上下限，即>=lower&<=upper
dt[column3 %between% c(52, 80)]
# 筛选数值范围，不包括上下限，即>lower&<upper
dt[between(column3,
           lower = 52,
           upper = 80,
           incbounds = FALSE)]

# 筛选成对的数值范围，包括上下限，相当于判断是否在[40,60]或[80,100]这两个范围之中
dt[column3 %inrange% list(c(40, 80), c(60, 100))]
# 筛选成对的数值范围，不包括上下限，相当于判断是否在(40,60)或(80,100)这两个范围之中
range = data.table(start = c(40, 80), end = c(60, 100))
dt[inrange(
  column3,
  lower = range$start,
  upper = range$end,
  incbounds = FALSE
)]
```

## 1.2. 用`:=`完成对列的增、删、改

在程序语言的世界里，`=`是常见的赋值符号，而在 data.table 里面`:=`也算是赋值符号，只是范围上除了一对一赋值还可以多对多赋值。有一点需要特别注意，`:=`是通过引用原输入对象的方式完成的，也会对输入对象做出改动，比如执行`dt.new <- dt[, ':='(column5 = sample(100:200, 24))]`后，不仅 dt.new 会新增一列，连 dt 也会。

+ 一对一、多对多地新增、删除列。


```r
# 为使 dt 不受干扰，使用 copy
dt.new <- copy(dt)
# 一对一赋值，新增或删去一列
dt.new <- dt.new[, ':='(column5 = sample(100:200, 24))]
dt.new <- dt.new[, ':='(column5 = NULL)]

# 多对多赋值，新增或删去多列
# 多列中，每列一一对应地写
dt.new <-
  dt.new[, ':='(column5 = sample(100:200, 24), column6 = rep(c('0', '0岁', '1岁'), 8))]
dt.new <- dt.new[, ':='(column5 = NULL, column6 = NULL)]

# 多列中，每列不必一一对应地写，但对应顺序不变
dt.new <-
  dt.new[, c('column5', 'column6') := .(sample(100:200, 24), rep(c('0', '0岁', '1岁'), 8))]
dt.new <- dt.new[, c('column5', 'column6') := NULL]

# 或者这样删除多列
nchar <- c('column5', 'column6')
dt.new <- dt.new[, (nchar) := NULL]
```

+ 基于条件函数的新增列。


```r
dt.new <- copy(dt)
dt.new[, ':='(column5 = ifelse(column4 < 60, '不及格', ifelse(
  column4 < 80, '及格', ifelse(column4 < 85, '良好', '优秀')
)),
column6 = 0)][1:6, ]
```

```
##    column1 column2 column3 column4 column5 column6
## 1:       1       A      80      80    良好       0
## 2:       2       B      47      98    优秀       0
## 3:       3       C      72      93    优秀       0
## 4:       4       D      26      97    优秀       0
## 5:       5       E      44      79    及格       0
## 6:       6       F      65      82    良好       0
```

+ 基于行筛选的替换列。


```r
# 这一段代码中的 dt.new 继承自上一段代码
# 基于行筛选的一次替换
dt.new <- dt.new[column5 == '优秀', ':='(column6 = 100)]

# 基于行筛选的多次替换
fun1 <- function(x) {
  if (x == '优秀') {
    return(100)
  }
  else if (x == '良好') {
    return(80)
  }
  else {
    return(60)
  }
}
dt.new[, ':='(column6 = sapply(column5, fun1))][1:6,]
```

```
##    column1 column2 column3 column4 column5 column6
## 1:       1       A      80      80    良好      80
## 2:       2       B      47      98    优秀     100
## 3:       3       C      72      93    优秀     100
## 4:       4       D      26      97    优秀     100
## 5:       5       E      44      79    及格      60
## 6:       6       F      65      82    良好      80
```

data.table 中还有一些 f（fast） 开头的函数，用于更快速地做出条件判断，可用于新增或修改列。

+ `fcase()`函数相当于SQL查询语句中的 `case when ... then ... else null end`。


```r
dt.new <- copy(dt)
dt.new[, ':='(column5 = fcase(column4 < 60, '不及格', column4 < 80, '及格', column4 <
                                90, '良好', default = '优秀'))][1:6,]
```

```
##    column1 column2 column3 column4 column5
## 1:       1       A      80      80    良好
## 2:       2       B      47      98    优秀
## 3:       3       C      72      93    优秀
## 4:       4       D      26      97    优秀
## 5:       5       E      44      79    及格
## 6:       6       F      65      82    良好
```

+ `fifelse()`也是一个条件判断函数，与`fcase()`相似，区别在于只能写入一个判断条件。


```r
dt.new <- copy(dt)
dt.new[, ':='(column5 = fifelse(
  column4 < 60,
  yes = '不及格',
  no = '及格',
  na = '未知'
))][1:6,]
```

```
##    column1 column2 column3 column4 column5
## 1:       1       A      80      80    及格
## 2:       2       B      47      98    及格
## 3:       3       C      72      93    及格
## 4:       4       D      26      97    及格
## 5:       5       E      44      79    及格
## 6:       6       F      65      82    及格
```

## 1.3. 用`by`分组，`.()`聚合

+ 用`by`分组。


```r
#按照column2分组，按照 column3 排序并生成序号
dt.new <- copy(dt)
dt.new[order(column3), rank_asc := 1:.N, by = .(column2)][order(column2, column3)][1:6, ]
```

```
##    column1 column2 column3 column4 rank_asc
## 1:      13       A       3      84        1
## 2:      19       A       9      85        2
## 3:       7       A      29      55        3
## 4:       1       A      80      80        4
## 5:       2       B      47      98        1
## 6:       8       B      49      53        2
```

+ 用`.()`做聚合计算。


```r
dt[, .(
  col3_min = min(column3),
  col3_mean = mean(column3),
  col3_median = median(column3),
  col3_max = max(column3),
  col3_sd = sd(column3)
)]
```

```
##    col3_min col3_mean col3_median col3_max col3_sd
## 1:        3    46.625        44.5       98  27.883
```

+ 用`by`分组后，再用`.()`聚合计算。下面`by = .(column2)`只用一列分组，等同于`by = 'column2'`，区别是在`by = .()`中其实可以写多个列。


```r
dt[, by = .(column2), .(
  col3_min = min(column3),
  col3_mean = mean(column3),
  col3_median = median(column3),
  col3_max = max(column3),
  col3_sd = sd(column3)
)]
```

```
##    column2 col3_min col3_mean col3_median col3_max  col3_sd
## 1:       A        3     30.25        19.0       80 34.97976
## 2:       B       47     58.00        53.0       79 14.65151
## 3:       C       38     59.00        58.5       81 20.73644
## 4:       D        4     19.00        15.5       41 17.83255
## 5:       E       30     65.75        67.5       98 33.80705
## 6:       F       24     47.75        51.0       65 19.75475
```

## 1.4. 表连接

在 data.table 里面两个表连接也是用`[]`符号，如`B[A, on = 'ID']`表示 A、B 两个表通过 ID 字段关联起来，需要注意的是写在`[`符号后面的表才是关联的主表，这里相当于 sql 中的`A left join B`。

+ 关联表的字段名称不一致时。如下，是以 dt 为主表，左连接 dt.new，因此当 dt.new 中有几行数据匹配不上时会默认填上 NA 空值。如果是写习惯 sql 语句的用户，这里有一点细节需要注意，在`on = .( == )`的`==`前后的字段顺序不能写反。

  - 在 sql 里面如`select * from A t1 left join B t2 on t1.id = t2.id`，on 后面的关联条件写成`t1.id = t2.id`或者`t2.id = t1.id`都可以。

  - 在 data.table 里面如`dt.new[dt, on = .(id1 == column1)]`，`==` 前后的字段必须对应属于`[`符号前后的表，并且在关联的结果表里也是`[`符号前面的表的字段出现在前面。


```r
dt.new <- data.table(
  id1 = c(1:20),
  id2 = rep(LETTERS[1:5], 4),
  value = sample(1:10, 20, replace = TRUE)
)
tail(dt.new[dt, on = .(id1 == column1)], 6)
```

```
##    id1  id2 value column2 column3 column4
## 1:  19    D     5       A       9      85
## 2:  20    E     8       B      57      54
## 3:  21 <NA>    NA       C      38      59
## 4:  22 <NA>    NA       D      41      68
## 5:  23 <NA>    NA       E      30      89
## 6:  24 <NA>    NA       F      39      77
```

+ 两个表关联时，尽量让用于关联的字段名称保持一致。


```r
colnames(dt.new)[1:2] <- c('column1', 'column2')

# 左连接，dt left join dt.new，以 dt 为主表关联
dt.new[dt, on = 'column1']
dt.new[dt, on = .(column1)]
dt.new[dt, on = .(column1, column2)]

# 右连接， dt right join dt.new，以 dt.new 为主表关联
dt[dt.new, on = .(column1,column2)]

# 内连接，dt join dt.new，只留下两个表都能匹配上的部分
dt.new[dt, on = .(column1, column2), nomatch = 0]

# 反连接，dt.new anti join dt，只留下 dt.new 中无法与 dt 匹配上的部分
dt.new[!dt, on = .(column1, column2)]
```

# 第二章 重塑数据

为了便于探索重塑数据的函数中提供的多用参数到底有什么用，这里在 dt 的基础上增加两列组成 dt.new。


```r
dt.new <-
  dt[order(column2)][, ':='(type1 = rep(c('太阳', '月亮', '金星', '水星'), 6), type2 =
                              rep(c('日月', '日月', '星辰', '星辰'), 6))]
dt.new[1:6]
```

```
##    column1 column2 column3 column4 type1 type2
## 1:       1       A      80      80  太阳  日月
## 2:       7       A      29      55  月亮  日月
## 3:      13       A       3      84  金星  星辰
## 4:      19       A       9      85  水星  星辰
## 5:       2       B      47      98  太阳  日月
## 6:       8       B      49      53  月亮  日月
```

## 2.1. 长变宽

在 data.table 中，将数据从长变宽的函数是`dcast()`、`dcast.data.table()`，此函数中最重要的参数有两个。

+ 其一，长宽转换公式，形如`formula = LHS ~ RHS`，这里`LHS`代表公式左边填入的变量，即转换前后不做变动的部分，而`RHS`代表公式右边填入的变量，即需要转换的部分。通常，需要转换的变量应该是字符型或因子型，含有多个重复的类别，转换后每一个类别变成一个新的变量。注意，公式左右两边都可以填入多个变量。
+ 其二，转换后的新变量下需要填入的数值，如`value.var = 一个或多个变量名称`。


```r
dcast(dt.new, column2 ~ type1, value.var = 'column3')

dcast.data.table(dt.new, column2 ~ type1, value.var = c('column3', 'column4'))

dcast(dt.new, column2 ~ type1 + type2, value.var = 'column3')
```

在长变宽的转换中有一点需注意，转换后的新变量每个单元格中理应仅填入一个数值，如若不符，将出现两种情况。

+ 其一，存在缺失。
+ 其二，存在多个数值。在 dt.new 中用`column2 ~ type2`作为转换公式时，column2 与 type2 是一对多的关系，每个转换后的新变量的单元格在默认情况下会填入一个计数的数值。不过，如果用`fun.aggregate()`函数指定统计聚合函数的话，问题也会迎刃而解。


```r
# 存在缺失
dcast(
  dt.new,
  column2 + type2 ~ type1,
  value.var = 'column3',
  subset = .(column3 >= 50, column4 <= 80), # 按筛选条件对转换前数据取子集
  drop = TRUE, # 删除转换后新变量均缺失的行
  fill = 0) # 指定转换后缺失部分需填充的内容
```

```
##    column2 type2 太阳 月亮 水星 金星
## 1:       A  日月   80    0    0    0
## 2:       B  星辰    0    0   57   79
## 3:       C  日月   72   81    0    0
## 4:       E  日月    0   98    0    0
## 5:       E  星辰    0    0    0   91
## 6:       F  日月   65   63    0    0
```


```r
# 存在多个数值
dcast(dt.new,
      column2 ~ type2,
      value.var = 'column3',
      fun.aggregate = list(min, max))
```

```
##    column2 column3_min_日月 column3_min_星辰 column3_max_日月 column3_max_星辰
## 1:       A               29                3               80                9
## 2:       B               47               57               49               79
## 3:       C               72               38               81               45
## 4:       D                5                4               26               41
## 5:       E               44               30               98               91
## 6:       F               63               24               65               39
```

## 2.2. 宽变长

在 data.table 中，将数据从长变宽的函数是`melt()`、`melt.data.table()`。


```r
melt(
  dt.new,
  id.vars = c('column2', 'type1'), # 指定不变的部分，可填入一个或多个变量
  measure.vars = c('column3', 'column4'), # 指定宽变长的部分
  variable.name = '类别变量名称', 
  value.name = '数值变量名称'
)[c(1:3, 46:48), ]
```

```
##    column2 type1 类别变量名称 数值变量名称
## 1:       A  太阳      column3           80
## 2:       A  月亮      column3           29
## 3:       A  金星      column3            3
## 4:       F  月亮      column4           83
## 5:       F  金星      column4           66
## 6:       F  水星      column4           77
```

在指定需要做宽变长转换的变量时，除了直接指定变量名称，还可以根据变量名称做模式匹配。在下面的例子中，转换前的变量名称如下。

|column2|column3_min_日月|column3_min_星辰|column3_max_日月|column3_max_星辰|
|:---:|:---:|:---:|:---:|:---:|
|A|1|38|48|42|

若根据变量名称做模式匹配，如`measure.vars = patterns('_min_', '_max_')`，会将原来的4列转换为变量名称分别包含 min 和 max 的两列。美中不足的是，新变量下填入的内容是1、2等数值，而不是原变量名称中的日月、星辰等内容。

|column2|variable|value_min|value_max|
|:---:|:---:|:---:|:---:|
|A|1|1|48|
|A|2|38|42|


```r
dt.dcast <- dcast(dt.new,
                  column2 ~ type2,
                  value.var = 'column3',
                  fun.aggregate = list(min, max))

# 在 variable 中，1代表日月，2代表星辰
melt(
  dt.dcast,
  id.vars = 1,
  measure.vars = patterns('_min_', '_max_'),
  value.name = c('value_min', 'value_max')
)
```

```
##     column2 variable value_min value_max
##  1:       A        1        29        80
##  2:       B        1        47        49
##  3:       C        1        72        81
##  4:       D        1         5        26
##  5:       E        1        44        98
##  6:       F        1        63        65
##  7:       A        2         3         9
##  8:       B        2        57        79
##  9:       C        2        38        45
## 10:       D        2         4        41
## 11:       E        2        30        91
## 12:       F        2        24        39
```

## 2.3. 拆分与合并

在 data.table 中用`split()`或`split.data.table()`函数将数据框拆分成列表，用`rbindlist()`函数将列表合成数据框。尽管`rbindlist()`函数的操作对象必须是列表，但是列表中的元素可以是列表或数据框。


```r
# 用 by 参数指定按哪些字段进行拆分
split(dt.new, by = c('type1'))
split(dt.new, by = c('column2', 'type2'))
split(dt.new, by = c('column2', 'type2'), flatten = FALSE)

# 合并
rbindlist(
  split(dt.new, by = c('type1')),
  use.names = TRUE, # 按列名称合并，FALSE按位置合并
  fill = FALSE, 
  idcol = TRUE # 新增一列“.id”，指示合并前的行分别来自哪个部分
)
```

在基础 R 中有`strsplit()`用于拆分字符型向量，在 data.table 中有`tstrsplit()`函数用于根据数据中的某个字段进行分列。


```r
dt.new <- data.table(name = c('日月-星辰', '太阳-星星'),
                     value = 1:2)
# 按“-”符号分列
dt.new[, c("name1", "name2") := tstrsplit(name, "-", type.convert = TRUE)][]
```

```
##         name value name1 name2
## 1: 日月-星辰     1  日月  星辰
## 2: 太阳-星星     2  太阳  星星
```

或者将一行拆分成多行。


```r
dt.new[, (new = unlist(tstrsplit(name, '-'))), by = value]
```

```
##    value   V1
## 1:     1 日月
## 2:     1 星辰
## 3:     2 太阳
## 4:     2 星星
```

`strsplit()`函数中的参数也可在`tstrsplit()`函数中使用，这样可以使用更复杂的模式匹配拆分列。


```r
dt.new <- data.table(name = c('0岁-男', '0岁-女', '1-4岁-男', '1-4岁-女'),
                     value = 1:4)
dt.new[, c("age", "gender") := tstrsplit(name, "-(?=[^-]*$)", perl = TRUE)][]
```

```
##        name value   age gender
## 1:   0岁-男     1   0岁     男
## 2:   0岁-女     2   0岁     女
## 3: 1-4岁-男     3 1-4岁     男
## 4: 1-4岁-女     4 1-4岁     女
```

## 2.4. 比较数据

在重塑数据后，有时候我们需要比较两个数据框是否一致或存在哪些差异，在基础 R 中有`all.equal()`函数可以比较两个 R 对象是否一致，也有`union()`、`intersect()`、`setdiff()`、`setequal()`用于比较两个向量之间的差异。而在 data.table 中也有类似函数，只是用于比较的对象为 data.table 类的数据框。

+ `all.equal()`，比较两个 data.table 对象是否一致，返回 TRUE 或 FALSE。此函数还可设置一些参数细节。
  - trim.levels，默认TRUE，删除比较对象中因子变量未被使用的等级。
  - check.attributes，默认TRUE，检查 data.table 对象的各种属性是否一致。
  - ignore.col.order，默认FALSE，是否忽略比较列序号。
  - ignore.row.order，默认FALSE，是否忽略比较行序号。
+ `fintersect()`， 返回比较对象中都存在的内容，并且去重。
+ `fsetdiff()`，返回比较对象中仅存在于前者、不存在于后者的内容，并且去重。
+ `funion()`，返回比较对象中存在于前者或后者的内容，并且去重。
+ `fsetequal()`，返回比较对象是否一致的结果，与`all.equal()`的区别是只比较数据框中的内容，不比较行列序号或是否有重复。

# 第三章 特殊变量

在 data.table 中有一些独有的特殊符号，可简单理解为一些数据集自带的变量，其中`.SD`、`.BY`、`.N`、`.I`、`.GRP`、`.NGRP`用于对列的操作，`.N`也可以用于对行的操作，`.I`、`.EACHI`用于参数 by。在 R 中可以用问号来查看这些特殊符号的帮助文档，比如`?.SD`。

## 3.1. `.SD`和`.SDcols`

`.SD`中的 SD 是指 Subset of Data，意即数据的子集。一般情况下`.SD`用于对列的数据处理，当未对子集做任何筛选时子集也等于全集，因此`all.equal(dt[], dt[, .SD])`会得到 TRUE 的结果。需要注意的是，既然`.SD`代表数据的子集，那么也是可以对子集的行或列进行筛选，如下。

+ 对子集筛选行，`dt[i,]`等价于`dt[, .SD[i]]`。因此诸如`all.equal(dt[1, ], dt[, .SD[1]])`、`all.equal(dt[1, ], dt[1, .SD])`、`all.equal(dt[column2 == 'A', ], dt[, .SD[column2 == 'A']])`执行后都会得到 TRUE 的结果。
+ 对子集筛选列，搭配`.SDcols`一起使用。比如执行`all.equal(dt[1, 1:2], dt[, .SD[1], .SDcols = 1:2])`也会得到 TRUE 的结果，都是筛选第一行前两列。

除了简单的筛选，当然还可以对子集进行其他操作，比如第一章中的分组聚合、新增列等。当然，如果将`.SD`与基础 R 中的`lapply()`组合使用，可以对数据的子集使用许多已有或自定义函数。


```r
# 按 column2 分组，取每个组的第一行数据
dt[, .SD[1], by = column2]

# 按 column2 分组，取每个组的最后一行数据，且筛选两列
dt[, .SD[.N], by = column2, .SDcols = c('column1', 'column2')]

# 按 column2 分组，筛选两列，并对子集中的两列数据分别求和、求平均值
dt[,  c(lapply(.SD, sum), lapply(.SD, mean)), by = column2, .SDcols = c('column1', 'column3')]

# 在上一行代码基础上，改为仅对每组数据的前两行求和、求平均
dt[,  c(lapply(.SD[1:2], sum), lapply(.SD, mean)), by = column2, .SDcols = c('column1', 'column3')]

dt[,  c(sapply(.SD, sum), sapply(.SD, mean)), by = column2, .SDcols = c('column1', 'column3')]

# 筛选列，将筛选子集数据转换为字符型，并查看数据类型
str(dt[, lapply(.SD, as.character), .SDcols = c('column1', 'column3')])
```

## 3.2. `.BY`和`.EACHI`

在 data.table 中 by 是一个参数，用于指定对整个数据集进行分组的列。而在`DT[i, j, by = .EACHI]`中`by = .EACHI`代表对每个 i 中的元素进行分组，这里的 i 可以是一个向量或者一个数据框。


```r
# 当 i 是一个向量时，以下两种写法得到相同的结果
# dt[column2 %in% c('A', 'B'), .(max(column1)),  by = .(column2)]
# dt[c('A', 'B'), .(max(column1)), on = 'column2', by = .EACHI]

# 当i是一个数据框时，对每一个 I（EACH I）分组
i <- data.table(column2 = c('A', 'A', 'B'), column5 = c(1:3))
dt[i,  .(max(column1), max(column5), sum(column1) + sum(column5)), on = 'column2', by = .EACHI]
```

```
##    column2 V1 V2 V3
## 1:       A 19  1 41
## 2:       A 19  2 42
## 3:       B 20  3 47
```

另一个有意思的特殊变量`.BY`，可用于引用 by 中的变量，且作用于列，但暂时想不到应该在什么情况下应用更合适。

## 3.3. `.N`、`.I`、`.GRP`、`.NGRP`

`.N`、`.I`、`.GRP`、`.NGRP`是 data.table 格式的数据框中隐含的变量。


```r
# 查看最后一行数据
dt[.N, ]
# 计数，计算总行数，展示一个计数的结果数值
dt[,.N]

# 查看行的序号
dt[, .I]
# 查看按 column2 分组后，每组数据第一行所在的行序号
dt[, .I[1], by = column2]

# 查看按 column2 分组后，每组数据的组序号
dt[, .GRP, by = column2]
# 查看按 column2 分组后，每组数据的数量
dt[, .NGRP, by = column2]
```

# 第四章 重置函数（set*）

在 data.table 包文档的 set 函数的描述中有如下这样一段文字，意思是在用 set 函数修改之前的数据没有留存备份，并且会把与其相关的输入对象一块改动。比如`dt.new <- dt`，这里 dt 就是 dt.new 的相关输入对象，一旦用 set 函数修改 dt.new，也会把 dt 一块修改。在数据量很大、占了很多内存的情况下，如果只是修改了变量名称，那么很快就能再改，可是如果是修改了某些数据的精度或者增删索引，那么未必能够还原或者还原也许消耗更多时间。所以这里的 set（设置）其实等同于 reset（重置），修改需谨慎。

>In data.table, all set* functions change their input by reference. That is, no copy is made at all,
other than temporary working memory which is as large as one column.

## 4.1. 重置对象属性或变量名称

用`attributes()`函数可以查看 R 对象的属性，常见属性有类别（class）、列名称（names）、 行名称（row.names）、维度（dim）、维度名称（dimnames）等。对于 data.table 类的数据框，这些属性可以通过`setattr()`函数重置。


```r
# 和 dt.new1 <- dt 相比，使用 copy 后，重置 dt.new1 的属性不会连 dt 也一块修改
dt.new1 <- copy(dt)
attributes(dt.new1)
```

```
## $names
## [1] "column1" "column2" "column3" "column4"
## 
## $row.names
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
## 
## $class
## [1] "data.table" "data.frame"
## 
## $.internal.selfref
## <pointer: 0x000001ea32a43ec0>
```


```r
# 重置类别
setattr(dt.new1, name = 'class', value = 'data.frame')
# 重置行名称
setattr(dt.new1, name = 'row.names', value = c(2:25))
# 重置列名称
setattr(dt.new1,
        name = 'names',
        value = c('col1', 'col2', 'col3', 'col4'))
```

尽管可以用 `setattr()`函数来修改列名称，但 data.table 中还有 `setnames()`函数专门用来修改列名称，且更加灵活。这里再次赘述 set 函数会修改该函数作用对象的相关输入对象。

+ 先执行`dt.new1 <- dt`生成一个 dt.new1 对象，这时新对象的列名称和 dt 一致，分别是column1、column2、column3、column4。
+ 然后执行`setnames(dt.new1, toupper)`，将 dt.new1 所有变量名称改为大写，分别是 COLUMN1、COLUMN2、COLUMN3、COLUMN4。
+ 再执行`dt.new1 <- dt`，会发现 dt.new1 的变量名称仍然是大写。
+ 再执行`dt.new2 <- dt`，会发现连 dt.new2 的变量名称也变成大写，连 dt 的变量名称也变成了大写


```r
# 将第2:3列的名称改为大写
setnames(dt.new1, 2:3, toupper)
# 将所有列的名称改为小写
setnames(dt.new1,tolower)
# 将所有列的名称一对一替换
setnames(
  dt.new1,
  old = c('col1', 'col2', 'col3', 'col4'),
  new = c('c1', 'c2', 'c3', 'c4'))
# 将第2:3列的名称一对一替换
setnames(dt.new1, 2:3, c('v2', 'v3'))
```

## 4.2. 重置顺序

对于一个 data.table 类的数据框，可重置的顺序分为两种：行顺序和列顺序。通过`setorder()`重置后会改变内存中数据集的原始行顺序。


```r
dt.new2 = copy(dt)

# 重置行序，先按 column2 升序、再按 column1 降序
setorder(dt.new2, column2, -column1)
# 与上一行代码作用相同
setorderv(dt.new2,
          cols = c('column2', 'column1'),
          order = c(1, -1))

# 重置列序，将 column2 疑到最前面
setcolorder(dt.new2, neworder = c('column2'))
```

## 4.3. 重置键和索引

数据库中的键和索引，可以对一张表中的一个或多个字段进行设置。

+ 设置为键，通常是对这些字段增加了一些约束条件，例如取值是否唯一、是否可以为空等。比如某个字段被设置为唯一主键，那么往表中插入数据时便不允许插入该字段重复或为空的数据。
+ 设置为索引，通常是为了提高查询效率。在没有索引的情况下，查询数据通常是全表查询，有了索引，查询数据会先根据索引来查询，这样效率更快，但同时建立索引本身是会占用内存的。

而 data.table 中的键和索引与数据库中很不一样。通过`setkey()`函数设置的键有以下特点。

+ 可以设置表中任意数量的字段为键。
+ 设置为键的字段默认按升序排序，并且会改变内存中数据集原始行顺序，但不占用内存。字段中含有空值的话，空值会排在最前面。
+ 设置键可以提高对表进行查询、连接的效率，如`setkey(..., physical = FALSE)`会同时增加一个索引。


```r
dt.new3 = copy(dt)

# 设置 column1, column2 为键，默认改变内存中数据顺序，不生成索引
setkey(dt.new3, column1, column2, physical = TRUE)
# 与上一行代码作用相同
setkeyv(dt.new3, col2 = c('column1', 'column2'))

# 查看表中设置为键的字段
key(dt.new3)

# 查看表中是否存在键，是则返回 TRUE，否则返回 FALSE
haskey(dt.new3)

# 查看当前环境中所有 data.table 对象及其键
tables()
```

通过`setindex()`函数建立的索引有以下特点。

+ data.table 中的索引只是生成一个按照索引列对数据集中的行进行排序的向量，并不改变内存中数据集原始行顺序，但是占用内存。
+ data.table 中的复合索引在使用时也不等于多个单独索引。比如"column1__column2"这个复合索引，实际的索引向量是先对 column1 排序再对 column2 排序，因此同时使用两个字段或者单独使用 column1 都能用到这个索引，但单独使用 column2 时未必。


```r
# 单独设置 column1 的单独索引
setindex(dt.new3, column1)

# 设置生成 column1, column2 组成的复合索引
setindex(dt.new3, column1, column2)
# 与上一行代码作用相同
setindexv(dt.new3, cols = c('column1', 'column2'))

# 查看设置的索引
indices(dt.new3)

# 删除索引
setindex(dt.new3, NULL)
```

## 4.4. 重置数据精度

从上小学[^2]学习加减乘除等基本运算法则开始，课堂里教的都是十进制数字。所谓十进制，即所有数值均需由0、1、2、3、4、5、6、7、8、9等十位数字组成，逢十进一位。尽管电脑屏幕显示的是十进制的数字，但是实际上是以二进制的方式存储的。而使用`setNumericRounding()`函数重置的数据精度，事实上是改变了计算机内部存储的二进制数字的舍入方式，而不是十进制的四舍五入。举个例子，将十进制的13转换为二进制的1101，过程如下。

|除以2|商|余|位数|
|:---:|:---:|:---:|:---:|
|13/2|6|1|0|
|6/2|3|0|1|
|3/2|1|1|2|
|1/2|0|1|3|

这里再举个特殊例子，将十进制的0.6转换为二进制，会得到0.10011001···，一个由1001组成的无限循环小数。

|小数部分乘以2|结果|取整数部分|位数|
|:---:|:---:|:---:|:---:|
|0.6*2|1.2|1|0|
|0.2*2|0.4|0|1|
|0.4*2|0.8|0|2|
|0.8*2|1.6|1|3|
|0.6*2|1.2|1|4|
|···|···|···|···|

在不舍入的情况下，0.6是个无限循环小数，后台存储的字节数有限，因此存储的二进制并不等于真正的十进制0.6。反而是按照 data.table 中二进制的舍入规则，舍入最后1位或最后2位字节后，十进制的0.6可以被存储为一个接近它的二进制数据，在进行数值之间的匹配或连接时，0.6这个数值才存在。


```r
# 舍去最后2个字节
setNumericRounding(2)
# 舍去最后1个字节
setNumericRounding(1)
# 默认情况，关闭舍入
setNumericRounding(0)
# 获取舍入情况，0，1，还是2
getNumericRounding()
```

## 4.5. 重置数据框

在 data.table 中可通过 `setDT()`将列表和数据框（data.frame）转换为 data.table 格式的数据框，而`as.data.table()`函数也可以实现这个功能，两者的区别如下。

+ `setDT()`能操作的对象仅限于列表（list），数据框（data.frame）或 data.table，而`as.data.table()`可操作的对象是所有 R 对象。
+ `setDT()`会将操作对象的相关输入对象也一块改变，而`as.data.table()`不改动相关输入对象。

在 data.table 中还有`setDF()`函数可将列表和 data.table 转换为数据框（data.frame），其与`as.data.frame()`函数的差异与上类似。

# 第五章 其他数据处理

在真实的应用场景中处理的数据通常都是不那么规整的，说是混乱、无序的也不为过。如果说探索数据是一个抽丝剥茧、寻一些线索出来，那么在此之前整理数据的步骤便是把丝和茧都捋顺、摆出来的过程。如果是写惯了 SQL 的用户，看到 data.table 里面居然有`%like%`，一定忍不住猜想这些函数就是找 SQL 语法借的吧，那当然是的。在开源的世界里，不管是某一种语言还是某个包，都不是与世隔绝的孤岛，它们都是奔腾不息的河流，甚至有些已经发展成能纳百川的海洋。所以当键者发现 data.table 里面可以用 like 以后，真得感受到了一份惊喜。

## 5.1. 排序

### 5.1.1. 数值排序

在基础 R 中有三个容易混淆的排序函数，`order()`、`rank()`、`sort()`。在 data.table 中也有对应的三个 f 开头的函数，`forder()/setorder()`、`frank()`、`fsort()`。后者除了更快，还有以下几点区别。

+ `rank()`函数作用于向量，`order()`、`sort()`函数可作用于向量或因子。`frank()` 函数可作用于向量、列表、数据框。都可作用于数据框中的一列或多列。

+ `frank()`函数比 rank 函数多一种`ties.method = "dense"`方法。 


```r
dt.new <-
  data.table(name = c('group2', rep('group1', 3), rep('group3', 2)),
             value = c(4, 3, 3, NA, 1, 2))
# 查看行序号
# row.names(dt.new)
dt.new
```

```
##      name value
## 1: group2     4
## 2: group1     3
## 3: group1     3
## 4: group1    NA
## 5: group3     1
## 6: group3     2
```


```r
# 行序号与行的对应关系不变，默认按照数值升序排序后，返回行序号随之改变后的排列位置
# order(dt.new$value)

# 默认升序，缺失值排在最后
dt.new1 <- copy(dt.new)
dt.new1[, ':='(order =  order(dt.new1$value))][]
```

```
##      name value order
## 1: group2     4     5
## 2: group1     3     6
## 3: group1     3     2
## 4: group1    NA     3
## 5: group3     1     1
## 6: group3     2     4
```


```r
# 返回每个元素的排名，与 order 返回行序号排列位置的区别在于，默认两个同样数值的排名相同
# rank(dt.new$value)
dt.new2 <- copy(dt.new)
dt.new2[, ':='(rank =  rank(dt.new2$value))][]
```

```
##      name value rank
## 1: group2     4  5.0
## 2: group1     3  3.5
## 3: group1     3  3.5
## 4: group1    NA  6.0
## 5: group3     1  1.0
## 6: group3     2  2.0
```


```r
# 返回按数值升序排序后的新向量
# sort(dt.new$value)
dt.new3 <- copy(dt.new)
dt.new3[, ':='(sort =  sort(dt.new3$value))][]
```

```
##      name value      sort
## 1: group2     4 1,2,3,3,4
## 2: group1     3 1,2,3,3,4
## 3: group1     3 1,2,3,3,4
## 4: group1    NA 1,2,3,3,4
## 5: group3     1 1,2,3,3,4
## 6: group3     2 1,2,3,3,4
```

`frank()` 函数中的 dense 方法等同于 ORACLE 开窗函数中的 `dense_rank()`，即数值相同的元素在排序时得到一样的排名，但是所有元素的排名是连续不间断的。


```r
dt.new4 <- copy(dt.new)
dt.new4[, ':='(dense_rank =  frank(dt.new4$value, ties.method = "dense"))][]
```

```
##      name value dense_rank
## 1: group2     4          4
## 2: group1     3          3
## 3: group1     3          3
## 4: group1    NA          5
## 5: group3     1          1
## 6: group3     2          2
```

### 5.1.2. 生成序号

+ `rowid()`，按数值分组生成序号，即相同的数值内容生成不同的序号。
+ `rleid()`，也是按相同的数值分组生成序号，与 rowid 的区别是，相同的数值如果不是连续出现也会被视作不同的组。


```r
dt.new <- copy(dt)
dt.new[, ':='(rank = 1:.N)][1:6]

# 分组生成序号
rowid(dt.new$column2,prefix = "group")
dt.new[, ':='(rank_rowid = rowid(column2))][]
dt.new[, ':='(rank_rleid = rleid(column2))][]

# 其他更复杂一些的应用
dcast(dt.new, column2 ~ rowid(column2, prefix = 'group'), value.var = 'column1')

dt.new[, max(column3), by = .(column2, rleid(column2, prefix = "group"))]
```

## 5.2. 匹配 

### 5.2.1. 模式匹配

在 data.table 中可以用 like 函数做模式匹配，此函数里面还有几个参数`like(vector, pattern, ignore.case = FALSE, fixed = FALSE, perl = FALSE)`，但是在`[]`里面这样写显然与此包整体上的简洁语法不大一致，因而此包作者根据 like 函数里面的每个参数又单独开发了新的函数，如下。

+ `%like%`，等同于`like(vector, pattern, ignore.case = FALSE, fixed = FALSE, perl = FALSE)`，由于参数均默认取值 FALSE，也等同于`like(vector, pattern)`。
+ `%ilike%`，在`%like%`的基础上匹配时忽略大小写，等同于`like(vector, pattern, ignore.case = TRUE)`。
+  `%flike%`，在`%like%`的基础上匹配时使用固定字符串，等同于`like(vector, pattern, fixed = TRUE)`。相当于只匹配固定字符串，而不用写成正则表达式的形式，即便有如`$/./^`之类的特殊字符也会被当做普通字符处理。
+ `%plike%`，在`%like%`的基础上匹配时使用 Perl 正则表达式的版本，等同于`like(vector, pattern, perl = TRUE)`。


```r
dt.new <- data.table(name = c('火星', '金星', 'Mars', 'mars', 'mar.s'),
                     value = c(1:5))

# 匹配最后一个字符为星的字符串
dt.new[like(name, "星$")]
# 结果同上
dt.new[name %like% "星$"]

# 匹配 mar 开头的字符串，不忽略大小写
dt.new[name %like% "^mar"]
# 匹配 mar 开头的字符串，忽略大小写
dt.new[name %ilike% "^mar"]

# 匹配含有 ar 的字符串，以下三组结果相同
dt.new[name %like% "ar"]
dt.new[name %like% ".ar."]
dt.new[name %flike% "ar"]

# 匹配含有 ar.的字符串，
# 由于%like%本身是识别正则表达式的，“.”会被当做匹配任何字符，因而会得到所有含有 ar 的字符串
dt.new[name %like% "ar."]
# 用%flike%匹配会将特殊字符当做普通字符对待，只会得到含有 ar.的字符串
dt.new[name %flike% "ar."]
```

### 5.2.2. 其他基础 R 中的字符串处理函数

data.table中似乎没什么专门用来处理字符串的函数，相关操作可以延用基础 R 中的函数来实现。如果了解一些[正则表达式基础](https://www.runoob.com/regexp/regexp-tutorial.html)，比如一些基本的元字符的含义，可以实现更复杂的匹配。

<details>
<summary>查看一些基本元字符的含义</summary>

|特殊符号|含义|
|:---:|:-------------------------------------------------|
|`.`|匹配任意一个字符，除了换行符。|
|`-`|表示范围，比如 [a-z] 表示匹配小写字母。|
|`^`|表示开头，比如 ^love 表示匹配以love开头的字符串。|
|`$`|表示结尾，比如 love$ 表示匹配以love结尾的字符串。|
|`*`|表示匹配前面的字符或子表达式零次或多次，比如 ab* 表示匹配a后面跟着任意个b的字符串。|
|`+`|表示匹配前面的字符或子表达式一次或多次，比如 ab+ 表示匹配a后面跟着至少一个b的字符串。|
|`?`|匹配前面的表达式零次或一次。|
|`{n}`|匹配前面的表达式恰好 n 次。|
|`{n,}`|匹配前面的表达式至少 n 次。|
|`{n,m}`|匹配前面的表达式至少 n 次，但不超过 m 次。|
|`[]`|用于指定一个字符集，可以匹配其中任意一个字符。例如，[abc] 匹配 a、b 或 c 中的任意一个字符。|
|`[^]`|用于指定一个不包含在字符集中的字符。例如，[^abc] 匹配除 a、b 和 c 以外的任意一个字符。|
|`\d`|匹配任何数字字符，等价于 [0-9]。|
|`\D`|匹配任何非数字字符，等价于 [^0-9]。|
|`\s`|匹配任何空白字符，包括空格、制表符、换行符等。|
|`\S`|匹配任何非空白字符。|
|`\w`|匹配任何字母数字字符，等价于 [a-zA-Z0-9_]。|
|`\W`|匹配任何非字母数字字符，等价于 [^a-zA-Z0-9_]。|

</details>


```r
dt.new <-
  data.table(
    name = c('AMUdog', 'MONEYcat', 'DOLLORdog', 'BANGcat', 'apple-banana'),
    value = c(1:5)
  )

# 对一个字符串截取子集
substr('AMUdog', start = 2, stop = 3)
# 对数据框中的一列字符串截取子集
dt.new[, substr(name, 2, 3)]

# 计算字符串长度
dt.new[, nchar(name)]

# 匹配子集，grep 返回能匹配上的结果所在行序号，grepl 返回匹配成功或失败的 TRUE/FALSE 结果
dt.new[,grep(
  pattern = 'dog',
  x = name,
  ignore.case = TRUE, # 忽略大小写
  fixed = TRUE # 按固定字符串匹配
)]

# 替换匹配的子集
dt.new[, gsub(
  pattern = 'dog',
  replacement = 'die',
  x = name,
  ignore.case = TRUE,
  fixed = TRUE
)]
```

## 5.3. 处理日期和时间

+ 基础 R 中的函数。
  - `as.Date()`，仅包含日期。
  - `as.POSIXct()`，包含日期和时间，缺失日期时以当前日期替代，表示以1970-01-01为基准的秒数。
  - `as.POSIXlt()`，包含年月日时分秒、时区等信息。
+ data.table 中的函数。
  - `as.IDate()`，仅包含日期，表示以1970-01-01为基准的整数天数。
  - `as.ITime()`，仅包含时间，不包含日期，表示以00:00:00为基准的秒数。
  

```r
moment <- '2023-08-07 12:13:14'

as.Date(moment)
# [1] "2023-08-07"

as.IDate(moment)
# [1] "2023-08-07"

identical(as.Date(moment), as.IDate(moment))
# [1] FALSE

as.POSIXct(moment)
# [1] "2023-08-07 12:13:14 CST"

as.POSIXlt(moment, tz = 'UTC')
# [1] "2023-08-07 12:13:14 UTC"

identical(as.IDate(moment),as.POSIXct(moment))
# [1] FALSE

identical(as.IDate(moment),as.POSIXlt(moment))
# [1] FALSE

identical(as.POSIXct(moment), as.POSIXlt(moment))
# [1] FALSE

as.ITime(moment)
# [1] "12:13:14"
```


```r
# 自动生成一个数据框
IDateTime('2023-08-07 12:13:14')
```

```
##         idate    itime
## 1: 2023-08-07 12:13:14
```

+ 获取年、月、日、时、分、秒、周、季度等信息。


```r
# 获取年
year(moment)
# [1] 2023

# 获取月
month(moment)
# [1] 8

# 获取日
mday(moment)
# [1] 7

# 获取小时
hour(moment)
# [1] 12

# 获取分
minute(moment)
# [1] 13

# 获取秒
second(moment)
# [1] 14

# 获取一年中的第几天
yday(moment)
# [1] 219

# 获取一周中的第几天，默认星期天对应1，Sun < Mon < Tue < Wed < Thu < Fri < Sat
wday(moment)
# [1] 2

# 获取一年中的第几周
week(moment)
# [1] 32

# 获取一年中的第几季度
quarter(moment)
# [1] 3
```

+ 日期时间的截断、舍入、取整。


```r
# 四舍五入到小数点后指定位数
round(3.156, digits = 2)
# [1] 3.16

# 截断
trunc(3.156)
# [1] 3

# 四舍五入到指定位数
format(3.156, digits = 2)
# [1] "3.2"

# 小数向上取整
ceiling(3.156)
# [1] 4

# 小数向下取整
floor(3.156)
# [1] 3

# 截取时间
time <- as.ITime('12:13:14')
trunc(time)
# [1] "12:00:00"
trunc(time, units = 'hours')
# [1] "12:00:00"
trunc(time, units = 'minutes')
# [1] "12:13:00"
round(time, digits = 'hours')
# [1] "12:00:00"
round(time, digits = 'minutes')
# [1] "12:13:00"

# 截取日期
date <- as.IDate('2023-08-07')
trunc(date, units = 'years')
# [1] "2023-01-01"
trunc(date, units = 'months')
# [1] "2023-08-01"
round(date, digits = 'years')
# [1] "2023-01-01"
round(date, digits = 'months')
# [1] "2023-08-01"
```

+ 用format函数转换时间日期格式。
  - %Y: 四位数的年份，如2023
  - %y: 两位数的年份，如23
  - %m: 两位数的月份，如01
  - %b: 缩写的月份名称，如Jan
  - %B: 完整的月份名称，如January
  - %d: 两位数的日期，如01
  - %a: 缩写的星期名称，如Mon
  - %A: 完整的星期名称，如Monday
  - %H: 24小时制的小时，如13
  - %I: 12小时制的小时，如01
  - %M: 两位数的分钟，如30
  - %S: 两位数的秒，如59
  - %p: 上午或下午的标识，如AM或PM
  - %z: 时区的偏移量，如+0800
  - %Z: 时区的名称，如CST


```r
format(as.IDate('2023-08-07'), '%d/%m/%y')
# [1] "07/08/23"

format(as.IDate('2023-08-07'), '%d-%m-%y')
# [1] "07-08-23"

format(as.IDate('2023-08-07'), '%d-%B-%Y')
# [1] "07-八月-2023"

format(as.IDate('2023-08-07'), '%d-%b-%Y')
# [1] "07-8月-2023"

format(as.IDate('2023-08-07'), '%d-%b-%Y %a')
# [1] "07-8月-2023 周一"

format(as.POSIXct('2023-08-07 13:14:15'),'%I:%M:%S %p')
# [1] "01:14:15 下午"

format(as.POSIXct('2023-08-07 13:14:15'),'%H:%M:%S %z %Z')
# [1] "13:14:15 +0800 CST"
```

## 5.4. 处理因子
 
data.table 中似乎也没有专门用来创建或修改因子的函数，延用基础 R 中的相关函数。 
 

```r
# 用 as.factor 函数将字符型转换成因子型
dt.new <- dt[, lapply(.SD, as.factor), .SDcols = c('column2')]

# 用 is.factor 判断是否为因子
# is.factor(dt.new$column2)

# 用 factor 函数创建因子或者修改因子水平、调整因子水平的顺序
str(dt.new[, ':='(column2_new =
                    factor(column2, levels = c('D', 'E', 'F', 'A', 'B', 'C')))])
```

```
## Classes 'data.table' and 'data.frame':	24 obs. of  2 variables:
##  $ column2    : Factor w/ 6 levels "A","B","C","D",..: 1 2 3 4 5 6 1 2 3 4 ...
##  $ column2_new: Factor w/ 6 levels "D","E","F","A",..: 4 5 6 1 2 3 4 5 6 1 ...
##  - attr(*, ".internal.selfref")=<externalptr>
```

## 5.5. 对缺失值的处理

R 中的缺失、不可用值有几种，执行`?NA`可以查看。如下，创建一个含有缺失值的数据集。


```r
dt.new <- data.table(
  name = c(LETTERS[1:6]),
  value1 = c(4, 3, 3, 2, NA, 1),
  value2 = c(NA_character_, NA_integer_, NA_complex_, NA_real_, 1, 2)
)
head(dt.new)
```

```
##    name value1 value2
## 1:    A      4   <NA>
## 2:    B      3   <NA>
## 3:    C      3   <NA>
## 4:    D      2   <NA>
## 5:    E     NA      1
## 6:    F      1      2
```

```r
# 计算缺失值
# dt.new[, sapply(.SD, function(x) mean(is.na(x)))] 
```

+ `na.omit()`，根据指定列名称删掉存在缺失的行。


```r
# 默认 invert = FALSE 即删掉缺失行，改成 invert = TRUE 为保留缺失行。
na.omit(dt.new,
        cols = c('value1', 'value2'),
        invert = TRUE)
```

```
##    name value1 value2
## 1:    A      4   <NA>
## 2:    B      3   <NA>
## 3:    C      3   <NA>
## 4:    D      2   <NA>
## 5:    E     NA      1
```

+ `nafill()`，填充缺失值，函数的输入对象可以是向量、列表、数据框，但仅对双精度或整数型数据起作用，有以下三种填充方法。
  - “const”：默认值, 用一个常数值来填充缺失值，可以用 fill 参数来指定常数值。
  - “locf”: 用最近的一个非缺失值来向前填充缺失值，即 last observation carried forward。
  - “nocb”: 用最近的一个非缺失值来向后填充缺失值，即 next observation carried backward。


```r
dt.new1 <- copy(dt.new)
dt.new1[, ':='(
  value1_const = nafill(value1, fill = 0),
  value1_locf = nafill(value1, type = 'locf'),
  value1_nocb = nafill(value1, type = 'nocb')
)][]
```

```
##    name value1 value2 value1_const value1_locf value1_nocb
## 1:    A      4   <NA>            4           4           4
## 2:    B      3   <NA>            3           3           3
## 3:    C      3   <NA>            3           3           3
## 4:    D      2   <NA>            2           2           2
## 5:    E     NA      1            0           2           1
## 6:    F      1      2            1           1           1
```

+ `setnafill()`，也可用于填充缺失值，由于属于重置函数（set*），需注意在填充缺失值的同时也会改动函数作用对象的相关输入对象，且不保留副本。


```r
dt.new2 <- copy(dt.new)
setnafill(dt.new2, fill = 0, cols = c('value1'))
head(dt.new2)
```

```
##    name value1 value2
## 1:    A      4   <NA>
## 2:    B      3   <NA>
## 3:    C      3   <NA>
## 4:    D      2   <NA>
## 5:    E      0      1
## 6:    F      1      2
```

+ fcoalesce，合并含有缺失值的向量。

## 5.6. 处理时序数据

在 data.table 中竟然还有一些专门用于处理时序数据的函数，用于处理滑动窗口的聚合计算，执行 `?data.table::rollup` 或 `?data.table::frollapply`可以查看帮助文档。


```r
# 后移1位，缺失值填0
shift(dt$column1, n = 1L, fill = 0, type = 'lag')
# 前疑2位，缺失值填0
shift(dt$column1, n = 2L, fill = 0, type = 'lead')
```

# 参考文档

整理这篇笔记主要是翻了翻官网手册<https://rdatatable.gitlab.io/data.table/reference/index.html>、Enhanced data.frame <https://rdatatable.gitlab.io/data.table/reference/data.table.html>
、包的文档<https://cran.r-project.org/web/packages/data.table/data.table.pdf>、常见问题<https://cran.r-project.org/web/packages/data.table/vignettes/datatable-faq.html>，除此以外，也参考了以下这些文档。

+ [A data.table and dplyr tour](https://atrebas.github.io/post/2019-03-03-datatable-dplyr/#introduction)
+ [data.table 与 pandas](https://cosx.org/2021/01/dt-pd/)
+ [谭显英，你只需要library(data.table)](https://www.bilibili.com/video/BV1sV411b7Eo/?spm_id_from=333.337.search-card.all.click)

[^1]:最开始使用 data.table 是被 fread/fwrite 这一对快速导入导出数据的函数吸引，后来使用数据通常都是连接数据库后得到，这对函数反而用得相对少了。

[^2]:本文作者没上过幼儿园，村里小学上了一年学前班就上小学一年级，因此上小学才开始学习知识。                         
