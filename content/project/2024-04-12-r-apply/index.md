---
title: R 中的 apply 族函数
author: yuanfan
date: 2024-04-12T19:32:46+0800
slug: r-apply
categories:
  - R
tags:
  - R
draft: no
---

<!--more-->



# 一、基本数据类型与数据结构

R 中最基本的数据类型有三种：数字、文本、逻辑。其中数字和文本又可衍生出几种不同的类型。每个 R 数据对象都可以用`class()`函数来查看数据类型。用`str()`查看数据内部的基础属性，用 is 类 函数（`is.integer()/is.numeric()/is.double()/is.complex()/is.character()/is.factor()/is.logical()`）判断是否是某种数据类型，用 as 类函数（`as.integer()/as.numeric()/as.double()/as.complex()/as.character()/as.factor()/as.logical()`）转换数据类型。而日期类型较为复杂一些，这里不展开。

+ 数字
  - 整型（integer）
  - 数值型（numeric），双精度浮点型[^1]（double）
  - 复数型（complex）
+ 文本
  - 字符型（character）
  - 因子型（factor）
+ 逻辑（logical）
  - TRUE/FALSE
+ 日期[^2]（Date）

[^1]:根据 AI 的答案，在计算机中，浮点数是一种用于表示实数的数据类型。单精度浮点数和双精度浮点数都是浮点数的一种，它们的区别在于所占用的内存空间和精度不同。单精度浮点数通常占用4个字节（32位）的内存空间，可以表示的数值范围为-3.40E+38~3.40E+38，有效数字位数为7位。而双精度浮点数通常占用8个字节（64位）的内存空间，可以表示的数值范围为-1.79E+308~1.79E+308，有效数字位数为15位。因此，双精度浮点数比单精度浮点数具有更高的精度和更大的数值范围，但同时也需要更多的内存空间。

[^2]:`Date`：用于存储日期数据，通常用整数表示，数值为从1970年1月1日经过的天数。`POSIXct`：用于存储日期时间数据，可以仅包含日期部分，也可以同时包含日期和时间。它将日期时间保存为从1970年1月1日零时到该日期时间的时间间隔秒数。`POSIXlt`：也用于存储日期时间数据，可以仅包含日期部分，也可以同时包含日期和时间。它将日期时间保存为一个包含年、月、日、星期、时、分、秒等成分的列表。

数据需要存放到一起才便于分析，根据存储和处理数据方面的差异，R 中有以下几种数据结构，可以分别用英文单词命名的函数（`c()/vector()/matrix()/array()/data.frame()/list()`）来创建不同的数据结构。每个对象可以用`str()`函数来查看数据结构，用 is 类函数（`is.vector()/is.matrix()/is.array()/is.data.frame()/is.list()`）来判断是否是某种数据结构，用 as 类函数（`as.vector()/as.matrix()/as.array()/as.data.frame()/as.list()`）转换成不同的数据结构。

1. 向量（vector），一维数组，用于存储同一数据类型的数据。
2. 矩阵（matrix），二维数组，用于存储同一数据类型的数据。
3. 数组（array），不限维度，用于存储同一数据类型的数据。
4. 数据框（data.frame），二维，不同列可以存储不同数据类型，各列长度必须相同。
5. 列表（list），可以包含向量、矩阵、数组、数据框。

需要注意的是，数据框和列表可以存储不同数据类型，而向量、矩阵、数组只能存储相同数据类型，因此倘若在创建向量、矩阵或数组时引入了不同数据类型的元素，那么这些元素会被统一转换成相同数据类型。如下数字1、2和字符a、b在组成向量或矩阵时，由于在 R 中数值能转换成字符串而字符串不能转换成数值，所以数字1、2被统一转换成了字符串，而组成数据框时则保留了原本的数据类型。


```r
x <- c(1, 2, 'a', 'b')
str(x)
```

```
##  chr [1:4] "1" "2" "a" "b"
```


```r
y <- matrix(c(1, 2, 'a', 'b'), nrow = 2, ncol = 2)
str(y)
```

```
##  chr [1:2, 1:2] "1" "2" "a" "b"
```


```r
z <- data.frame(c(1, 2), c('a', 'b'))
str(z)
```

```
## 'data.frame':	2 obs. of  2 variables:
##  $ c.1..2.    : num  1 2
##  $ c..a....b..: chr  "a" "b"
```


```r
# 判断两个数据对象是否完全一致，数据结构和元素的数据类型都一致
identical(x, y) ;identical(x, z)
```

```
## [1] FALSE
```

```
## [1] FALSE
```

```r
# 判断两个数据对象中元素是否一致
setequal(x, y) ;setequal(x, z)
```

```
## [1] TRUE
```

```
## [1] FALSE
```

# 二、apply 族基本用法

> 由于 apply 族本身是 R 中的函数，而 apply 函数内部又可以通过 FUN 参数写入函数，为了避免混淆，将前者统一写作应用 apply 函数，将后者统一写作调用函数。

