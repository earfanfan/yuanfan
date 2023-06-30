---
title: 用 ggplot2 绘制柱状图的笔记
author: yuanfan
date: 2023-07-01T07:00:54+0800
slug: ggplot2 bar
categories:
  - R
tags:
  - R
draft: no
output:
  blogdown::html_page:
    toc: true
---




<!--more-->

由于俺会用的 R 绘图包只有 echarts4r，此包语法简洁、高效易用，用来做数据的可视化展示时够用，但用来做探索性数据分析稍有不足，且 echarts4r 不支持 crosstalk，暂无法完成图表数据共享，所以还需要再学习一个作图系统达成互补。备选项有二：plotly 和 ggplot2。考虑到 ggplot2 可以用`plotly::ggplotly()`转换成 plotly 图形，且网络上介绍它的文章和书籍更多，可绘制的图形种类也更丰富，所以尽管此包官方文档相当厚实，也先学了再说。后面还是不够用的话，再学别的。

一般来说，图形可展现数据的占比、大小、趋势、结构、层次、分配、归类、变化、流动等特点。鉴于 ggplot2 以及各类 gg 包子们能够绘制的图形类型繁多，俺决定从基础的柱状图开始学起。由于俺现在对 ggplot2 不够熟悉，因此笔记力求细致，若有错漏之处，猴年马月再改。

>本篇笔记所用的 ggplot2 版本是3.4.2。

# 一、ggplot2 基础概念

使用 ggplot2 绘图需要三个最基本的元素：数据集、几何对象、图形属性映射。数据集自不必再说，没有数据就无法绘图。几何对象就是将数据展示到坐标系上的几何图形对象，比如折线图就是直线几何对象，条形图就是条形几何对象，散点图就是点几何对象。在一个二维坐标系上，最基础的几何图形就是点和线，线又可以分成直线、曲线，多条线合起来组成了面，也就有了更加丰富的几何图形如矩形、圆形、多边形等。但只有数据和几何图形是不够的，还需要有更多的图形属性使图形展现的信息更加清晰、简洁，比如将多组数据绘制成散点图时，无法区分哪些点属于哪个组别，那么可以对不同组别的点映射不同的形状、颜色、透明度、大小来加以区分。

ggplot2 功能十分强大，可调整的图形细节也十分丰富，整个图形语法系统可以扩展出如下几个方面：数据集（DATA）、几何对象（GEOM_FUNCTION）、图形属性映射（`mapping = aes()`）、统计变换（**stat**istic transformation）、位置调整（position）、坐标系（**coord**inate）、分面（facet）、标度（**scale**）、主题（theme）。其中，标度（scale）即视觉映射，用于将数据映射到几何对象的颜色、形状、大小等图形属性。在图形属性映射（`mapping = aes()`）里面也可以指定颜色、形状等属性，但是在标度（scale）里面指定的视觉映射更具特色，前者指定更统一的属性，后者指定更加差异化的属性，比如渐变颜色等。

```
ggplot(data =  <DATA> ) +
  <GEOM_FUNCTION>(
  mapping = aes(<MAPPINGS>),
  stat =  <STAT> , 
  position =  <POSITION>) +
  <COORDINATE_FUNCTION> +
  <FACET_FUNCTION> +
  <SCALE_FUNCTION> +
  <THEME_FUNCTION>
```

ggplot2 有别于其他绘图包的最大特点是图层，关于图层这个概念，有几点需要梳理清楚。

+ 其一，**每一个几何对象都是一个图层**，对应地，每个绘制几何对象的函数如 GEOM_FUNCTION()都会创建一个图层，都有一个mapping = aes()，这是设置图形属性映射的函数。

+ 其二，**除了 `ggplot()`图层，各 `GEOM_FUNCTION()`图层中的图形属性映射仅对本图层起作用**。绘制一个最基本的 ggplot2 图形至少需要两个图层，一个 `ggplot()`和一个 `GEOM_FUNCTION()`，通常由前者引入数据集，由后者指定绘制的具体几何图形，比如绘制柱状图就是 `geom_bar()`，绘制散点图就是 `geom_point()`。需要注意的是，`ggplot()`图层里面的映射属于全局映射，而 `GEOM_FUNCTION()`图层里面的映射属于局部映射，但 `GEOM_FUNCTION()`图层的映射优先级更高且设定内容只对本图层起作用。因此，当 `ggplot()`和 `GEOM_FUNCTION()`都设定了同一种图形属性的不同内容时，后者的设定会覆盖前者；而当某种图形属性在 `ggplot()`中有设定而在 `GEOM_FUNCTION()`中没有设定时，后者缺失的部分会直接引用前者设定的内容。

+ 其三，除了绘制几何对象的函数，其他函数也可以修改图层中的图形属性，其优先级依`+`号后面的函数编写顺序而定。

## 1.1.图形属性映射（Aes）

