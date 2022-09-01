---
title: 用R中echarts4r包绘制柱状图的笔记
author: yuanfan
date: '2021-09-01'
slug: echarts4r-e-bar
categories:
  - R
tags:
  - R
draft: no
---

<font face="微软雅黑">两个多月前我将“抽时间把积累下来的东西捋捋、整理出来”这件事放到了我的年度目标里，考虑到模型那套东西涉及的方方面面太多了，从那开始整理的话恐怕又要食言而肥了，于是先整理一些最简单的东西。

<!--more-->

图形展示中有三种最基础的形式，俗称“折柱饼”，一般用折线图看趋势、用饼图看占比、用柱状图对比大小。其中竖着放的柱状横过来就变成了条形，因此这篇笔记中既包含竖着的柱状图也包括横着的条形图。

R里面的内置数据集我不熟悉，随便翻了翻也没找到合适的面板数据，在正式画图之前先编造一份基础数据：

```{r}
data<-data.frame(
  area=c('area1','area2','area3','area4','area5','area6','area7','area8'),
  value1=sample(1:10,8),
  value2=sample(1:10,8),
  value3=sample(1:10,8),
  value4=sample(1:10,8),
  value5=sample(50:100,8)
)
```

## 1.基础定义

**echarts4r包的所有参数设置细节都可以去[官网](https://echarts4r.john-coene.com/reference/)查找，有必要的话还可以去[echarts的官网](https://echarts.apache.org/en/option.html)查找更细致的参数设定。**

**若使用4.1.0及以上版本的R，则所有`%>%`需要换成`|>`。**

先用基础数据画一个最普通的柱状图:

```{r}
library(echarts4r)

data%>%
  e_charts(area)%>%  #横轴
  e_bar(value1)  #纵轴，e_bar代表柱状图
```
![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-1.png)

### 1.1.坐标轴(axis)

echarts4r包中的函数通常都有默认参数，横轴通常默认间隔1来展示具体标签,若要调整横轴需要设置`e_x_axis()`，若要调整纵轴的间隔需要设置`e_y_axis()`。

```{r}
data %>%
  e_charts(area) %>%  
  e_bar(value1) %>%  
  e_x_axis(axisLabel = list(interval = 0), name = "X轴") %>%
  #将横轴标签间隔调整为0，这样每个坐标轴标签都会显示出来
  #有时候坐标轴标签太长，也可以设置旋转角度如axisLabel = list(interval = 0, rotate = 30)
  e_y_axis(
    min = 0,  #Y轴最小值
    max = 10,  #Y轴最大值
    interval = 5,  #Y轴间隔
    name = "Y轴"  #增加Y轴的名字
  )
```

|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-1.png)|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-2.png)|
|:-:|:-:|

### 1.2.标签(label)&提示(tooltip)

提示工具就是鼠标放到柱子上时会显示出来的内容。

```{r}
data %>%
  e_charts(area) %>%
  e_bar(value1, name = "数据项的名字") %>%
  e_labels(fontSize = 9,  #设置数据标签的字体大小
           position = "top") %>%  #设置数据标签的位置如top,buttom,inside
  e_tooltip()  #可设置参数trigger = "item"和trigger = "axis"，提示内容一样但格式不一样
```

|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-1.png)|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-3.png)|
|:-:|:-:|

### 1.3.标记(mark)

echarts4r包提供三种标记方式：标记点(`e_mark_point`)、标记线(`e_mark_line`)、标记区域(`e_mark_area`)。

