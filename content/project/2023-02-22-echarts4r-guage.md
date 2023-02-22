---
title: 用 R 中 echarts4r 包绘制仪表盘
author: yuanfan
date: '2023-02-22'
slug: echarts4r-guage
categories:
  - R
tags:
  - R
draft: no
---

<!--more-->

>这篇笔记使用的 echarts4r 包的版本是0.4.4。

>仪表盘和饼图一样属于极坐标系，可以一次嵌套多层仪表盘，也可以一次嵌套多个饼图和仪表盘。

# 1.配色· ghibli 包

笔者最近知道 R 中有很多和配色相关的包，比如 ghibli 包，里面调色盘中的颜色正是来自吉卜力工作室出品的电影。

```r
library(ghibli)

# 查看各项调色盘名称和颜色
par(mfrow=c(7,3))
for(i in names(ghibli_palettes)) print(ghibli_palette(i))

# 查看单个调色盘的颜色
ghibli_palette("MarnieMedium1")

# 指定调色盘生成颜色的数量
pal <- ghibli_palette("MarnieMedium2", 7)
print(pal)
cat(pal)

# 根据调色盘得到更多连续的颜色
pal <- ghibli_palette(name = "MarnieMedium1", n = 21, type = "continuous")
cat(pal)
```

# 2.基础仪表盘

整个仪表盘的组成部分是轴（axisLine）、进度条（progress）、指针（pointer）、刻度分割线（splitLine）、刻度线（axisTick）、仪表盘指标名称（title）、仪表盘指标数值（detail）、刻度标签（axisLabel）。

## 2.1.位置、半径、角度

+ `center`：圆心的位置，默认值是`center = c('50%','50%')`，即在整张方形画布的正中间。第一个数值从0%到100%表示从左至右，第二个数值从0%到100%表示从上到下。

+ `radius`：整个仪表盘的半径。

+ `startAngle`/`endAngle`：仪表盘的起始角度和结束角度。参照12小时手表指针，起始角度或结束角度，0度为3点钟，90度为12点钟，起始角度180度为9点钟，起始角度270度为6点钟。

```r
library(echarts4r)

e1 <- e_charts() |>
  e_gauge(value = 35, name = '指标A', radius = '85%')

e2 <- e_charts() |>
  e_gauge(value = 45, name = '指标B', radius = '100%')

e3 <- e_charts() |>
  e_gauge(
    value = 55, name = '指标C', radius = '85%', startAngle = 90, endAngle = -270)

e4 <- e_charts() |>
  e_gauge(
    value = 65, name = '指标D', radius = '85%', center = c('30%', '40%'))
  
e_arrange(e1, e2, e3, e4, cols = 4, rows = 1)
```