在每个几何对象函数中，有两个有关图形属性映射的大类，一是轴的映射，比如在直角坐标系下指定 x、y 轴需映射的变量；二是美学映射，根据[ ggplot2 的美学规范（Aesthetic specifications）](https://ggplot2.tidyverse.org/articles/ggplot2-specs.html)，又可细分为如下几类。

+ 颜色

  - colour/color[^1]：颜色或边框颜色，可以填写一个代表颜色的字符串如`"red"`，或 RGB 值如`"#44A57CFF"`，或者填写一个数据集中的变量名称，默认按此变量分组映射不同的颜色。
  
  - fill：填充颜色，填入一个变量名称时，同样默认按此变量分别映射不同的填充颜色。填入一个字符串时，字符串的内容也是图例项的名称。
  
+ 点

  - shape：形状。填入一个变量名称时，默认按此变量分别映射不同的形状，但 ggplot2只能同时使用6种形状，第7个或更多类别的形状将不会出现在图形中。也可填入单个字符，以此作为点的形状展示。或者填入代表形状的英文单词，如 circle、square、diamond、triangle 等。或填入0-24之间的整数数字，分别代表不同的形状，相同形状由 color 和 fill 参数来区分，比如空心形状（0-14）的边界颜色由 color 设定，实心形状（15-20）的填充颜色由 color 设定，填充形状（21-24）的边界颜色由 color 设定、填充颜色由 fill 设定。
  
  - size：大小，可以填入数字，单位是毫米，或者填入一个变量名称，需注意这是一个有序图形属性。
  
  - alpha：透明度，可以填0-1之间的数值，或者填入一个变量名称,这同样是一个有序图形属性。
  
+ 线

  - linetype：线型，填数字或字符串`(0 = "blank", 1 = "solid", 2 = "dashed", 3 = "dotted", 4 = "dotdash", 5 = "longdash", 6 = "twodash")`，分别对应空白、实线、虚线、点线、点划线、长虚线、点划线。
  
  - linewidth：线宽，填数字。
   
  - lineend：线末端的形状，填字符串，圆形（round）, [butt](http://sape.inf.usi.ch/quick-reference/ggplot2/lineend#:~:text=The%20lineend%20parameter%20accepts%20one%20of%20three%20possible,%22round%22%2C%20%22butt%22%2C%20or%20%22square%22.%20The%20default%20is%20%22butt%22)，方形（square），默认为 butt。
  
  - linejoin：折线的连接处的形状，填字符串，圆形（round）、斜角（mitre）、斜面（bevel），默认为圆形（round）。
  
+ 文字

  - 字体（Font Family）：参数名称是 family，默认字体是 sans，也可以填 serif、mono 等。
  
  - 字型（Font face）：参数名称是 fontface，是字体粗细、倾斜的结合体，比如 italic 表示倾斜，而 bold.italic 表示加粗倾斜。
  
  - 字号（Font size）：比如 `size = 12/.pt` 表示字号为12。
  
  - 对齐方式（Justification）：分为水平参数 hjust 和垂直参数 vjust，取值范围可以是0-1之间的数值，或者 top、middle、bottom、left、center、right 中的一个字符串。
  
+ 分组

  - group：分组，自动为分类变量的每个类别绘制一个独立的几何对象。可以填任意常数，代表不分组。或者填入一个变量名称来指定分组变量。

## 1.2.几何图形（Geoms）

在 ggplot2 中，所有的几何图形以及基本的点、线元素都是一个 `GEOM_FUNCTION()`函数。与 echarts4r 的语法相比，两者对图形类别划分的粗细不同，但也有很多相似之处。又由于平时绘图翻[ echarts4r 入门](https://cosx.org/2021/12/introduction-to-echarts4r/)和[ echarts 配置项手册](https://echarts.apache.org/zh/option.html#series)比较多，俺决定整理一个 echarts4r 与 ggplot2 的对照表，尽早作出区分，免得学习前期不同语法在脑子里打架。

| ggplot2 类别|图形名称| ggplot2 函数|对照 echarts4r 函数|
|:------:|:-----:|:----------:|:----------:|
|图形基础元素|空白矩形单元格|`geom_blank()`|[graphic](https://echarts4r.john-coene.com/reference/graphic.html)|
|-|曲线|`geom_curve()`|？|
|-|路径|`geom_path()`|？|
|-|多边形|`geom_polygon()`|`e_polygon_g()`|
|-|矩形|`geom_rect()`|`e_rect_g()`/`e_mark_area()`|
|-|带状图形|`geom_ribbon()`|`e_band()`|
|单变量（连续型）|基础折线图|`geom_line()`|`e_line()`|
|-|面积图|`geom_area()`|`e_area()`|
|-|阶梯折线图|` geom_step(direction = "hv")`|`e_step()`|
|-|密度曲线图|`geom_density(kernel = "gaussian")`|`e_density()`|
|-|点图|`geom_dotplot()`|？|
|-|频数图？|`geom_freqpoly()`|？|
|-|直方图|`geom_histogram()`|`e_histogram()`|
|-|QQ图|`geom_qq()`|？|
|单变量（离散型）|柱状图/条形图|`geom_bar()`|`e_bar()`|
|-|饼图|？|`e_pie()`|
|双变量（两个连续型）|标签图？|`geom_label()`/`geom_text()`|？|
|-|散点图|`geom_point()`|`e_scatter()`|
|-|分位数图|`geom_quantile()`|？|
|-|地毯图？|` geom_rug(sides = “bl") `|？|
|-|回归线|`geom_smooth(method = lm)`|`e_lm()`|
|双变量（离散型&连续型）|柱状图|` geom_col()`|`e_bar()`|
|-|箱线图|` geom_boxplot()`|`e_boxplot()`|
|-|点图|` geom_dotplot(binaxis = "y", stackdir = “center")`|？|
|-|提琴图|`geom_violin(scale = “area") `|？|
|双变量（两个离散型）|棋盘图|`geom_count()`|？|
|-|？|`geom_jitter()`|？|
|双变量（连续二元分布）|？|`geom_bin2d()`|？|
|-|？|`geom_density_2d()`|？|
|-|？|`geom_hex()`|？|
|三变量|轮廓图|`geom_contour()`|？|
|-|？|`geom_contour_filled()`|？|
|-|？|`geom_raeter()`|？|
|-|？|`geom_tile()`|？|
|其他|雷达图|？|`e_radar()`|
|-|热力图|？|`e_heatmap()`|
|-|关系图|？|[Graph](https://echarts4r.john-coene.com/articles/graph.html)|
|-|树图|？|`e_tree()`|
|-|矩形树图|？|`e_treemap()`|
|-|旭日图|？|`e_sunburst()`|
|-|平行坐标|？|`e_aprallel()`|
|-|桑基图|？|`e_sankey()`|
|-|漏斗图|？|`e_funnel()`|
|-|仪表盘|？|`e_gauge()`|
|-|日历图|？|`e_calendar()`|
|-|词云|？|`e_cloud()`|
|-|三维立体图|？|[3D](https://echarts4r.john-coene.com/articles/threed)|

## 1.3.坐标系（Coordinate）

ggplot2 本身适用于绘制静态图形，在坐标系种类的数量上比适用于绘制交互图形的 echarts4r 略少。整理完上一小节后，俺心里纳闷为撒没有一个`geom_pie`之类的函数用来绘制饼图呢？整理了坐标系后才明白，原来 ggplot2 的一切绘图基础都是基于坐标系，默认的直角坐标系是没法绘制饼图的，需要转换成极坐标系才能做到。

|坐标系名称|ggplot2 函数|echarts4r 函数|
|:--------:|:--------:|:--------:|
|直角坐标系|`coord_cartesian()`|`e_grid()`|
|(固定xy轴比例)|`coord_fixed()`|？|
|(交换xy轴)|`ggplot(,aes(y=))`/`coord_flip()`|`e_flip_coords()`|
|(缩放xy轴)|`coord_trans()`|？|
|极坐标系|`coord_polar()`|`e_polar()`|
|(角度轴)|`coord_polar(theta = "x")`|`e_angle_axis()`|
|(径向轴)|`coord_polar(theta = "y")`|`e_radius_axis()`|
|地理坐标系|`coord_map()`|`e_map()`|
|单轴坐标系|？|`e_single_axis()`|
|日历坐标系|？|`e_calendar()`|
|平行坐标系|？|`e_parallel()`|

# 二、柱状图

绘图数据选用 ggplot2 包自带的 diamonds 数据集，一共有53940条数据，10个变量。

+ price：石头价格，单位是美元，范围是326–18823。

+ carat：石头重量，范围是0.2–5.01。

+ cut：切割质量，有序变量，分五个等级（Fair, Good, Very Good, Premium, Ideal）。

+ color：石头颜色，有序变量，也分多个等级，D (最好) - J (最差)。

+ clarity：石头匀净度，有序变量（I1 (最差), SI2, SI1, VS2, VS1, VVS2, VVS1, IF (最好)）。

+ x：石头长度，单位是毫米，范围是0–10.74。

+ y：石头宽度，单位是毫米，范围是0–58.9。

+ z：石头高度，单位是毫米，范围是0–31.8。

+ depth：衡量石头的一个指标，计算公式是 `z / mean(x, y) = 2 * z / (x + y)`，范围是43–79。

+ table：衡量石头的一个指标，范围是43–95。

使用 echarts4r 绘图时，要求数据是已经整理好的。diamonds 数据集本身是拥有10个变量的清单数据，如果要对 cut（切割质量）各类别汇总计数后展示为柱状图，需要先对数据做一番处理。使用 ggplot2 对已经汇总处理好的数据绘制柱状图，可以用 `geom_col()`函数，或者 `geom_bar(stat = 'identity')`指定对原始数据绘图。


```r
library(ggplot2)
library(data.table)
library(echarts4r)

# data(package = "ggplot2")
# help("diamonds")
# str(diamonds)
data(diamonds)

diamonds.new <- as.data.table(diamonds)
diamonds.new1 <- diamonds.new[, by = .(cut), .(freq = .N)]

# 用 echarts4r 绘图
# diamonds.new1 |> # 指定数据集
#   e_charts(cut) |> # 指定横轴
#   e_bar(freq) # 指定纵轴

# 用 ggplot2 绘图，指定数据集、x 轴、y 轴
ggplot(data = diamonds.new1) + geom_col(mapping = aes(x = cut, y = freq))
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-1-1.png" width="672" />

```r
# 使用原始数据绘图，效果同上
# ggplot(data = diamonds.new1) + geom_bar(mapping = aes(x = cut, y = freq), stat = 'identity')
```

如果总是先处理数据再绘图，那么就浪费了 ggplot2 的强大特点，ggplot2 在数据处理环节可通过指定统计方法来完成，可以直接根据清单数据绘图，此时绘制柱状图的函数是`geom_bar()`，指定`stat = 'count'`表示对 cut 列的各项类别先汇总统计频数，然后用频数绘制柱状图。


```r
# 基础柱状图，指定 x 轴
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut), stat = 'count')

# 基础柱状图，指定 y 轴
ggplot(data = diamonds) + geom_bar(mapping = aes(y = cut), stat = 'count')
```

## 2.1.不同坐标系

+ `coord_cartesian()`：直角坐标系。

一般情况下，柱状图是默认在笛卡尔坐标系（直角坐标系）上绘图，加上 `coord_cartesian()`函数后可设置 xlim、ylim 参数来限制 x 轴、y 轴的取值范围。需要注意的是 `coord_cartesian(ylim = c(0, 25000))`等同于 `ylim(0, 25000)`。


```r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut), stat = 'count') +
  coord_cartesian(ylim = c(0, 25000))
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

+ `coord_flip()`：x、y 轴互换。

当在直角坐标系上横轴和纵轴互换时，柱状图变成条形图，可以使用 `coord_flip()`函数达到此效果，或者干脆把轴属性的映射关系由 `aes(x = cut)`换成  `aes(y = cut)`。


```r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut), stat = 'count') +
  coord_flip()
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />

+ `coord_polar()`：极坐标系。
  - theta：指定把x轴还是y轴卷起来。
  - start：起始角度。
  - direction：1表示顺时针，-1表示逆时针。


```r
# 极坐标系下，默认把 x 轴卷起来
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut), stat = 'count') +
  coord_polar(theta = "x")
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-5-1.png" width="672" />