R 中 apply 族函数有多个，分别针对不同的数据结构或不同的应用场景，其基本功能是对输入的数据对象调用指定函数，被调用的函数是 R 中已有或者自定义的。且重点是 apply 并非是使用循环挨个对每个元素调用函数，而是批量进行，应比执行普通的 for 循环更快 。

|函数名|函数名首字母及含义|输入数据对象的类型|调用函数的应用范围|是否默认简化输出结果|
|:----:|:--------:|:--------:|:--------:|:----:|
|apply|应用 apply 调用函数|数组|选择维度|**是**|
|lapply|list，对列表调用函数|列表|所有元素|否|
|sapply|simplify，简化输出结果|列表|所有元素|**是**|
|vapply|validate，验证数据类型|列表|所有元素|否|
|mapply|multiple，多个数据对象|列表|多个数据对象的所有元素|**是**|
|tapply|table，分组计算|向量、数据框|向量|**是**|
|rapply|recursive，递归|列表|嵌套列表中所有元素|**是**|
|eapply|environment，环境|列表|环境中所有数据对象|否|

为便于后续复现，创建一些基础的数据对象。


```r
# 创建一个维度为(2, 3, 4)的三维数组
my_array <- array(c(1:24), dim = c(2, 3, 4))

# 取 my_array中的第1个矩阵
# 由于默认按列填充数据，所以第一行是 1 3 5 而不是 1 2 3
my_matrix <- my_array[, , 1]

my_vector <- my_matrix[1,]

my_list <- list(my_array, my_matrix, my_vector)

seed <- 2024
my_dataframe <-
  data.frame(value = c(1:24),
             type = sample(c('A', 'B', 'C', 'D'), replace = TRUE))
```

## 2.1.apply

apply 函数中涉及的参数用法大致如下。

`apply(X, MARGIN, FUN, ..., simplify = TRUE)`

+ X 参数，输入数据对象，应至少是2维的。

+ MARGIN 参数，用于指定按什么维度调用函数。通常情况下，填入1代表选择行，填入2代表选择列，填入`c(1, 2)`或者`1:2`代表选择所有行和列。由于 apply 函数也可应用于多维数组，因此对于一个 N 维数组来说此参数的范围是1到 N，当填入 `MARGIN = N` 时，表示分别对 N 个 N-1维的数组进行计算。

+ FUN 参数，用于指定具体调用的函数，可以是 R 中的基础函数，如求和（sum）、求平均值（mean）、求开方（sqrt）、求分位数（quantile）、排序（sort）等，或者可以自定义函数。

+ `...`，通常放在 FUN 参数后面，用于设置所调用函数的参数细节。比如`apply(X, MARGIN, FUN = quantile, probs = 1:3/4)`，相当于指定仅计算25%、50%、75%等三个分位数值。

+ simplify 参数，默认取值为 TRUE，即默认将输出结果简化为向量、矩阵。当设置`simplify = "array"`，输出结果会是更高维度的数组。

需要指出的是，应用 apply 函数输出结果的维度设定如下，这里一时看不懂也没关系，后来跑跑代码、看看输出结果自然就会明白了。

>如果每次调用 FUN 返回的向量长度一致且为 n ，并且默认 simplify 为 TRUE，则返回一个维度为`c(n, dim(X)[MARGIN])` 的数组（如果 n > 1）。如果 n 等于 1，则返回一个向量，且如果 MARGIN 的长度为 1，则返回维度为`dim(X)[MARGIN]` 的数组。 如果 n 为 0，则结果的长度为 0，但不一定是“正确”的维度。

>如果每次调用 FUN 返回的向量长度不一致，或者 simplify  为 FALSE，输出结果的维度参照 MARGIN 参数， 返回长度为 prod(dim(X)[MARGIN]) 的列表。

### 2.1.1.调用统计函数

当数据框中各列数据类型一致时，可等同于二维数组，因而在一些特殊情况下也可以对数据框使用 apply 函数。本节中的数据框 `my_dataframe` 有两列，value 列为数值型，type 列为字符型。当 FUN 参数填入的函数只能对类型一致的数据进行计算时，无论按行或按列都会报错，比如求和（sum）；而填入对数据类型没有要求的函数时，那么可以计算出结果，比如求最大（max）、判断缺失（`is.na`）等。


```r
# 按列求和，由于无法对数值和字符串进行求和，会报错
# apply(X = my_dataframe, MARGIN = 2, FUN = sum)
# 按列求最大值
apply(X = my_dataframe, MARGIN = 2, FUN = max)
```

```
## value  type 
##  "24"   "D"
```

当 FUN 参数输入的是带有汇总性质的统计函数时，如果 MARGIN 参数仅选择一个维度，那么输出的将会是按该维度的汇总结果。