![](https://yuanfan.rbind.io/images/2023/2023-02-22-1.png)

## 2.2.轴（axisLine）和进度条（progress）

下图中灰色部分即为仪表盘的轴，绿色部分即为仪表盘的进度条。

+ `axisLine()`用于设置轴的样式，`progress()`用于设置进度条的样式，下面三个参数是轴和进度条通用的。

  - `roundCap`：是否在两段显示成圆形；
  - `width`：宽度；
  - `opacity`：透明度。

```r
e_charts() |>
  e_gauge(value = 35, name = '指标A',
    # 设置轴的样式
    axisLine = list(
      show = TRUE,
      # 两端显示为圆形
      roundCap = TRUE,
      # 设置轴的宽度和透明度
      lineStyle = list(width = 40, opacity = 1)
    ),
    # 设置进度条的样式
    progress = list(
      show = TRUE,
      width = 20,
      roundCap = TRUE,
      # 设置进度条的颜色
      itemStyle = list(color = '#58A449FF')
    )
  )
```

![](https://yuanfan.rbind.io/images/2023/2023-02-22-2.png)

由于 Echarts 中设置轴的颜色需要引入数组，而 JavaScripts 中的数组和 R 中的数组含义有所不同，JavaScripts 中的数组可以放入不同类型的数据，而 R 中的数组要求放入同类型的数据。因此在 R 中 用 echarts4r 包绘制仪表盘时，若要设定轴的颜色，需要引入数组。

```r
e_charts() |>
  e_gauge(
    value = 35,
    name = '指标A',
    min = 0,
    max = 100,
    startAngle = 180,
    endAngle = 0,
    axisLine = list(lineStyle = list(color = list(
      c(0.4, 'red'), c(0.6, 'green'), c(1, 'blue')
    )))
  )
```

![](https://yuanfan.rbind.io/images/2023/2023-02-22-3.png)

## 2.3.指针（pointer）和刻度分隔线（splitLine）、刻度线（axisTick）

+ 在`e_guage()`函数中，有一些与刻度本身相关的参数。
  - `min`/`max`/`splitNumber`：仪表盘上刻度的最小值、最大值、分割段数。其中在`e_gauge()`中设定`splitNumber`参数时，会覆盖在刻度分隔线（`splitLine()`）中设置的效果。在刻度线（`axisTick()`）中设置`splitNumber`参数时，所设定的是两段刻度分隔线之间的分割段数。

  -  `clockwise`：默认取值`TRUE`，表示仪表盘刻度顺时针增长。

+ `splitLine()`/`axisTick()`：前者用于设置刻度上的分隔线样式，即有数字标签的刻度；后者用于设置刻度上的普通刻度线样式，即没有数字标签的刻度。两者的参数是通用的。

  - `length`/`width`：表示刻度分隔线、刻度线的线长和宽度。
  - `distance`：表示与轴的距离。
  - `type`：表示线型

+ `pointer`：用于设置指针的样式。

```r
e_charts() |>
  e_gauge(
    value = 35, name = '指标A', min = 10, max = 90,
    # 设置指针的样式
    pointer = list(
      show = TRUE,
      icon = 'triangle', # 指针形状
      length = '60%', # 指针长度
      width = 10, # 指针宽度
      itemStyle = list(color = 'black')), # 指针颜色
    # 设置刻度分隔线的样式
    splitLine = list(
      show = TRUE,
      splitNumber = 10,
      length = 20,
      distance = 20,
      lineStyle = list(color = 'blue')), # 刻度分隔线颜色
    # 设置刻度线的样式  
    axisTick = list(
      show = TRUE,
      splitNumber = 2,
      length = 10,
      distance = 10,
      lineStyle = list(color = 'green')))
```

![](https://yuanfan.rbind.io/images/2023/2023-02-22-4.png)

## 2.4.仪表盘指标名称（title）、仪表盘指标数值（detail）、刻度标签（axisLabel）

由于都是文本标签，三者的标签样式参数是通用的，都可以设置字体、边框、富文本等样式。

+ `title()`/`detail()`：分别用于设置仪表盘指标的名称和数值的样式。设置参数`offsetCenter`可调整其相对仪表盘中心的位置。

+ `axisLabel()`：用于设置刻度标签的样式，设置参数`distance`可调整其与轴之间的距离。

```r
e_charts() |>
  e_gauge(
    value = 35,
    name = '指标A',
    axisLabel = list( # 刻度标签
      show = TRUE,
      distance = 20,
      formatter = '{value}%',
      fontSize = 12,
      color = 'blue'
    ),
    title = list( # 仪表盘指标的名称
      fontSize = 24,
      offsetCenter = c('0%', '25%'), # 相对位置
      color = 'red'
    ),
    detail = list( # 仪表盘指标的数值标签
      fontSize = 36,
      formatter = '{value}%',
      offsetCenter = c('0%', '50%'), #相对位置
      color = 'green'
    )
  )
```

![](https://yuanfan.rbind.io/images/2023/2023-02-22-5.png)

# 3.示例

## 3.1.进度仪表盘

<details>
<summary>点击查看代码</summary>
<pre><code>

```r
library(htmlwidgets)
e_charts() |>
  e_gauge(
    value = 100,
    name = '指标',
    startAngle = 180,
    endAngle = 0,
    min = 0,
    max = 240,
    splitNumber = 12,
    color = '#58A449FF',
    progress = list(show = TRUE,
                    roundCap = TRUE),
    # 设置分隔线之间的分割段数
    axisTick = list(splitNumber = 2),
    title = list(show = FALSE),
    detail = list(
      width = '80%',
      height = 40,
      lineHeight = 40,
      offsetCenter = c('0%', '25%'),
      color = 'inherit',
      borderColor = 'inherit',
      boerderRadius = 20,
      borderWidth = 1,
      formatter = htmlwidgets::JS(
        "function(value){
     return '{value|' + value.toFixed(0) + '}{unit|km/h}';
      }"
      ),
     rich = list(
       value = list(
         fontSize = 45,
         fontWeight = 'bolder',
         color = 'black'
       ),
       unit = list(
         fontSize = 20,
         color = 'black',
         padding = c(10, 0,-10, 10) # 上、右、下、左
       )
     )
    )
  )

```

</code></pre>
</details>

![](https://yuanfan.rbind.io/images/2023/2023-02-22-6.png)

## 3.2.多层得分环

<details>
<summary>点击查看代码</summary>
<pre><code>

```r
e_guage_new <- function(...) {
  e_gauge(
    ...,
    #起始角度为12点钟方向
    startAngle = 90,
    endAngle = -270,
    progress = list(
      # 展示进度条
      show = TRUE,
      # 设置进度条宽度
      width = 25,
      # 多组数据时进度条不重叠
      overlap = FALSE,
      # 进度条两段为圆形
      roundCap = TRUE,
      itemStyle = list(borderWidth = 1)
    ),
    # 设置轴宽度，轴的透明度
    axisLine = list(lineStyle = list(width = 25, opacity = 0.1)),
    # 不显示指针
    pointer = list(show = FALSE),
    # 不显示刻度分割线
    splitLine = list(show = FALSE),
    # 不显示刻度线
    axisTick = list(show = FALSE),
    # 不显示刻度标签
    axisLabel = list(show = FALSE),
    # 设置数值标签的样式
    detail = list(
      width = 50,
      height = 14,
      fontSize = 14,
      color = 'inherit',
      borderColor = 'inherit',
      boerderRadius = 20,
      borderWidth = 1,
      formatter = '{value}%'
    )
  )
}

e_charts() |>
  e_guage_new(
    35,
    name = '指标A',
    radius = '75%',
    color = '#44A57CFF',
    title = list(offsetCenter = c('0%', '-40%')),
    detail = list(offsetCenter = c('0%', '-25%'),
                  formatter = '{value}%')
  ) |>
  e_guage_new(
    55,
    name = '指标B',
    radius = '85%',
    color = '#58A449FF',
    title = list(offsetCenter = c('0%', '0%')),
    detail = list(offsetCenter = c('0%', '15%'),
                  formatter = '{value}%')
  ) |>
  e_guage_new(
    75,
    name = '指标C',
    radius = '95%',
    color = '#CEC917FF',
    title = list(offsetCenter = c('0%', '40%')),
    detail = list(offsetCenter = c('0%', '55%'),
                  formatter = '{value}%')
  )
```

</code></pre>
</details>

![](https://yuanfan.rbind.io/images/2023/2023-02-22-7.png)

## 3.3.饼和仪表盘嵌套画花纹

仪表盘和饼图一样属于极坐标系，可以嵌套在一起。

<details>
<summary>点击查看代码</summary>
<pre><code>

```r
data <- data.frame(name = 'A', value1 = 1)
data |>
  e_charts(name) |>
  e_pie(value1, # 第一层 
        radius = c("0%", "20%"),
        color = '#58A449FF') |>
  e_gauge(
    value = 100,
    name = 'B',
    radius = '85%',
    startAngle = 270,
    endAngle = -90,
    # 不展示仪表盘的轴
    axisLine = list(show = FALSE),
    # 设置仪表盘进度条的颜色
    progress = list(show = TRUE, itemStyle = list(color = '#58A449FF')),
    # 不展示指针
    pointer = list(show = FALSE),
    # 不展示刻度标签
    axisLabel = list(show = FALSE),
    # 刻度分隔线
    splitLine = list(
      # 刻度分割线
      show = TRUE,
      length = 10,
      distance = 80,
      splitNumber = 12,
      lineStyle = list(
        color = '#58A449FF',
        width = 40,
        cap = 'round')),
    # 刻度线
    axisTick = list(
      # 刻度线
      show = TRUE,
      length = 10,
      distance = 20,
      lineStyle = list(
        color = '#58A449FF',
        width = 10,
        cap = 'round')),
    # 不展示
    title = list(show = FALSE),
    detail = list(show = FALSE)) |>
  e_legend(show = FALSE) |>
  e_labels(show = FALSE)

```

</code></pre>
</details>

![](https://yuanfan.rbind.io/images/2023/2023-02-22-8.png)