```r
# 极坐标系下，指定把 y 轴卷起来
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut), stat = 'count') +
  coord_polar(theta = "y")
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-5-2.png" width="672" />


## 2.2.填充柱子颜色

若要填充柱子颜色，需指定 fill 参数。如果指定 x 轴变量和填充变量相同，那么会给每个柱子填上不同颜色，此时的填充颜色来源于默认主题。而如果指定 x 轴变量和填充变量相同，那么会产生分组堆叠效果，见后文第2.3小节。


```r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = cut), stat = 'count')
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-1.png" width="672" />

也可引入调色盘来填充柱子颜色，如下需要用 `scale_fill_brewer()`函数。。


```r
# 将 ggplot2 升级到3.4.2后，与吉卜力相关的配色函数被删除了
# ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = cut), stat = 'count') + scale_fill_ghibli_d(name = "MarnieMedium2")

# 查看调色盘名称 `RColorBrewer::display.brewer.all()`
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = cut), stat = 'count') + scale_fill_brewer(palette = "PiyG")
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-7-1.png" width="672" />

还可以手动指定填充的颜色，如下需要用 `scale_fill_manual()`函数。


```r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = cut), stat = 'count') +
  scale_fill_manual(values = c('black', 'black', 'red', 'black', 'black'))
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-8-1.png" width="672" />