```{r}
#可以这样写
data %>%
  e_charts(area) %>%
  e_bar(value1, name = "数据项的名字") %>%
  e_mark_point("数据项的名字", data = list(type = "min")) %>%  #标记最小值
  e_mark_point("数据项的名字", data = list(type = "max")) %>%  #标记最大值
  e_mark_line("数据项的名字", data = list(type = "average")) %>%  #标记平均值
  e_mark_area(
    serie = "数据项的名字",
    data = list(list(xAxis = "min", yAxis = 8),
                list(xAxis = "max", yAxis = 10)),
    itemStyle = list(color = "lightblue")
  )  #标记区域

#也可以这样写
max <- list(name = "Max",
            type = "max")

min <- list(name = "Min",
            type = "min")

avg <- list(type = "average",
            name = "AVG")

data %>%
  e_charts(area) %>%
  e_bar(value1) %>%
  e_mark_point("value1", data = min) %>%
  e_mark_point("value1", data = max) %>%
  e_mark_line("value1", data = avg)
```
如果要同时对多个数据项标记，可以写`e_mark_point(c("value1","value2"), data = min)`，前提是前面也有`e_bar(value2)`

|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-1.png)|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-4.png)|
|:-:|:-:|

### 1.4.图例(legend)&标题(title)

当需要显示许多数据项时，需要对图例做详细设置，以后遇到复杂情况时再把这部分展开细写。

```{r}
data %>%
  e_charts(area) %>%
  e_bar(value1) %>%
  e_legend(show = FALSE) #不显示图例

data %>%
  e_charts(area) %>%
  e_bar(value1) %>%
  e_legend(right = TRUE)%>% #左(left)、中(center)、右(right);上(top)、中(middle)、下(buttom)
  e_title('主标题','副标题')
```

|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-1.png)|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-6.png)|
|:-:|:-:|

## 2.堆叠(stack)

当需要展示的数据项不止一个时，可以根据业务需要进行堆叠：

```{r}
#四个数据项并排展示
data %>%
  e_charts(area) %>%
  e_bar(value1) %>%
  e_bar(value2) %>%
  e_bar(value3) %>%
  e_bar(value4) %>%
  e_x_axis(axisLabel = list(interval = 0))

#四个数据项全堆到一起
data %>%
  e_charts(area) %>%
  e_bar(value1, stack = "grp") %>%
  e_bar(value2, stack = "grp") %>%
  e_bar(value3, stack = "grp") %>%
  e_bar(value4, stack = "grp") %>%
  e_x_axis(axisLabel = list(interval = 0))

#四个数据项分成两堆
data %>%
  e_charts(area) %>%
  e_bar(value1, stack = "grp1") %>%
  e_bar(value2, stack = "grp1") %>%
  e_bar(value3, stack = "grp2") %>%
  e_bar(value4, stack = "grp2") %>%
  e_x_axis(axisLabel = list(interval = 0))
```
|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-7.png)|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-8.png)|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-9.png)|
|:-:|:-:|:-:|

全堆到一起的情况，也可以展示各个数据项的占比：

```{r}
#计算占比
data.1 <-
  data %>% dplyr::mutate(
    value1_rate = round(value1 / (value1 + value2 + value3 + value4), 2),
    value2_rate = round(value2 / (value1 + value2 + value3 + value4), 2),
    value3_rate = round(value3 / (value1 + value2 + value3 + value4), 2),
    value4_rate = round(value4 / (value1 + value2 + value3 + value4), 2)
  )

data.1 %>% 
  e_chart(area) %>% 
  e_bar(value1_rate, stack="grp") %>%
  e_bar(value2_rate, stack="grp") %>%
  e_bar(value3_rate, stack="grp") %>%
  e_bar(value4_rate, stack="grp") %>%
  e_x_axis(axisLabel = list(interval = 0))%>%  #设置横轴间隔为0
  e_y_axis(max=1,formatter = e_axis_formatter("percent", digits = 0))%>%  #设置Y轴最大值为100%
  e_legend(type='scroll')  #数据项很多时，可以设置图例滚动展示
```

![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-10.png)

## 3.双轴

同时需要展示多个数据项但是数据的量级存在差异时，可以考虑用两个Y轴来展示：