```r
bak <- my_matrix
dimnames(bak)[[1]] <- c('第1行', '第2行')
dimnames(bak)[[2]] <- c('第1列', '第2列', '第3列')

# 按列求和
col.sums <- apply(X = bak, 2, sum)
# 按行求和
row.sums <- apply(X = bak, 1, sum)
# 汇总按行与列的和
rbind(cbind(bak, "行汇总" = row.sums), "列汇总" = c(col.sums, sum(col.sums)))
```

```
##        第1列 第2列 第3列 行汇总
## 第1行      1     3     5      9
## 第2行      2     4     6     12
## 列汇总     3     7    11     21
```

### 2.1.2.调用对元素进行操作的函数

当 FUN 参数输入的是针对每个元素进行转换的函数时，如果 MARGIN 参数还是仅选择一个维度，那么可能会得到“奇怪”的效果。

如下例子输入的函数是让 x 成为 x 自己，若选择的维度是1，代表按行应用函数。X 输入的是一个2行3列的矩阵，得到的结果是一个3行2列的矩阵，相当于应用 apply 后的每一行是应用前的每一列，就成了转置的效果。


```r
apply(X = my_matrix, MARGIN = 1, FUN = function(x) x)
```

```
##      [,1] [,2]
## [1,]    1    2
## [2,]    3    4
## [3,]    5    6
```

若要解释“转置”的由来，需要先知道应用 apply 函数时默认会简化结果，即`simplify = TRUE`。那么下面看看当设置成不简化结果时，输出的结果如下。即在输入的2行3列矩阵的基础上，分别按行取出了2个向量，并由此组成了一个列表。于是在默认简化结果时，这两个向量`(1, 3, 5)`和`(2, 4, 6)`以列向量（1列3行）的形式组成了一个2列3行的矩阵。


```r
apply(X = my_matrix, MARGIN = 1, FUN = function(x) x, simplify = FALSE)
```

```
## [[1]]
## [1] 1 3 5
## 
## [[2]]
## [1] 2 4 6
```

同样是让 x 成为 x 自己，若选择的维度是2，即代表按列应用函数。如下特别设定不简化结果，可以看到输入的2行3列矩阵的基础上，分别按列取出了3个向量。


```r
apply(X = my_matrix, MARGIN = 2, FUN = function(x) x, simplify = FALSE)
```

```
## [[1]]
## [1] 1 2
## 
## [[2]]
## [1] 3 4
## 
## [[3]]
## [1] 5 6
```

在默认简化结果时，取出的3个向量`(1, 2)`、`(3, 4)`、`(5, 6)`以列向量（1列2行）的形式组成了一个3列2行的矩阵，即原矩阵。


```r
apply(X = my_matrix, MARGIN = 2, FUN = function(x) x)
```

```
##      [,1] [,2] [,3]
## [1,]    1    3    5
## [2,]    2    4    6
```

### 2.1.3.应用于多维数组 

如下在一个`dim = c(2, 3, 4)`的多维数组上，选择的维度为1，即按行应用求和函数。输入的数组只有2行，于是得到2个求和结果。


```r
apply(X = my_array, MARGIN = 1, FUN = sum)
```

```
## [1] 144 156
```
第1行的求和结果是144，若是好奇144是哪些数字的和，可以打印多维数组的第一行看看。


```r
print(my_array[1,,])
```

```
##      [,1] [,2] [,3] [,4]
## [1,]    1    7   13   19
## [2,]    3    9   15   21
## [3,]    5   11   17   23
```

如若是像上一小节调用函数让 x 成为 x 自己，会得到一个12行两列的矩阵。apply 函数内部的运算过程可以这样理解：按指定维度取出子矩阵（数组）-->用`as.vector()`使子矩阵变成向量-->以列向量的形式组成最后结果矩阵。

1. 从输入的三维数组中分别按行取出子矩阵，即`my_array[1,,]`和`my_array[2,,]`这两个3行4列的矩阵。
2. 按照 apply 函数的特性——默认简化结果，子矩阵被`as.vector()`函数处理成向量，那么如`my_array[1,,]`这个3行4列的矩阵，经过`as.vector(my_array[1,,])`会变成一个列向量（12行1列）。
3. 最后输出结果的维度为`c(12, dim(my_array)[1])`，即两个列向量（12行1列）组成一个12行2列的矩阵。


```r
apply(X = my_array, MARGIN = 1, FUN = function(x) x)
```

```
##       [,1] [,2]
##  [1,]    1    2
##  [2,]    3    4
##  [3,]    5    6
##  [4,]    7    8
##  [5,]    9   10
##  [6,]   11   12
##  [7,]   13   14
##  [8,]   15   16
##  [9,]   17   18
## [10,]   19   20
## [11,]   21   22
## [12,]   23   24
```

### 2.1.4.应用于多个维度

如下对维度为2x3x4的数组调用函数让 x 成为 x 自己，最终输出结果是3个4x2的矩阵，即维度为4x2x3的数组。这个过程可以这样理解。