指定 color 参数可以改变柱子边框颜色，这点令俺超级意外，此前从未想过居然还可以这么做。


```r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, color='red'), stat = 'count')
```

## 2.3.分组

当绘图时指定的 x 轴变量为离散型变量时，默认对 x 轴变量分组展示。在下面的例子中不再统计频数，而是用`after_stat(prop)`来计算每个组别占整体的比例，如果按照默认分组，会得到每个组别占每个组别的整体比例都是100%，但此时希望得到每个 x 轴变量的组别占全部数据的比例，需要设置 group 参数为任意常数，即不再按照默认分组计算比例。


```r
ggplot(data = diamonds) +
  geom_bar(mapping = aes(x = cut, y = after_stat(prop), group = 1))
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-10-1.png" width="672" />

也可以直接指定分组变量，指定不同的分组变量将会得到不同的输出结果。


```r
d <- ggplot(diamonds, aes(x = cut, y = clarity))
d + geom_count(aes(size = after_stat(prop)))

d + geom_count(aes(size = after_stat(prop), group = 1)) +
scale_size_area(max_size = 10)

d + geom_count(aes(size = after_stat(prop), group = cut)) +
scale_size_area(max_size = 10)

d + geom_count(aes(size = after_stat(prop), group = clarity)) +
scale_size_area(max_size = 10)
```

## 2.4.不同堆叠方式

在需要将不同组别或类别数据堆叠起来之前，需要先依据不同形式的数据了解不同分组方式。

+ 其一，可直接指定数据集中的分组变量，那么设置 `aes(fill = 分组变量)`或者 `aes(group = 分组变量)`都可以达到分组效果。
+ 其二，需要将不同变量分组堆叠，那么如`geom_col(y = 变量1) + geom_col(y = 变量2)`逐个将变量引入，再进行分组。

### 2.4.1.调整位置的堆叠

当数据类似于下面这种形式，即 cut 列作为 x 轴，依据 clarity 列将 x 轴的数据进一步分组展示，那么可以通过设置 position 参数来调整不同类别柱子的堆叠方式。

|cut|clarity|count|
|:----:|:----:|:----:|
|Good|VS1|10|
|Good|VS2|20|
|Fair|VS1|30|
|Fair|VS2|40|

+ `position = 'stack'`：按统计量堆叠，不同组别的数据堆叠在一个柱子上。


```r
ggplot(data = diamonds) + geom_bar(
  mapping = aes(x = cut, fill = clarity),
  position = 'stack',
  stat = 'count') 
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-12-1.png" width="672" />

