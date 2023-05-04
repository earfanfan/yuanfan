---
title: echarts4r 包分面及引入新数据的笔记
author: yuanfan
date: '2022-05-18'
slug: echarts4r_facet
categories:
  - R
tags:
  - R
draft: no
---

这篇笔记使用的echarts4r包的版本是0.4.3。

<!--more-->

在[之前的笔记](https://yuanfan.rbind.io/project/e-line/)中，曾想要把一片图形区域分成上下左右四片未能实现。近日偶然留意到 echarts4r 包更新到了0.4.3版本，此包对应的 echarts.js 也更新到5.2.2版本，新版本中新增了`e_facet`函数可以实现分面的效果，也顺便记录一些温故而知新的东西。仍然是用以前编造的数据，如下。

```r
library(echarts4r)
library(data.table)

data <- data.table(
  year = as.character(c(1900:1920)),
  num1 = sample(1:20, 21, replace = TRUE),
  num2 = sample(10:30, 21, replace = TRUE),
  num3 = sample(40:60, 21, replace = TRUE),
  num4 = sample(61:100, 21, replace = TRUE),
  letter = LETTERS[1:21])
```

# 分面（e_facet）

在引入`e_facet`函数前需要先对数据做一些处理，一片图形区域要被分成多少片更小的区域，数据中就需要有一个字段能区分出每片小区域中所引入的数据。

+ 优点：代码简洁，数据准备好以后，可以一次性画很多图
+ 缺点：分面后每片图形区域的样式不能单独设置，若要单独设置还是得一个个画图，然后用`e_arrange`函数连接在一起。

```r
#使用melt函数将数据从宽变长
data.facet <-
  data.table::melt(
    data,
    id = "year", #长数据中第一个字段
    measure = c('num1', 'num2', 'num3', 'num4'),
    variable.name='type', #长数据中第二个字段，内容是'num1', 'num2', 'num3', 'num4'等四个类别
    value.name = 'num' #长数据中第三个字段，内容是num1-num4等原四个字段中的具体数值
  )

data.facet |>
  group_by(type) |>
  e_charts(year) |>
  e_bar(num) |>
  e_facet(
    rows = 2, # 分面的行数
    cols = 2, # 分面的列数
    legend_pos = "top", # 图例的位置
    legend_space = 12 # 图例与图形区域之间的距离
  ) 
```

![](https://yuanfan.rbind.io/images/2022/2022-05-18-1.png)

# 引入新数据

## 自定义单个柱子颜色（e_add_nested）

可使用`e_add_nested`函数来修改下面柱状图中单个柱子的图形样式（itemStyle）、文本标签样式（label），前提是要往原数据中增加表示具体参数的字段，且字段名字应与所要设置的参数名称一致。此法除了可以用来调整柱状图，也适用于饼状图、热力图等等。

```r
#设置柱体样式（itemStyle）中颜色（color）的具体参数值
data$color <-
  c(rep('RoyalBlue', 4), rep('red', 2), rep('RoyalBlue', 15))

#设置标签样式（label）中是否显示（show）、标签字体大小（fontSize）、标签位置（position）的具体参数值
#虽然设置最后一个柱子的标签不显示，但由于设定了标签的位置，所以这里不起作用
data$show <- c(rep('TRUE', 20), rep('FALSE', 1))
data$fontSize <- c(rep(12, 18), rep(24, 3))
data$position <- c(rep('insedeTop', 17), rep('top', 4))

data |>
  e_charts(year) |>
  e_bar(num1) |>
  e_add_nested("itemStyle", color) |>
  e_add_nested("label", show, fontSize, position)
```

![](https://yuanfan.rbind.io/images/2022/2022-05-18-2.png)

## 嵌套环形图

基于饼图半径可修改的特性，可使用`e_data`函数引入多份数据，在一个图形区域中嵌套多层饼状图、环形图，更多细节可参照[画花笔记](https://yuanfan.rbind.io/posts/echarts-flower/)

```r
data0 <- data.table(name = LETTERS[1:2], value = c(1:2))

data1 <- data.table(name1 = LETTERS[1:8], value1 = c(1:8))

data0 |>
  e_charts(name) |>
  e_pie(value, radius = c('0%', '20%')) |>
  e_data(data1, value1) |>
  e_pie(
    value1,
    radius = c('25%', '99%'),
    roseType = "radius",
    startAngle = 15,
    itemStyle = list(
      borderRadius = c('0%', '10%'),
      borderColor = '#fff',
      borderWidth = 5 ) ) |>
  e_legend(show = FALSE) |>
  e_labels(show = FALSE)
```

![](https://yuanfan.rbind.io/images/2022/2022-05-18-3.png)

## 地图上加线

参照[统计之都的原贴](https://d.cosx.org/d/423113-echarts4r/15)，通过引入数据`e_data`的方式，在地图、散点图、视觉映射的基础上再叠加一条线。

```r
city <- data.frame(
  city = c('Beijing', 'Shanghai', 'Dingxi Shi', 'Taiwan', 'Hong Kong'),
  freq = c(3807399, 2915865, 2147668, 1999026, 1617000),
  lon = c(116.407395,  121.473701, 104.626282, 121.0105733, 114.1333),
  lat = c(39.904211, 31.230416, 35.580663, 24.8050587, 22.4060834))

# 地图json文件从这里下载<https://datav.aliyun.com/portal/school/atlas/area_selector>
china_map <- jsonlite::read_json("data/中华人民共和国.json")

# 加上黑河与腾冲的经纬度数据
linedata <- data.frame(
  source_lon = c(127.526863),
  source_lat = c(50.250167),
  target_lon = c(98.490692),
  target_lat = c(24.943295),
  source_name = c("黑河"),
  target_name = c("腾冲"),
  cnt = c(2147688)
)

city |>
  e_charts(lon) |>
  e_map_register("China2", china_map) |>
  e_geo(map = "China2") |>
  e_scatter(
    serie = lat,
    size = freq ,
    bind = city,
    scale_js = "function(data){ return 80*(Math.sqrt(data[2]/ 5e7) + 0.1);}",
    coord_system = "geo" ) |>
  e_visual_map(freq, show = FALSE, scale = e_scale) |>
  e_legend(show = FALSE) |>
  e_tooltip(trigger = "axis")|>
  e_data(linedata)|> # 引入黑河-腾冲线的经纬度数据
  e_lines(
    source_lon, # 起点经度
    source_lat, # 起点纬度
    target_lon, # 终点经度
    target_lat, # 终点纬度
    source_name, # 起点城市
    target_name, # 终点城市
    cnt,
    coord_system = "geo", # 地理坐标系
    name = "线的名字",
    lineStyle = list(normal = list(
      curveness = 0, # 线的弯曲度
      color = "red", # 线的颜色
      width = 2 #线宽
    )) ) 
```

![](https://yuanfan.rbind.io/images/2022/2022-05-18-4.png)

## 改变横轴的排列顺序

在直角坐标系中，当横轴的数据是数值型时，可在`e_x_axis()`中指定`inverse=TRUE/FALSE`来改变横轴的排列顺序，而当横轴的数据是字符型时，可用`data=c()`这种引入数据的方式来指定横轴中各个值的排列位置。

```r
data[letter%in%c('A','B','C','D'),]|>
  e_charts(letter)|>
  e_bar(num1)|>
  e_x_axis(data=c('B','A','D','C'))
```

![](https://yuanfan.rbind.io/images/2022/2022-05-18-5.png)
