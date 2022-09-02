---
title: 使用 R 中 DT 包创建多层表头的笔记
author: yuanfan
date: 2022-06-27T22:08:48+0800
slug: dt-table-header
categories:
  - R
tags:
  - R
draft: no
---

<font face="微软雅黑">主要记录使用 R 中 DT 包在绘制表格时创建多层表头的笔记，顺便粗浅地记一记通过在 R 中引入 CSS 、以及使用回调函数调用 JavaScript 来改变表格样式。

<!--more-->

# 基础知识

在 DT 包的官方介绍网站中，有针对创建两层的表头举例，见<https://rstudio.github.io/DT/>中第2.6小节。正好笔者今天要鼓捣一个有三层表头的表格，原来的例子看了看没看懂，于是上网搜了搜，找到有人写的[用html创建多层表头的笔记](https://blog.csdn.net/m0_48276047/article/details/121588528)，照着鼓捣出来了三层表头。这里需要先弄明白[html 和 CSS 的关系和区别](https://blog.csdn.net/stonebecomesrock/article/details/82223827)，本菜鸟的理解就是在一张白纸上，先用 html 语言来定义一些框框以及这些框的布局，以此作为基本机构，随后用 CSS 语言来定义各个框中内容的基本样式比如字体、字号、颜色等等。

|标签|英文全称|描述|
|:---------:|:-------------:|:---------------:|
|`<table>`||定义表格|
|`<th>`|table header cell|定义表格的表头|
|`<tr>`|table row|定义表格的行|
|`<td>`|table data cell|定义表格单元|
|`<caption>`||定义表格标题|
|`<colgroup>`|column group|定义表格列的组|
|`<col>`|column|定义用于表格列的属性|
|`<thead>`|table head|定义表格的表头|
|`<tbody>`|table body|定义表格的主体|
|`<tfoot>`|table foot|定义表格的脚注|

照旧，为了今后方便复现，先编造一份数据。

```r
library(DT)
library(htmltools)

data <- data.frame(
  `年份` = c(2017:2022),
  `类别` = 'S06',
  `住院-一级医院-上5%分位数` = sample(0:200000, 6),
  `住院-一级医院-下5%分位数` = sample(0:200000, 6),
  `住院-二级医院-上5%分位数` = sample(0:200000, 6),
  `住院-二级医院-下5%分位数` = sample(0:200000, 6),
  `住院-三级医院-上5%分位数` = sample(0:200000, 6),
  `住院-三级医院-下5%分位数` = sample(0:200000, 6),
  `门诊-一级医院-上5%分位数` = sample(0:20000, 6),
  `门诊-一级医院-下5%分位数` = sample(0:20000, 6),
  `门诊-二级医院-上5%分位数` = sample(0:20000, 6),
  `门诊-二级医院-下5%分位数` = sample(0:20000, 6),
  `门诊-三级医院-上5%分位数` = sample(0:20000, 6),
  `门诊-三级医院-下5%分位数` = sample(0:20000, 6))
```

# 创建多级表头

下面使用`htmltools::withTags(table())`就是在 R 中引入 html 语言来创建表头，但写法上有些不同。原html语言通常是如`<tr> </tr>`来定义表格中的一行，在 R 里面写作`th()`。由于需要创建多层级的表头，那么表头上横跨多行或多列的表头部分都要定义出具体跨了几行或者几列。

+ rowspan：设置单元格可横跨的行数。
+ colspan：设置单元格可横跨的列数。

```r
sketch = htmltools::withTags(table(
  class='display',
  thead(
    tr(
      th(rowspan = 3, '事故年份'),
      th(rowspan = 3, 'ICD10代码'),
      th(rowspan = 1, colspan = 6, '住院账单金额'),
      th(rowspan = 1, colspan = 6, '门诊账单金额')
    ),
    tr(
      th(rowspan = 1, colspan = 2, '一级医院'),
      th(rowspan = 1, colspan = 2, '二级医院'),
      th(rowspan = 1, colspan = 2, '三级医院'),
      th(rowspan = 1, colspan = 2, '一级医院'),
      th(rowspan = 1, colspan = 2, '二级医院'),
      th(rowspan = 1, colspan = 2, '三级医院')
    ),
    tr(
      class = 'thirdHead',
      lapply(rep(c('上5%分位数', '下5%分位数'), 6), th)
    )
  )
))
```


```r
DT::datatable(
  data,
  rownames = FALSE,
  escape = FALSE, # 不进行转义
  container = sketch, # 引入定义好的表头
  options = list(scrollY = FALSE,
                 autoWidth = TRUE)
)
```