+ `position = 'fill'`：按比例堆叠，不同组别的数据堆叠在一个柱子上。


```r
ggplot(data = diamonds) + geom_bar(
  mapping = aes(x = cut, fill = clarity),
  position = 'fill',
  stat = 'count')
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-13-1.png" width="672" />

+ `position = 'dodge'`：按统计量堆叠，不同组别的数据堆叠到不同的柱子上。


```r
ggplot(data = diamonds) + geom_bar(
  mapping = aes(x = cut, fill = clarity),
  position = 'dodge',
  stat = 'count') 
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-14-1.png" width="672" />

### 2.4.2.设置不同变量的柱子错开

当数据类似于下面这种，即 name 列作为 x 轴，goal 列和 achieve 列都作为 y 轴变量。

|name|goal|achieve|
|:----:|:----:|:----:|
|1|1500|3000|
|2|1000|5000|
|3|3500|2000|

+ `width`：调整两列柱子宽度使其不一致，这样代表不同变量的柱子虽然堆叠但不互相覆盖。


```r
data <- data.frame(
  name = letters[1:6],
  goal = c(1500, 1000, 3500, 2000, 5000, 4000),
  achieve = c(3000, 5000, 2000, 3000, 3000, 2000))

ggplot(data, mapping = aes(x = name)) +
  geom_col(mapping = aes(y = goal, fill = '目标'), width = 0.6) +
  geom_col(mapping = aes(y = achieve, fill = '达成'), width = 0.4)
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-15-1.png" width="672" />

+ `just`：调整柱子的中心相对坐标轴刻度中心的位置，以及柱子宽度，使两个柱子错开。此参数默认取值0.5，设置0或1分别表示相对坐标轴刻度中心的左边或右边。


```r
ggplot(data, mapping = aes(x = name)) +
  geom_col(
    mapping = aes(y = goal, fill = '目标'),
    just = -0.1,
    width = 0.3) +
  geom_col(
    mapping = aes(y = achieve, fill = '达成'),
    just = 1.1,
    width = 0.3)
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-16-1.png" width="672" />

## 2.5.双 y 轴

在下面的例子中，用于绘图的数据如下所示，次 y 轴需要展示的 y2 列比主 y 轴需要展示的 y1 列在数量级上相差几千倍。

|cut|y1|y2|
|:------:|:------:|:------:|
|Ideal|0.54|1810.0|
|Premium|0.86|3185.0|
|Good|0.82|3050.5|

假如用此数据绘图折线、柱状混合图形，以 y1列数据为主轴，y2列的数据为次轴，先要将 y2列的数据缩小到与 y1列同一范围内，然后在 y 轴的刻度变换函数中设定`sec.axis = sec_axis()`将缩小后的 y2 轴再放大，才能还原。如此操作得到的双 y 轴图形，本质上还是在一个直角坐标系上绘制相对同一个 y 轴变化的图形。


```r
diamonds.new2 <-
  diamonds.new[, by = .(cut), .(y1 = median(carat), y2 = median(price))]

coeff <- max(diamonds.new2$y2) / max(diamonds.new2$y1)

ggplot(data = diamonds.new2, mapping = aes(x = cut)) +
  geom_bar(
    mapping = aes(y = y1, fill = '柱状图'),
    stat = 'identity',
    position = 'dodge') +
  geom_line(mapping = aes(
    y = y2 / coeff,
    # 将次 y 轴的数据缩小
    fill = '折线图',
    linewidth = 1),
  group = 1) +
  scale_y_continuous(name = "主y轴",
                     # 将次 y 轴的坐标轴范围放大，还原
                     sec.axis = sec_axis( ~ . * coeff, name = "次y轴"))
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-17-1.png" width="672" />

## 2.6.分面

分面是指将指定变量按照每个变量类别单独绘制一个图形，再按指定方式排列。尽管分开展示，但所参照的坐标系默认为同一个。实现分面的函数有 `facet_wrap()`和 `facet_grid()`，设定用于分类的变量应是离散型。


```r
p <- ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut), stat = 'count')

# 按指定列数排列
p + facet_wrap(vars(clarity), ncol = 4)
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-18-1.png" width="672" />


```r
# 按指定行数排列
p + facet_wrap(vars(clarity), nrow = 4)

# 按多个指定变量的类别组合排列，由于组合后图数量增加多倍，慎用
p + facet_wrap(vars(clarity, color), ncol = 4)

# 按指定变量的类别排成一列
p + facet_grid(cols = vars(clarity))

# 按指定变量的类别排成一行
p + facet_grid(rows = vars(color))

# 按指定变量的类别排成行列组合
p + facet_grid(cols = vars(clarity), rows = vars(color))
```

## 2.7.文本标签

在 ggplot2 中修改各类文本标签有许多函数可以做到。

