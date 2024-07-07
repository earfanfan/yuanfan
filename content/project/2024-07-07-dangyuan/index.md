---
title: 看一看中国共产党党员组成
author: yuanfan
date: 2024-07-07T17:11:14+0800
slug: dangyuan
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

中共中央组织部网站上公开了2012年至今的[中国共产党党内统计公报](https://news.12371.cn/dzybmbdj/zzb/dntjgb/)，截止2023年底党员总数一共有9918.5万人，其中女党员共有3018.5万人，占比33.5%。


```r
library(readxl)
library(data.table)
library(ggplot2)

# 党员
data1 <- read_xlsx('data/中国共产党党内统计公报.xlsx', sheet = 1)
# 党组织
data2 <- read_xlsx('data/中国共产党党内统计公报.xlsx', sheet = 2)

setDT(data1)
setDT(data2)
```

计算出每年发展党员数和净增党员数，绘制图形如下，可以看到有两个显著不同的年份，一是2021年发展党员数远多于其他年份，二是2017年净增党员数远少于其他年份。
 
<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-1.png" width="672" />

# 性别

近十年来，发展党员中女党员的占比不超过50%。

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

# 年龄

近十年来，发展党员中35岁及以下党员的占比稳定超过80%。

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />

# 学历

近十年来，发展党员中具有大专及以上学历党员占比逐年上升，到2023年此比例超过50%。

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-5-1.png" width="672" />

# 职业

从2023年党员职业的分布来看，企事业单位、社会组织占比最高为28%，其次是农牧渔民占比为26%。而在当年发展党员中，学生占比最高为38%。

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-1.png" width="672" />

不过若是计算2023年各职业当年净增党员数，数据所呈现的表象又有所不同。

|职业类别|2023年净增党员数（万个）|占比|
|:----:|:----:|:----:|
|农牧渔民|4.3|3.7%|
|工人|-0.6|-0.5%|
|企事业单位、社会组织|48|41.9%|
|党政机关|-13.9|-12.2%|
|学生|-13|-11.4%|
|其他职业|11.9|10.4%|
|离退休人员|77.7|67.9%|

# 组织

随着国内城市化进程不断加速，各行政级别建立的党组织数量也随之变化。从2013年到2023年的这十年，乡镇级别的党组织减少了3352个，行政村级别的党组织减少了95016个，而城市街道级别的党组织增加了1677个，城市社区级别的党组织增加了28996个。


```
##                           级别     2013     2023
##  1:         党的各级地方委员会   3219.0   3199.0
##  2:             省（区、市）委     31.0     31.0
##  3:                 市（州）委    395.0    397.0
##  4:         县（市、区、旗）委   2793.0   2771.0
##  5:                   城市街道   7448.0   9125.0
##  6:                       乡镇  32972.0  29620.0
##  7:             社区（居委会）  90443.0 119437.0
##  8:                     行政村 583975.0 488959.0
##  9:     机关基层党组织（万个）     23.5     77.1
## 10: 事业单位基层党组织（万个）     50.8     99.7
```