```{r}
#下面是我瞎碰乱试出来的，备注的文字仅仅是我的猜想
data %>%
  e_chart(area) %>%
  e_line(value1) %>%  #没有y_index参数时默认左侧Y轴为主轴
  e_bar(value5, y_index = 1) %>%  #设置了y_index=1时，默认用的是右侧Y轴即副轴
  e_y_axis(
    min = 0,
    max = 10,
    interval = 5,
    name = "左侧Y轴"  
  ) %>%
  e_y_axis(
    index = 1, #对副轴进行设置
    min = 0,
    max = 100,
    interval = 20,
    name = "右侧Y轴"
  )
```

![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-11.png)

## 4.时间轴(timeline)

虽然名字是时间轴，但是也可以用于将数据分组后展示：

```{r}
data.2 <- data.frame(
  type = c('type1','type1','type1','type1','type2','type2','type2','type2'),
  area = c('area1','area2','area3','area4','area1','area2','area3','area4'),
  value1 = sample(1:10, 8)
)

data.2 %>%
  group_by(type) %>%  #分组
  e_charts(area, timeline = TRUE) %>%  #横轴
  e_bar(value1) %>%
  e_timeline_opts(axis_type = "category",
                  top = 5)  #通常时间轴默认放在图形下方，也可以设定放到图形上方
```
|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-12.png)|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-17.png)|
|:-:|:-:|

## 5.转置

若要将图形旋转90度后横轴与纵轴互换，即行列互换，亦即转置，最好是按数值排序后展示，或者按照数据项本身的含义排序后展示如人口金字塔图：

```{r}
#倒序排序
data.3 <- data[order(data$value1, decreasing = FALSE), ] 

data.3 %>%
  e_chart(area) %>%
  e_bar(value1) %>%
  e_y_axis(show = FALSE) %>%
  e_legend(show = FALSE) %>%
  e_flip_coords() %>%
  e_labels(position = "right") 
```


```{r}
#仿人口结构的金字塔图
data.4 <- data.frame(
  level = c('0-10岁','11-20岁','21-30岁','31-40岁','41-50岁','51-60岁','61-70岁','71-80岁','80岁以上'),
  value1 = sample(1:10, 9),
  value2 = sample(1:10, 9),
  value3 = sample(1:10, 9),
  value4 = sample(1:10, 9)
)

data.4%>%
  dplyr::mutate(value3=-value3,value4=-value4)%>%
  e_chart(level)%>%
  e_bar(value1,stack="grp")%>%
  e_bar(value2,stack="grp")%>%
  e_bar(value3,stack="grp")%>%
  e_bar(value4,stack="grp")%>%
  e_y_axis(show = FALSE) %>%
  e_legend(show = FALSE) %>%
  e_flip_coords()
```
|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-13.png)|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-14.png)|
|:-:|:-:|

## 6.极坐标(polar)

echarts4r包还提供了一种画在极坐标系上的条形图，相当于把普通条形图的横轴两端连成一个圆：

```{r}
data %>%
  e_charts(area) %>%  #X轴
  e_polar() %>% 
  e_angle_axis(area) %>% # angle = x
  e_radius_axis() %>% 
  e_bar(value1, coord_system = "polar") %>%
  e_scatter(value2, coord_system = "polar")
```

```{r}
data %>%
  e_charts(area) %>%
  e_polar() %>%
  e_angle_axis() %>%
  e_radius_axis(area, axisLabel = list(interval = 0)) %>%  #将x轴标签的间隔设为0
  e_bar(value1, coord_system = "polar")
```

|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-1.png)|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-15.png)|![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-16.png)|
|:-:|:-:|:-:|

## 7.速查表

当想要修改图的细节但是不知道对应的函数名字时，也可以先翻翻官方的[速查表](https://echarts.apache.org/en/cheat-sheet.html)，然后再去官方文档中搜索对应函数名称。

I.常用组件：

![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-18.png)

II.图形系列：

![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-19.png)

III.坐标系&组件：

![](https://raw.githubusercontent.com/earfanfan/yf/main/static/images/2021-8-30-20.png)
