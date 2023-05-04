---
title: 使用 R 中 DT 包为表格填充渐变颜色的笔记
author: yuanfan
date: 2022-07-20T22:09:31+0800
slug: dt-fill-color
categories:
  - R
tags:
  - R
draft: no
---

主要是从 DT 包子和 reactable 包子的官网翻了翻生成渐变颜色的案例，然后叨叨了一篇笔记。

<!--more-->

DT 包中有一些函数可以针对表格中的各列数据做格式化处理，官网有例子<https://rstudio.github.io/DT/functions.html>、<https://rstudio.github.io/DT/010-style.html>。比如`formatString(table, columns, prefix = "", suffix = "", rows = NULL)`可以在单列数据的前面或后面直接加上或者贴上固定内容；`formatPercentage()`可以将数据转换为百分比格式；`formatStyle()`可以填充表格颜色（不止）。

依照惯例，编造一份数据，便于以后复现：

```r
library(DT)

set.seed(2022)
data <- data.frame(
  group = c(rep('A', 5), rep('B', 5)),
  value1 = c(rep(1, 2), rep(0, 2), rep(0.005, 2), rep(0.995, 2), 0.4, 0.6),
  value2 = sample(1:20, 10))
```

# 基础知识

一般来说，要往表格里面填充颜色首先得知道在使用的工具中如何表达颜色。在中文互联网之内以 RGB 或者颜色作为关键词可以检索出很多相关网站，比如[RGB颜色查询对照表](https://www.sojson.com/rgb.html) 、[RGB颜色选择器](https://www.rapidtables.org/zh-CN/web/color/RGB_Color.html)、[RGB转16进制工具](https://c.runoob.com/front-end/55/)、[颜色表及html代码](http://xh.5156edu.com/page/z1015m9220j18754.html)等等。RGB，即Red（红）、Green（黄）、Blue（蓝）三原色，取值范围均为[0,255]。当这个值仅取值为0或255时，如下表所示，可以组合出2的3次方即8种颜色。理论上来说，单说颜色的数量应该能有256的3次方，即16777216这么多种，但是人的眼睛有几亿像素，而电子产品的分辨率往往到不了这么高，并且很多画图的工具也未必能识别这么多颜色。其实普通人（比如我）即使知道颜色种类应该有很多，许多时候也分辨不出来，扯远了……据说16进制格式可以表达出2的16次方，即65536种颜色。

|颜色名称|RGB|英文名|16进制格式|
|:--:|:--:|:--:|:--:|
|黑色|(0,0,0)|Black|#000000|
|蓝色|(0,0,255)|Blue|#0000FF|
|绿色|(0,255,0)|Green|#00FF00|
|青色|(0,255,255)|Cyan|#00FFFF|
|红色|(255,0,0)|Red|#FF0000|
|紫色|(255,0,255)|Magenta|#FF00FF|
|黄色|(255,255,0)|Yellow|#FFFF00
|白色|(255,255,255)|White|#FFFFFF|

# 通过改变 RGB 值大小来改变颜色

参照 DT 包官方案例，设定表格中填充的颜色由白色逐渐变为红色。其中白色的 RGB 值是`255,255,255`，红色的 RGB 值是`255,0,0`，那么由白色渐变为红色可理解为 R 值不变，G/B值逐渐减小。

```r
#数值由小到大，颜色由白到红
brks <-
  quantile(data$value2, probs = seq(.05, .95, .1), na.rm = TRUE)
clrs <- round(seq(255, 40, length.out = length(brks) + 1), 0) %>%
  {paste0("rgb(255,", ., ",", ., ")")}

datatable(data, rownames = FALSE, options = list(order = list(2, 'asc'))) |>
  formatStyle('value2', backgroundColor = styleInterval(brks, clrs))
```

![](https://yuanfan.rbind.io/images/2022-07-20-1.jpg)

其中`quantile()`是用于求分位数的函数，自不必多说。`seq(from = 1, to = 1, by = ((to - from)/(length.out - 1)), length.out = NULL)`是 R base 中一个用来生成序列的函数。如下，可以指定间隔步长的具体数值，也可以指定所需生成序列的长度。

```r
>seq(.05, .95, .1)
[1] 0.05 0.15 0.25 0.35 0.45 0.55 0.65 0.75 0.85 0.95

>seq(255, 51, length.out = length(brks) + 1)
[1] 255.0 234.6 214.2 193.8 173.4 153.0 132.6 112.2  91.8  71.4  51.0
```

像这种直接改变 RGB 值而使填充表格的颜色从白色渐变为另一种颜色的方式是很简便的，比如下图改成由白色渐变为绿色，由于白色的 RGB 值是`255,255,255`，绿色的RGB值是`0,255,0`，相当于保持G值不变，R/B值逐渐减小。

```r
#改成由白到绿
clrs <- round(seq(255, 51, length.out = length(brks) + 1), 0) %>%
  {paste0("rgb(" ,  . , ",255,", ., ")")}

datatable(data, rownames = FALSE, options = list(order = list(2, 'asc'))) |>
  formatStyle('value2', backgroundColor = styleInterval(brks, clrs))
```

![](https://yuanfan.rbind.io/images/2022-07-20-2.jpg)

同理，也可以改成由红色渐变为绿色。由于红色的 RGB 值是`255,0,0`，绿色的 RGB 值是`0,255,0`，由红渐变为绿即 R 值逐渐减小、G值逐渐增大、B值不变。

```r
#改成由红到绿
clrs <- round(seq(51, 255, length.out = length(brks) + 1), 0) %>%
  {paste0("rgb(" , 255 - . , ",", ., ", 0)")}

datatable(data, rownames = FALSE, options = list(order = list(2, 'asc'))) |>
  formatStyle('value2', backgroundColor = styleInterval(brks, clrs))
```

![](https://yuanfan.rbind.io/images/2022-07-20-3.jpg)

这种方法有一个弊端，普通人（比如我）对红黄蓝三原色如何配比组合成其他颜色的效果是很陌生的，这样弄出来的颜色总感觉有点扎眼睛。

# 借用`colorRamp`函数

一般情况下，若是觉得自己瞎选的颜色太难看的话，可以参照一些现成的例子比如[Women's World Cup ](https://glin.github.io/reactable/articles/womens-world-cup/womens-world-cup.html)。此案例中使用了一个专门用来生成渐变颜色的函数`colorRamp(colors, bias = 1, space = c("rgb", "Lab"), interpolate = c("linear", "spline"), alpha = FALSE)`（ps.这个函数我看着还是有点懵，只知道输入什么、输出什么，中间原理没明白，此次浅尝辄止）。

先瞅瞅原案例中由红变绿、由白变绿的颜色长什么样子。

```r
library(echarts4r)

data.frame(type = c('A', 'B', 'C'), value = rep(1, 3)) |>
  e_charts(type) |>
  e_pie(value, color = c("#ff2700", "#f8fcf8", "#44ab43"))

data.frame(type = c('A', 'B', 'C', 'D', 'E'), value = rep(1, 5)) |>
  e_charts(type) |>
  e_pie(value,
        color = c("#ffffff", "#f2fbd2", "#c9ecb4", "#93d3ab", "#35b0ab"))
```

|![](https://yuanfan.rbind.io/images/2022-07-20-4.jpg)|![](https://yuanfan.rbind.io/images/2022-07-20-5.jpg)|
|:-:|:-:|

接着搬来案例中生成渐变色的函数。

```r
make_color_pal <- function(colors, bias = 1) {
  get_color <- colorRamp(colors, bias = bias)
  function(x) rgb(get_color(x), maxColorValue = 255)
}

# 输入函数中的数值范围应为[0,1]
# color1，由红变绿，bias>1，则绿色更多
color1 <- make_color_pal(c("#ff2700", "#f8fcf8", "#44ab43"), bias = 1.3)
# color2，由红变绿，bias<1，则红色更多
color2 <- make_color_pal(c("#ff2700", "#f8fcf8", "#44ab43"), bias = 1.3)
# color3，由白变绿
color3 <- make_color_pal(c("#ffffff", "#f2fbd2", "#c9ecb4", "#93d3ab", "#35b0ab"), bias = 2)
```

最后，生成需要的渐变色，并填入表格中。

```r
# 把上一节中计算出来的十个分位数值拿来生成渐变颜色
brks <- unname(brks)
scaled <- (sort(brks) - min(brks)) / (max(brks) - min(brks))
clrs2 <- color1(scaled)
# clrs2 <- color2(scaled)
# clrs2 <- color3(scaled)

# 由于生成了十个颜色，在使用`styleInterval`函数时新生成只有9个数值的brks2
brks2 <-
  quantile(data$value2,
           probs = seq(.05, .95, length.out = 9),
           na.rm = TRUE)

datatable(data, rownames = FALSE, options = list(order = list(2, 'asc'))) |>
  formatStyle('value2', backgroundColor = styleInterval(brks2, clrs2))
```

![](https://yuanfan.rbind.io/images/2022-07-20-6.jpg)

# 转换数据后填充颜色

一般情况下，设置渐变颜色是与数值大小相关的，若是刚好有些数据想转换成特殊字符来展示且同时还填充渐变色的话，可以试试这么干。

```r
# 1.转换数据
format_pct <- function(value) {
  ifelse(value == 0, " \u2013 " ,   # en dash for 0%
         ifelse(value == 1, "\u2713",  # checkmark for 100%
                ifelse(
                  value < 0.01, "<1%",
                  ifelse(value > 0.99, ">99%",
                         formatC(paste0(
                           round(value * 100), "%"
                         ), width = 4))
                )))
}

data$value1.new <- format_pct(data$value1)

# 2.生成渐变颜色
# 使用`styleEqual(brks, clrs)`时，里面两个向量的长度应一致
scaled.value1 <- sort(data$value1)
clrs3 <- color3(scaled.value1)

# 3.为表格填充颜色
datatable(data,
          rownames = FALSE,
          options = list(order = list(1, 'desc'),
                         columnDefs = list(list(
                           targets = c(1), #隐藏不展示原 value1 列
                           visible = FALSE
                         )))) |>
  formatStyle(
    columns = 'value1.new', # 展示列
    valueColumns = 'value1',
    backgroundColor = styleEqual(scaled.value1, clrs3) ) 
```

![](https://yuanfan.rbind.io/images/2022-07-20-7.jpg)

```r
# 2.生成渐变颜色
# 使用`styleInterval(brks, clrs)`时，表达颜色的向量长度多1位。
scaled.value1 <- sort(data$value1)
clrs3 <- color3(scaled.value1)

brks3 <-
  quantile(data$value1,
           probs = seq(.05, .95, length.out = 9),
           na.rm = TRUE)

# 3.为表格填充颜色
datatable(data,
          rownames = FALSE,
          options = list(order = list(1, 'desc'),
                         columnDefs = list(list(
                           targets = c(1), #隐藏不展示原 value1 列
                           visible = FALSE
                         )))) |>
  formatStyle(
    columns = 'value1.new',
    valueColumns = 'value1',
    backgroundColor = styleInterval(brks3, clrs3)
  ) 
```