+ 其一，使用专门的标签类函数进行修改，比如 `labs()`、`xlab()`、`ylab()`、`ggtitle()`、`geom_text()`等。
+ 其二，使用各类标度变换类函数进行修改，比如用`scale_x_FUNCTION()`、`scale_y_FUNCTION()`对应修改 x、y 轴，用 `scale_fill_FUNCTION()`、`scale_color_FUNCTION()`等修改图例。

### 2.7.1.标题

使用 `labs()`函数来同时设置标题、坐标轴标题、图例标题等的文字内容，各项位置都默认固定。需要注意的是如果在 `aes()`中设定了 fill 参数，那么 `labs()` 函数中设定图例标题就用 fill 参数，同样如果在`aes()`中设定了 color 参数，那么 `labs()` 函数中设定图例标题就用 color 参数。


```r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = cut), stat = 'count') +
  labs(
    title = '图形主标题',
    subtitle = '图形副标题',
    caption = '图形备注',
    tag = '不知道干撒用的标签',
    x = 'x 轴标题',
    y = 'y 轴标题',
    fill = '图例标题')
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-20-1.png" width="672" />

可以使用 `ggtitle()` 函数来设置主标题，使用 `xlab()` 和 `ylab()` 函数来设置 x 轴和 y 轴的轴标题。


```r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = cut), stat = 'count') +
  ggtitle('主标题', subtitle = '副标题') + xlab('x 轴标题') + ylab('y 轴标题')
```

还可以使用 `sclae_x_FUNCTION` 修改 x 轴标题，案例中 x 轴变量为离散型，可以用 `scale_x_discrete`。使用 `scale_y_FUNCTION` 修改 y 轴标题，案例中 y 轴变量为连续型，可以用 `scale_y_continuous`。


```r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = cut), stat = 'count') +
  scale_x_discrete(name = 'x 轴标题') +
  scale_y_continuous(name = 'y 轴标题')
```

### 2.7.2.图例

使用图形属性的统计变换函数来修改图例标题、图例标签。需要注意的是，如果`aes()`中设定了 fill 参数，那么应该用 `scale_fill_FUNCTION`，比如以下案例中 fill 参数填入的是一个离散型变量，那么可以使用 `scale_fill_discrete()`或者 `scale_fill_manual()`。如果图例中的类别不是在 `aes()`中由 fill 参数设定，而是单个变量逐个引入，那么修改图例标签的方法参考第2.4.2小节。


```r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = cut), stat = 'count') +
  scale_fill_discrete(
    name = '图例标题',
    labels = c('一般', '好', '非常好', '非常高级', '非常理想'))
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-23-1.png" width="672" />


```r
# 图例标题、图例标签的修改效果同上
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = cut), stat = 'count') +
  scale_fill_manual(
    values = c('#1D271CFF', '#274637FF', '#2C715FFF', '#44A57CFF', '#819A7AFF'), 
    name = '图例标题',
    labels = c('一般', '好', '非常好', '非常高级', '非常理想'))
```

## 2.8.注释

### 2.8.1.添加数据标签

使用 `geom_text()` 或者 `geom_label()` 函数可以在图形上添加数据标签，前者仅在图形上添加文本标签，后者在文本标签基础上还添加了矩形框便于分辨标签内容。如果是用 echarts4r 绘图时需要添加数据标签，那么用 `e_labels(show = TRUE)`打开展示数据标签的开关即可。但是在 ggplot2 中添加数据标签相当于在图形基础上再加一个图层，`geom_text()` 或者 `geom_label()` 都是属于`GEOM_FUNCTION`函数，即用于绘制几何图形对象的函数。

在本文第2.4.2小节，由于一共需要绘制3个图层，一个 `ggplot()`图层，两个 `GEOM_FUNCTION()`图层，为使代码简洁将 `GEOM_FUNCTION()`中映射 x 轴变量的代码挪到了 `ggplot()`里面。这样做的基本逻辑是，`ggplot()`图层里面的映射属于全局映射，而`GEOM_FUNCTION()`图层里面的映射属于局部映射，但`GEOM_FUNCTION()`图层的映射优先级更高且设定内容只对本图层起作用，因而可以将多个 `GEOM_FUNCTION()`图层里相同的映射内容挪到 `ggplot()`图层中，避免了在每个 `GEOM_FUNCTION()`图层都重复设定。

基于此，如下有（1）（2）（3）（4）（5）组代码。第（1）（2）组代码只有两个图层，不管 `mapping = aes(x = cut)`是放在 `ggplot()`还是 `geom_bar()`结果都一样。第（3）（4）（5）组都有三个图层，第（3）组代码中 `mapping = aes(x = cut)`放在 `ggplot()`，`geom_bar()`和 `geom_text()`均可引用全局映射，代码正常执行；第（5）组代码中 `geom_bar()`和 `geom_text()`分别单独设定了对 x 轴的映射，代码也可正常执行；只有第（4）组代码执行时会报错，因为没有可引用的全局映射，`geom_bar()`中对 x 轴映射的设定仅对本图层起作用，`geom_text()`缺少对 x 轴映射的设定。