![](https://yuanfan.rbind.io/images/2022/2022-06-27-1.png)

# 调整表头样式

据本菜鸟所知，有两种方式可以调整表头样式，一是直接在创建表头的时候引入 CSS 定义的样式，二是在 R 中调用 JS 来引入 CSS 定义的样式。

## 创建表头时引入 CSS

在定义每层表头的样式时，可以分别用如`firstHead`、`secondHead`、`thirdHead`这三个不同的名称来对不同的样式进行命名，随后形如`tr(class='firstHead',th(),th())`来逐行对表头内容进行设定。

+ 第一步，定义 CSS 样式。

````
```{css}
.firstHead th{
font-size:20px;
font-weight:bold;
background-color: #000;
color: #fff;
}

.secondHead th,
.thirdHead th{
font-size:14px;
font-weight:normal;
}
```
````

+ 第二步，创建表头且写入定义好的 CSS 样式的名称。

```r
sketch2 = htmltools::withTags(table(
  class='display',
  thead(
    tr(
      class = 'firstHead',
      th(rowspan = 3, '事故年份'),
      th(rowspan = 3, 'ICD10代码'),
      th(rowspan = 1, colspan = 6, '住院账单金额'),
      th(rowspan = 1, colspan = 6, '门诊账单金额')
    ),
    tr(
      class = 'secondHead',
      th(rowspan = 1, colspan = 2, '一级医院'),
      th(rowspan = 1, colspan = 2, '二级医院'),
      th(rowspan = 1, colspan = 2, '三级医院'),
      th(rowspan = 1, colspan = 2, '一级医院'),
      th(rowspan = 1, colspan = 2, '二级医院'),
      th(rowspan = 1, colspan = 2, '三级医院')
    ),
    tr(
      class = 'thirdHead',
      lapply(rep(c('上5%分位数', '下5%分位数'), 6), th)
    )
  )
))
```

+ 第三步，使用 DT 包绘制表格。

```r
DT::datatable(
  data,
  rownames = FALSE,
  escape = FALSE,
  container = sketch2,
  options = list(scrollY = FALSE,
                 autoWidth = TRUE)
)
```


![](https://yuanfan.rbind.io/images/2022/2022-06-27-2.png)

## 使用回调函数引入 CSS

DT 包的官方网站中<https://rstudio.github.io/DT/options.html>，此页第4.3、4.4、4.5节里有介绍使用回调函数（引入JS）的案例。原案例中`options=list(initComplete=JS(" "))`，写入 JS 语言的时候每行的代码都要用`" ",`来连接，试了试只在 JS 代码的头尾写引号也是可以的。

```r
# 原案例的写法
datatable(
  data,
  rownames = FALSE,
  escape = FALSE,
  container = sketch,
  options = list(
    initComplete = JS(
      "function(settings, json) {",
      "$(this.api().table().header()).css({'border-bottom-color': '#555','font-size': '0.8125rem','font-weight': '400'});",
      "}"
    )
  )
)

# JS()中只需头尾加上引号
datatable(
  data,
  rownames = FALSE,
  escape = FALSE,
  container = sketch,
  options = list(
    initComplete = JS(
      "function(settings, json) {
      $(this.api().table().header()).css({'border-bottom-color': '#555','font-size': '0.8125rem','font-weight': '400'});
      }"
    )
  )
)
```

![](https://yuanfan.rbind.io/images/2022/2022-06-27-3.png)

# 引入 CSS 增加外框线

DT 包也可以给单独的每一列引入 CSS 样式，形如`options=list(columnDefs=list( list(targets = 目标列序号, class = 'css样式名称') ))`。

+ 第一步，定义 css 样式。

````
```{css}
.border-left {
  border-left: 2px solid #555;
}

.border-left2 {
  border-left: 0.5px dashed #555;
}
```
````

+ 第二步，引入 css 样式并绘制表格。

```r
DT::datatable(
  data,
  rownames = FALSE,
  escape = FALSE,
  container = sketch,
  options = list(
    scrollY = FALSE,
    autoWidth = TRUE,
    columnDefs = list(
      list(targets = c(2, 8), class = 'border-left'),
      list(targets = c(4, 6, 10, 12), class = 'border-left2'),
      list(targets = c(0:13), className = 'dt-center')
    )
  )
)
```

![](https://yuanfan.rbind.io/images/2022/2022-06-27-4.png)

既然都可以通过引入 CSS 样式的方式来增加表格的外框线了，那么接下来可以改动的地方当然就很多很多啦。可是这相当于一jio踩进了一个大坑里。本菜鸟先随便写写，毕竟已经十一点了，作为阳间作息者，马上就要睁不开俺的狗眼了。今天又是想要拍拍大神的毛驴屁--但是又不好意思拍--纠结纠结--于是在自己的博客里絮叨絮叨的一天。