1. 从输入的三维数组中分别按第一维度（行）和第二维度（列）取出6个子向量，即 `my_array[1, 1, ]`、`my_array[2, 1, ]`、`my_array[1, 2, ]`、`my_array[2, 2, ]`、`my_array[1, 3, ]`、`my_array[2, 3, ]`等6个长度为4的向量。
2. 子向量被 `as.vector()`函数处理后依然是向量。
3. 最后输出结果维度为 `c(4,dim(my_array)[1:2])`，4x2x3，即6个长度为4的列向量（4行1列）组成了3个4行2列的矩阵。


```r
apply(X = my_array, MARGIN = 1:2, FUN = function(x) x)
```

```
## , , 1
## 
##      [,1] [,2]
## [1,]    1    2
## [2,]    7    8
## [3,]   13   14
## [4,]   19   20
## 
## , , 2
## 
##      [,1] [,2]
## [1,]    3    4
## [2,]    9   10
## [3,]   15   16
## [4,]   21   22
## 
## , , 3
## 
##      [,1] [,2]
## [1,]    5    6
## [2,]   11   12
## [3,]   17   18
## [4,]   23   24
```

## 2.2.lapply / sapply

lapply 或 sapply 与 apply 函数的区别有这几点：

1. apply 可输入的数据对象仅限于数组，而 lapply 或 sapply 可输入任意数据对象（ R 中任何数据对象都可以看做是一个列表）。

2. apply 指定 MARGIN 参数来选择对输入对象中的某一或某几个维度调用函数，而 lapply 或 sapply 对输入数据对象中的每个元素调用函数。

`lapply(X, FUN, ...)`

`sapply(X, FUN, ..., simplify = TRUE)`

lapply 与 apply 之间的区别是，lapply 输出结果只会是一个列表，而 sapply 在 lapply 的基础上默认将输出结果简化为向量或矩阵。如果使用 lapply 时输出列表中的所有元素都是相同的类型，则使用 sapply 时 输出结果将简化为一个向量，否则就输出一个矩阵。

如下例子所示，对一个数组使用 lapply 时，会对原数组中每个维度下的每个元素调用函数，并且将作为列表中的元素输出；而对一个数组使用 sapply 时，由于输出的每个元素都是数值型数据，于是简化成输出一个数值型向量。


```r
# 输出列表
#lapply(X = my_array, FUN = function(x) x)

# 输出向量
sapply(X = my_array, FUN = function(x)  x)
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
```

再如下例子所示，对一个数据框使用 lapply 时，会对数据框中每一列调用函数，将每一列的结果作为一个列表中的元素输出。；而对一个数据框使用 sapply 时，如果输出的各列数据类型不一致，会自动转换成统一的数据类型，且输出时简化为一个向量。


```r
lapply(X = my_dataframe, FUN = max)
```

```
## $value
## [1] 24
## 
## $type
## [1] "D"
```


```r
sapply(X = my_dataframe, FUN = max)
```

```
## value  type 
##  "24"   "D"
```

## 2.3.lapply -> vapply

与 lapply 相比，vapply 函数需要设定 FUN.VALUE 参数，用于指定调用函数后返回结果的数据类型和结构（长度），以此验证输出结果与设定的一致。下面例子中输入的数据对象是一个数据框，其中一列为数值型，另一列为字符型，不论设定 FUN.VALUE 参数为长度为1的数字型还是字符型，结果都会报错。这也说明此例中 FUN.VALUE 参数是分别对 `FUN(X[[1]])` 和 `FUN(X[[2]])`的结果进行验证的。


```r
vapply(X = my_dataframe,  FUN = max, FUN.VALUE = numeric(1))
```

>Error in vapply(my_dataframe, FUN = max, FUN.VALUE = numeric(1)) : 
  values must be type 'double', but FUN(X[[2]]) result is type 'character'


```r
vapply(X = my_dataframe,  FUN = max, FUN.VALUE = character(1))
```

>Error in vapply(my_dataframe, FUN = max, FUN.VALUE = character(1)) : 
  values must be type 'character', but FUN(X[[1]]) result is type 'integer'

## 2.4.sapply -> mapply

与 sapply 相比，mapply 可以对多个数据对象调用函数，并且可以在调用函数时设定多个参数。需要注意的是使用 mapply 所填入的参数顺序，调用的函数写在最前面。

`sapply(X = 列表1, FUN = 调用函数名称)`

`mapply(FUN = 调用函数名称, 列表1, 列表2, ..., 列表n, MoreArgs = list(调用函数参数1, 调用函数参数2, ..., 调用函数参数n))`

mapply 对多个数据对象调用函数时，并不是单独对每个数据对象调用函数。如下对`my_matrix[1, ]`和`my_matrix[2, ]`调用 sum 函数，得到的结果并不是`sum(my_matrix[1, ])`和`sum(my_matrix[2, ])`，而是对两个长度为3的向量中每组一一对应的元素来求和，这才有`1+2=3`、`3+4=7`、`5+6=11`，其实就相当于`my_matrix[1, ] + my_matrix[2, ]`。