```r
# （1）正常执行
ggplot(diamonds, mapping = aes(x = cut)) + geom_bar()

# （2）正常执行
ggplot(diamonds) + geom_bar(mapping = aes(x = cut))

# （3）正常执行
ggplot(diamonds, mapping = aes(x = cut)) +
  geom_bar() +
  geom_text(
    mapping = aes(label = after_stat(count)),
    stat = "count",
    vjust = -0.5)

# （4）报错
ggplot(diamonds) +
  geom_bar(mapping = aes(x = cut)) +
  geom_text(
    mapping = aes(label = after_stat(count)),
    stat = "count",
    vjust = -0.5)

# （5）正常执行
ggplot(diamonds) +
  geom_bar(mapping = aes(x = cut)) +
  geom_text(
    mapping = aes(x = cut, label = after_stat(count)),
    stat = "count",
    vjust = -0.5)
```

在 `geom_text()`函数中，一共有 x、y、label、alpha、angle、colour、family、fontface、group、hjust、lineheight、size、vjust 等14种图形属性可以设置，多数在第1.1小节中有介绍。其中 label 参数可填入自定义的数据、字符串、或者统计变换后的数据。


```r
ggplot(data = diamonds,
       mapping = aes(
         x = cut,
         y = after_stat(prop),
         group = color,
         fill = color
       )) +
  geom_bar(position = position_dodge(0.9)) +
  geom_text(
    mapping = aes(
      label = scales::percent(round(after_stat(prop), digits = 2)), 
      angle = -90, # 调整数据标签的旋转角度
      vjust = 0.5,
      hjust = 0.5
    ),
    stat = "count",
    position = position_dodge(0.9))
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-26-1.png" width="672" />

### 2.8.2.添加标注

在 echarts4r 中往图形上添加标注的函数分别是，标注点（`e_mark_point()`）、标注线（`e_mark_line()`）、标注区域（`e_mark_area`）。在 ggplot2 中也可实现类似的功能。

+ 标注点，使用 `geom_segment()`函数增加一个绘制箭头的图层。


```r
ggplot(diamonds, mapping = aes(x = table, y = price, shape = cut),position = 'jitter') +
  geom_point() +
  geom_segment(
    x = 80, # 箭头起点的 x 坐标
    y = 15000, # 箭头起点的 y 坐标
    xend = 95, # 箭头终点的 x 坐标
    yend = 13500, # 箭头终点的 y 坐标
    linewidth = 1, # 箭头线宽
    color = 'red', # 箭头颜色
    arrow = arrow(length = unit(0.3, "inches"))
  )
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-27-1.png" width="672" />


+ 添加标注线，使用 `geom_hline()`标注一条水平的线，使用 `geom_vline()`标注一条垂直的线。


```r
ggplot(diamonds, mapping = aes(x = cut)) +
  geom_bar() +
  geom_hline(yintercept = 10000, color = 'red') +
  geom_vline(xintercept = 1, color = 'green')
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-28-1.png" width="672" />

+ 添加标注区域，使用 `geom_rect()`函数实现。


```r
ggplot(diamonds, mapping = aes(x = cut)) +
  geom_bar() +
  geom_rect(
    xmin = 1,
    xmax = 2,
    ymin = 10000,
    ymax = 15000,
    fill = 'green') 
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-29-1.png" width="672" />

+ 更灵活的标注，使用`annotate()`函数可以增加一个标注点 `geom = "point"`、线（曲线 `geom = "curve"`、箭头 `geom = "segment"`）、矩形 `geom = "rect"`、文本 `geom = "text"`的图层，多个 `annotate()`图层可以叠加，但不能与 `geom_hline()`、`geom_vline()`共用。


```r
ggplot(diamonds,
       mapping = aes(x = table, y = price, shape = cut),
       position = 'jitter') +
  geom_point() +
  annotate(
    geom = "point",
    x = 95,
    y = 13500,
    color = 'red',
    size = 3) + 
  annotate(
    geom = "text",
    x = 95,
    y = 13500,
    label = '标注点',
    vjust = -1)
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-30-1.png" width="672" />

## 2.9.统计变换

ggplot2中提供了多种统计变换（statistic transformation）函数，即将原始数据转换、变形的函数。每个几何对象函数都有一个默认的统计变换，每个统计变换函数也有一个默认的几何对象，因此几何对象函数和统计变换函数有时可以互换使用。如下有（1）（2）（3）（4）组代码，由于 `stat_count()`只会计算出 count（计数）和 prop （比例），因而（1）（2）结果一样，（3）结果不一样，而（4）中 `stat_density()`可以计算出密度，于是结果一样。


```r
# （1）结果一样
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut))
ggplot(data = diamonds) + stat_count(mapping = aes(x = cut))
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut), stat = 'count')
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, y = after_stat(count)))

# （2）结果一样
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, y = after_stat(prop), group = 1))
ggplot(data = diamonds) + stat_count(mapping = aes(x = cut, y = after_stat(prop), group = 1))

# （3）结果不一样
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut), stat = 'density')
ggplot(data = diamonds) + stat_count(mapping = aes(x = cut), stat = 'density')

# （4）结果一样
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut), stat = 'density')
ggplot(data = diamonds) + stat_density(mapping = aes(x = cut))
```

除了计算频数、比例、密度，ggplot2 一共提供了20多种统计变换函数，具体得翻看速查表（ggplot2::CHEET SHEET）还有包作者写的书<https://ggplot2-book.org/layers.html#sec-stat>。


```r
ggplot(data = diamonds) + stat_summary(
  mapping = aes(x = cut, y = depth),
  fun = mean,
  fun.min = min,
  fun.max = max,
  colour = "red")
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-32-1.png" width="672" />

在数据处理方面，ggplot2 还提供一些将连续型变量离散化处理的函数.

 + `cut_interval`：使分箱后的每组数据有相同的范围。
 + `cut_number()`：等频分箱，使分箱后的每组数据有相同的数据量。
 + `cut_width()`：等宽分箱，使分箱后的数据有一样的宽度。


```r
table(cut_interval(1:100, n = 11))
table(cut_number(1:100, n = 11))
table(cut_width(1:100, width = 11))

ggplot(diamonds, aes(carat, price)) +
  geom_boxplot(aes(group = cut_width(carat, 0.25)))
```

## 2.10.标度变换

在 ggplot2 中，将变量映射为具体图形属性的过程就是标度变换，因此标度变换函数是与图形属性相对应的。在第2.2小节、第2.5小节、第2.7.2小节中已有涉及。下面以 x 轴的标度变换函数为例，在现有的9个函数中，有5个函数名称与 x 轴变量类型直接相关，还有4个是当 x 轴变量为连续型时对其做数据转换的。

|标度变换函数|x 轴变量类型|
|:------:|:----------:|
|`scale_x_continuous()`|连续型|
|`scale_x_discrete()`|离散型|
|`scale_x_date()`|日期型|
|`scale_x_datetime()`|日期时间型|
|`scale_x_time`|时分秒|

|标度变换函数|数据转换功能|
|:------:|:----------:|
|`scale_x_binned`|连续变量离散化|
|`scale_x_log10`|取对数|
|`scale_x_reverse`|翻转顺序|
|`scale_x_sqrt`|开方|
  
使用 x 轴的标度变换函数可以修改x轴的标题名称、标题位置、缩放刻度、刻度线、刻度标签、设置次坐标轴、做数据转换等。其中，在对应 x 轴变量类型的函数中设置数据转换参数 trans，跟直接使用带有数据转换功能的函数输出结果是等价的，比如下面几组代码的执行结果就是一样的。
  

```r
# 翻转 x 轴的顺序
# 添加 `scale_x_reverse()`函数
ggplot(data = diamonds) + geom_point(mapping = aes(x = carat, y = price, color = cut)) +
  scale_x_reverse()

# 在 `scale_x_continuous()`函数中设置 trans 参数
ggplot(data = diamonds) + geom_point(mapping = aes(x = carat, y = price, color = cut)) +
  scale_x_continuous(trans = 'reverse')

# 设置坐标系中 x 轴范围
ggplot(data = diamonds) + geom_point(mapping = aes(x = carat, y = price, color = cut)) +
  coord_cartesian(xlim = c(5, 0))

# 直接用 `xlim()`函数设置 x 轴范围
ggplot(data = diamonds) + geom_point(mapping = aes(x = carat, y = price, color = cut)) +
  xlim(c(5, 0))
```
  
除了 x 轴，y 轴也有类似的9个标度变换函数，函数名称形似`scale_y_*`。并且如颜色（colour/color）、填充颜色（fill）、大小（size）、形状（shape）、线型（linetype）、线宽（linewidth）、透明度（alpha）等图形属性也都有对应各个变量类型的标度变换函数，以及允许手动设置的函数。整体上看，这些标度变换函数的名称形似`scale_图形属性_变量类型`、`scale_图形属性_数据转换功能`、`scale_图形属性_manual`（手动设置）。除此以外，颜色（colour/color）、填充颜色（fill）这两个图形属性还另有一些与配色相关的标度变换函数

------

学习 ggplot2 可参考的书籍或文章有很多，如下。依个人经验，许多入门的书籍和文章要在真正入门以后才看得懂，最好懂的是 《R 数据科学》这本书里关于ggplot2的两个章节。

+ ggplot2 速查表：[ggplot2 CHEET SHEET](https://rstudio.github.io/cheatsheets/html/data-visualization.html)，还有[中文版](https://rstudio.github.io/cheatsheets/translations/chinese/data-visualization_zh.pdf)。
+ ggplot2 包的文档：<https://cran.r-project.org/web/packages/ggplot2/ggplot2.pdf>。
+ ggplot2 包的官网：<https://ggplot2.tidyverse.org/index.html>。
+ ggplot2 包的作者写的书
  - [ggplot2: Elegant Graphics for Data Analysis (3e)](https://ggplot2-book.org/)
  - 《R 数据科学》第1章 使用ggplot2进行数据可视化、第21章 使用 ggplot2进行图形化沟通
+ 湘云写的书和文章：[ggplot2 入门](https://bookdown.org/xiangyun/data-analysis-in-action/visualization-basic.html)、[ggplot2 作图经验](https://xiangyun.rbind.io/2023/02/ggplot2-tips/)、[ggplot2 食谱](https://xiangyun.rbind.io/2023/02/ggplot2-cookbook/)。

[^1]:在《R 数据科学（R for Data Science）》一书中第7页有一句话“如果你更喜欢英式英语，就像 Hadley 一样，那么可以使用 colour 代替 color ”，从这里可以看出 colour 和 color 是等价的。