```r
mapply(FUN = sum, my_matrix[1, ], my_matrix[2, ])
```

```
## [1]  3  7 11
```

而当 mapply 对多个不同类型的数据对象调用函数时，如下对一个向量和一个矩阵调用 sum 函数，基于 apply 默认简化结果的特点，最终输出的相当于`as.vector(my_matrix[1,] + my_matrix)`。


```r
mapply(FUN = sum, my_matrix[1, ], my_matrix)
```

```
## [1]  2  5  8  5  8 11
```

如果 mapply 中输入了多个数据对象，而调用的函数只能输入一个参数，比如让 x 成为 x 自己，这样会报错。


```r
mapply(FUN = function(x) x, my_matrix[1, ], my_matrix[2, ])
```

>Error in (function (x)  : unused argument (dots[[2]][[1]])

## 2.5.sapply -> tapply

与 sapply 相比，tapply 可以做分组计算，其中用 INDEX 参数来指定一个或多个分组的依据。

`tapply(X, INDEX, FUN = NULL, ..., default = NA, simplify = TRUE)`

如下，用 apply 对数据框调用 summary 函数，这里相当于`summary(my_dataframe)`，即输出数据框中每一列的摘要信息。


```r
sapply(X = my_dataframe, FUN = summary)
```

```
## $value
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00    6.75   12.50   12.50   18.25   24.00 
## 
## $type
##    Length     Class      Mode 
##        24 character character
```

而用 tapply 对数据框调用 summary 函数，可以指定按分组依据来计算各个组别的摘要信息。


```r
tapply(X = my_dataframe$value, INDEX = my_dataframe$type, FUN = summary)
```

```
## $A
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##       1       6      11      11      16      21 
## 
## $B
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##       3       8      13      13      18      23 
## 
## $D
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##     2.0     7.5    13.0    13.0    18.5    24.0
```

tapply 也可以指定多个分组依据，如下。


```r
my_dataframe$new_type <- sample(c('甲', '乙', '丙', '丁'), replace = TRUE)
tapply(
  X = my_dataframe$value,
  INDEX = my_dataframe[, -1],
  FUN = sum,
  default = 0 # 缺失值填0
)
```

```
##     new_type
## type 丁 甲 乙
##    A 66  0  0
##    B  0  0 78
##    D  0 84 72
```

值得一提的是 tapply 中 FUN 参数可以输入 NULL 值，此时相当于将对输入的数据对象进行分组但不做任何计算，输出的结果是数据对象中每个元素对于的组别序号。


```r
tapply(X = my_dataframe$value, INDEX = my_dataframe$type, FUN = NULL)
```

```
##  [1] 1 3 2 3 1 3 2 3 1 3 2 3 1 3 2 3 1 3 2 3 1 3 2 3
```

## 2.6.lapply -> eapply

与 lapply 相比，eapply 可以对环境中的多个数据对象调用函数，且输出时不简化结果。

`eapply(env, FUN, ..., all.names = FALSE, USE.NAMES = TRUE)`

如下是一个简单例子，用 eapply 对环境中的数据对象调用 sum 函数。


```r
# 创建一个新的环境对象，不使用哈希表（耗内存但更快），使用列表的形式存储数据对象
env <- new.env(hash = FALSE) 
env$my_matrix <- my_matrix
env$my_vector <- my_vector

tmp1 <- eapply(env, FUN = sum)
tmp1
```

```
## $my_vector
## [1] 9
## 
## $my_matrix
## [1] 21
```

创建新的环境对象相当于创建一个存储数据的容器，如果选择用列表的方式来存储，等同于将各个数据对象组成一个新的列表，所以在下面这种情况下用 eapply 和 lapply 的输出是一致的。


```r
tmp2 <-
  lapply(
    X = list(my_vector = my_vector, my_matrix = my_matrix), 
    FUN = sum
  )
identical(tmp1, tmp2)
```

```
## [1] TRUE
```

## 2.7.lapply -> rapply

与 lapply 相比，rapply 可以对嵌套列表中每层列表的每个元素调用函数。其中 r（recursive）代表的含义是递归，但仅仅只是向下递归。

`rapply(object, f, classes = "ANY", deflt = NULL, how = c("unlist", "replace", "list"), ...)`
 
如下所示，用 lapply 对一个嵌套列表调用函数求平方，执行后会报错。这是因为 lapply 是对输入列表中的每个元素调用函数，相当于分别对第一个元素1、第二个元素`list(2, 3)`求平方，而求平凡这个函数无法对一个列表生效，于是就报错了。


```r
lapply(X = list(1, list(2, 3)), FUN = function(x) {x^2})
```

>Error in x^2 : non-numeric argument to binary operator

改为用 rapply 时，尽管第一层列表中的第二个元素`list(2, 3)`也是一个列表，但仍然会对嵌套的列表中的每个元素调用函数，于是能输出结果。


```r
rapply(object = list(1, list(2, 3)), f = function(x) {x^2})
```

```
## [1] 1 4 9
```

rapply 默认设置`classes = "ANY"`，即对嵌套列表中的任何类型的数据都调用函数。当在 rapply 输入的数据对象是一个包含多种数据类型的嵌套列表时，也可以指定只对一种数据类型调用函数。比如下面，只对数值计算求平方，或只对字符转换成大写。


```r
rapply(
  object = list(1, list(2, 3, list('a', 'b'))),
  f = function(x) {
    x ^ 2
  },
  class = c("numeric")
)
```

```
## [1] 1 4 9
```


```r
rapply(
  object = list(1, list(2, 3, list('a', 'b'))),
  f = toupper,
  class = c("character")
)
```

```
## [1] "A" "B"
```

rapply 也默认设置`how  = "unlist"`，即将输出结果简化为向量。此外输出结果还可以设定成另两种方式。其一是`how  = "list"`，输出结果与输入的数据对象结构一致，但每个元素会被替换为调用函数后的结果，此时可设置 deflt 参数来填补缺失；其二是`how  = "replace"`，与前者的区别是，仅有调用了函数的部分会被替换，而没调用过函数的部分仍然与输入时保持不变。


```r
rapply(
  object = list(1, list(2, 3, list('a', 'b'))),
  f = toupper,
  class = c("character"),
  how  = "list",
  deflt = "填补" #设置 deflt 参数填补 NULL
)
```

```
## [[1]]
## [1] "填补"
## 
## [[2]]
## [[2]][[1]]
## [1] "填补"
## 
## [[2]][[2]]
## [1] "填补"
## 
## [[2]][[3]]
## [[2]][[3]][[1]]
## [1] "A"
## 
## [[2]][[3]][[2]]
## [1] "B"
```


```r
rapply(
  object = list(1, list(2, 3, list('a', 'b'))),
  f = toupper,
  class = c("character"),
  how  = "replace"
)
```

```
## [[1]]
## [1] 1
## 
## [[2]]
## [[2]][[1]]
## [1] 2
## 
## [[2]][[2]]
## [1] 3
## 
## [[2]][[3]]
## [[2]][[3]][[1]]
## [1] "A"
## 
## [[2]][[3]][[2]]
## [1] "B"
```

## 2.8.aggregate

aggregate 用于对数据进行分组汇总统计，与 apply 族很相似。由于 R 的开发者们各有各的倔强，整个 apply 族在不同应用场景下的函数名称各不相同，而 aggregate 在不同应用场景下函数名称保持统一。

`aggregate.data.frame(x, by, FUN, ..., simplify = TRUE, drop = TRUE)`

`aggregate.formula(x, data, FUN, ..., subset, na.action = na.omit)`

`aggregate.ts(x, nfrequency = 1, FUN = sum, ndeltat = 1, ts.eps = getOption("ts.eps"), ...)`

### 2.8.1.aggregate.data.frame

当 aggregate 作为 aggregate.data.frame 来使用时，作用与 tapply 相似，但如果指定多个分组依据，tapply 的输出结果会排布成列联表的形式，而 aggregate 的输出结果按列的顺序排布如下。


```r
aggregate(
  x = my_dataframe$value,
  by = list(type = my_dataframe$type, new_type = my_dataframe$new_type),
  FUN = sum)
```

```
##   type new_type  x
## 1    A       丁 66
## 2    D       甲 84
## 3    B       乙 78
## 4    D       乙 72
```

由于 aggregate 是以输入列表的形式来指定分组依据，所以在`by = list()`里也可以在原始组别的基础上做进一步划分。另外，tapply 在 INDEX 参数里指定分组依据时也可以做到这点，但似乎只能在只有一个分组依据时实现。


```r
aggregate(
  x = my_dataframe$value,
  by = list(type = my_dataframe$type, new_type = my_dataframe[, "new_type"] %in%
              c('甲', '乙')),
  FUN = sum)
```

```
##   type new_type   x
## 1    A    FALSE  66
## 2    B     TRUE  78
## 3    D     TRUE 156
```

### 2.8.2.aggregate.formula

当 aggregate 作为 aggregate.formula 来使用时，作用与 aggregate.data.frame 相似，但有以下几处区别。

区别之一如下，aggregate.formula 调用函数的列名称仍与输入时一致，而 aggregate.data.frame 调用函数的列名称变成了 x。


```r
aggregate(value ~ type + new_type, data = my_dataframe, FUN = sum)
```

```
##   type new_type value
## 1    A       丁    66
## 2    D       甲    84
## 3    B       乙    78
## 4    D       乙    72
```

区别之二如下，aggregate.formula 用单独的 subset 参数来设置组别过滤，输出结果会仅留下过滤后的组别，而 aggregate.data.frame 仍然会保留原始组别。


```r
aggregate(
  value ~ type + new_type,
  data = my_dataframe,
  FUN = sum,
  subset = my_dataframe[, "new_type"] %in% c('甲', '乙')
)
```

```
##   type new_type value
## 1    D       甲    84
## 2    B       乙    78
## 3    D       乙    72
```

区别之三如下，当需要对多个字段进行汇总统计时，aggregate.formula 要在公式左边用`cbind(value, new_value)`的方式来写，如果公式写成`value + new_value ~ type + new_type`，会被当做对 value 与 new_value 之和进行汇总。


```r
my_dataframe$new_value <- sample(1:100, 24)
aggregate(cbind(value, new_value) ~ type + new_type,
          data = my_dataframe,
          FUN = sum)
```

```
##   type new_type value new_value
## 1    A       丁    66       290
## 2    D       甲    84       228
## 3    B       乙    78       246
## 4    D       乙    72       455
```

```r
# aggregate(
#   x = my_dataframe[, c('value', 'new_value')],
#   by = list(type = my_dataframe$type, new_type = my_dataframe$new_type),
#   FUN = sum)
```

# 三、一些关于数据处理的思考题

## 3.1.第一个思考题

题目：已知有 data1 和 data2，想要得到 data3 的结果。


```r
data1 <- data.frame(
  id = c('A', 'B', 'C'),
  code = c('code1', 'code2,code3', 'code4,code5,code6'))
print(data1)
```

```
##   id              code
## 1  A             code1
## 2  B       code2,code3
## 3  C code4,code5,code6
```


```r
data2 <- data.frame(code = paste0('code', c(1:6)),
                    fee = c(100, 1000, 10000, 500, 5000, 1314))
print(data2)
```

```
##    code   fee
## 1 code1   100
## 2 code2  1000
## 3 code3 10000
## 4 code4   500
## 5 code5  5000
## 6 code6  1314
```


```r
data3 <- data.frame(
  id = c('A', 'B', 'C'),
  code = c('code1', 'code2,code3', 'code4,code5,code6'),
  fee = c(100, 11000, 6814))
print(data3)
```

```
##   id              code   fee
## 1  A             code1   100
## 2  B       code2,code3 11000
## 3  C code4,code5,code6  6814
```

这道思考题的解题重点在于要先把 data1 中的 code 列拆开，然后匹配每一个单独的 code 对应的 fee，最后汇总。

+ 第一种解法，在 R 中。

自定义字符串拆分函数，然后用 apply 族调用函数创建中间表 new_data，新表第一列按 data1 中 code 列每行拆分后的长度重复生成新 id 列，对应拆分后的内容放入新 code 列中。最后按 code 列关联，按 id 列汇总。


```r
library(data.table)
setDT(data1)
setDT(data2)

# 定义一个函数，将字符串按照逗号拆分
split_codes <- function(x) {
  strsplit(x, ",")[[1]]
}

# 将函数应用到整个 data1 表中的 code 列
new_data <-
  data.table(id = rep(data1$id, sapply(data1$code, function(x)
    length(split_codes(x)))),
    code = unlist(lapply(data1$code, split_codes)))

# 关联 fee，汇总结果
data3 <-
  data2[new_data, on = .(code)][, by = .(id), .(sum_fee = sum(fee))][data1, on = .(id)]
```

拆分字符串的步骤也可以直接放到 data.table 表格中进行。


```r
# 定义一个函数，将字符串按照逗号拆分
split_codes <- function(x) {
  tstrsplit(x, ",")
}

# 将函数应用到整个data1表中的code列
new_data <-
  data1[, lapply(.SD, split_codes), by = id][, .(code = unlist(code)), by = id]
```

+ 第二种解法，在 ORACLE 中。

ORACLE 本身是存储数据的数据库，要是刚好某张表被设计成如 data1 那样，那就不得不先递归得到具体每个 code。讲真，ORACLE 里面条条框框限制太多，做一些较为复杂的数据处理真得有些笨重。 


```sql
create table oracle_table (id VARCHAR2(4), code varchar2(400));
insert all 
  into oracle_table (id, code)
  values ('A','code1') 
  into oracle_table (id, code)
  values ('B', 'code2,code3') 
  into oracle_table (id, code)
  values ('C', 'code4,code5,code6') 
select * from dual;

--1 需要递归的方法得到字符串拆分的结果
SELECT TRIM(REGEXP_SUBSTR('code1,code2,code3', '[^,]+', 1, LEVEL)) AS code
FROM dual
CONNECT BY REGEXP_SUBSTR('code1,code2,code3', '[^,]+', 1, LEVEL) IS NOT NULL;
           
--2 将列拆分到行
select t1.id, regexp_substr(t1.code, '[^,]+', 1, level) pcode
  from oracle_table t1
CONNECT BY LEVEL <= REGEXP_COUNT(t1.code, ',') + 1
       AND PRIOR id = id
       AND PRIOR SYS_GUID() IS NOT NULL
 ORDER BY t1.id;
```

## 3.2.第二个思考题

题目：已知有一个目标文本`text <- 'a,b,c'`，判断数据框 my_dataframe2 中的 new_name 列是否与目标文本有交集。


```r
# 目标文本
text <- 'a,b,c'

# 待匹配数据
set.seed(131415926)
letters <- c("a", "b", "c", "d", "e", "f", "g")
my_dataframe2 <- data.frame(
  id = c(1:100),
  name1 = sample(letters, 100, replace = TRUE),
  name2 =  sample(letters, 100, replace = TRUE)
)

my_dataframe2$new_name <-
  mapply(
    FUN = function(x, y) {
      paste(x, y, sep = ",")
    },
    my_dataframe2$name1,
    my_dataframe2$name2
  )

head(my_dataframe2[, c("id", "new_name")], n = 4)
```

```
##   id new_name
## 1  1      d,c
## 2  2      b,a
## 3  3      e,d
## 4  4      f,f
```

+ 第一种解法，将整体比较的过程封装成一个函数。这样做的好处是，换成比较别的目标文本和别的列时，可以调用同一个函数。


```r
# 自定义函数
rule_intersection <- function(text, my_dataframe) {
  if (is.na(text) == FALSE) {
    set1 <- strsplit(text, ",")[[1]]
    set2_list <- strsplit(my_dataframe[, "new_name"], ",")
    my_dataframe$result <- sapply(
      X = set2_list,
      FUN = function(set2) {
        if (length(intersect(set1, set2)) > 0) {
          return(0)
        } else {
          return(1)
        }
      }
    )
  } else {
    my_dataframe$result <- rep(1, nrow(my_dataframe))
  }
  return(my_dataframe)
}

# 对目标文本和数据框使用函数，查看结果
head(rule_intersection(text, my_dataframe2[, c("id", "new_name")]), 4)
```

```
##   id new_name result
## 1  1      d,c      0
## 2  2      b,a      0
## 3  3      e,d      1
## 4  4      f,f      1
```

+ 第二种解法，应用 sapply 批量处理单次比较。


```r
# 分别对目标文本和 new_name 列做拆分
target_vector <- strsplit(text, split = ",")[[1]]
new_name_vectors <- strsplit(my_dataframe2$new_name, split = ",")

# 应用 sapply 批量比较是否有交集
my_dataframe2$result2 <-
  sapply(new_name_vectors, function(x) any(x %in% target_vector))

# 查看结果
head(my_dataframe2[, c("id", "new_name","result2")], 4)
```

```
##   id new_name result2
## 1  1      d,c    TRUE
## 2  2      b,a    TRUE
## 3  3      e,d   FALSE
## 4  4      f,f   FALSE
```

这里用 microbenchmark 包来比较两种解法的执行效率。在打印的结果中，数值的单位是毫秒，其中 neval 代表代码片段的执行次数，而 min、lq、mean、median、uq、max分别代表代表多次执行用时的最小值、25%分位数、均值、中位数、75%分位数、最大值。

根据比较结果，第二种解法执行效率更快。


```r
library(microbenchmark)

# 比较两个代码片段的执行效率
results <- microbenchmark(
  # 第一种解法
  code_chunk_1 = {
  rule_intersection(text, my_dataframe2[, c("id", "new_name")])
},
  # 第二种解法
  code_chunk_2 = {
  target_vector <- strsplit(text, split = ",")[[1]]
  new_name_vectors <- strsplit(my_dataframe2$new_name, split = ",")
  my_dataframe2$result3 <-
    sapply(new_name_vectors, function(x)
      any(x %in% target_vector))
},
# 指定每个代码片段执行的次数
times = 100)

# 打印结果
print(results)
```

```
## Unit: microseconds
##          expr    min      lq     mean  median     uq    max neval
##  code_chunk_1 1031.1 1056.35 1202.337 1067.45 1088.0 8504.9   100
##  code_chunk_2  251.7  261.00  287.825  266.40  273.2 1391.0   100
```

# 四、总结

1. apply  -> lapply/sapply：只有 apply 是根据指定维度来调用函数，其他 apply 族函数都是对所有元素来调用函数。
2. lapply -> sapply：简化输出结果，如将列表简化为向量。
3. lapply -> vapply：对输出结果做类型控制。
4. lapply -> eapply：调用函数的范围扩大到环境中的所有数据对象。
5. lapply -> rapply：针对嵌套列表的情况，调用函数的范围递归至每一层每个元素。
6. sapply -> mapply：可输入多个数据对象，但调用函数的参数数量需要跟数据对象的数量互相适配。
7. sapply -> tapply：可以分组调用函数。
8. tapply -> aggregate：指定分组依据的方式更灵活，可以筛选子集。

PS. 在今天下班骑自行车回去的路上，有一辆汉警快骑（摩托车）快速略过我身旁，联想到去年参加警营开放日时汉警快骑们又帅又酷的表演，俺在心里说“啊，要追上去”，然而尽管使出全力瞪踏板，也还是眼见着快骑没于车流中，叹息一秒后很快想通，毕竟自行车是追不上摩托车的嘛。
