---
title: 看一看我国自杀率变化趋势
author: yuanfan
date: 2024-03-29T22:06:29+0800
slug: population3
categories:
  - R
tags:
  - R
draft: no
output:
  blogdown::html_page:
    toc: true
---

<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/jquery-sparkline/jquery.sparkline.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/jquery-sparkline/jquery.sparkline.js"></script>
<script src="{{< blogdown/postref >}}index_files/sparkline-binding/sparkline.js"></script>
<!--more-->

近两年总是看到一些年轻人自杀的新闻，去年就见过一些底层年轻人相约去景区自杀的深度报道，今年开年就又见到多起学生、年轻教师、医院规培生自杀的新闻，这些累积促使我决定找来官方公布的自杀率数据看看。本文使用的数据来源有二，其一是[2011-2022年中国卫生健康统计年鉴](http://www.nhc.gov.cn/mohwsbwstjxxzx/tjzxtjsj/tjsj_list.shtml)，其中可以找到2010-2021年的自杀率数据；其二是[世界卫生组织](https://data.who.int/zh/indicators/i/16BBF41)提供下载的2000-2019年世界各国自杀率数据。

``` r
library(ggplot2)
library(data.table)
library(readxl)
library(sparkline)
library(DT)

data <- read_xlsx('data/中国卫生统计年鉴-自杀率数据.xlsx', sheet = 1)
setDT(data)

data.who <-
  read_xlsx('data/中国卫生统计年鉴-自杀率数据.xlsx', sheet = 2)
setDT(data.who)
setnames(data.who, tolower)

spark_html <- function(...) {
  as.character(htmltools::as.tags(sparkline(..., height = 50, width = 100)))}
```

# 一

本节使用的数据来源是：中国卫生健康统计年鉴。关于此有两点细节需要说明。

1.  按城乡分，城市包括直辖市区和地级市辖区，农村包括县及县级市。这和中国人口普查年鉴里面分成城市、镇、乡村的划分方式不一样。

2.  性别年龄别死亡率，指分性别年龄别计算的死亡率。计算公式：男（女）性某年龄别死亡率＝男（女）性某年龄别死亡人数／男（女）性同年龄平均人口数。下文中死亡率的单位是1/10万人，仅提供了按城市合计、城市男性、城市女性、农村合计、农村男性、农村女性计算的自杀率数据，由于没有同一口径下城市、农村人口比例或男女人口比例，所以无法算出各年龄段的总和自杀率或男性女性自杀率。

按城乡和性别来看，从2010年到2021年我国自杀率整体呈现下降趋势。若比较自杀率高低，应是`农村-男 > 农村-女 > 城市-男 > 城市-女`，即农村自杀率高于城市，而分别在农村和城市则均为男性自杀率高于女性。

<details>
<summary>
点击查看绘图的 R 代码
</summary>
<pre><code>


```r
ggplot(data = data[ICD10 == '自杀' &
                     type %in% c('农村-男', '农村-女', '城市-男', '城市-女'), ],
       mapping = aes(x = year,
                     y = total,
                     colour = type)) +
  geom_line(size = 1) + geom_point(size = 1.5) + theme_classic() +
  labs(
    x = '年份',
    y = '自杀率（每10万人）',
    colour = '城乡&性别',
    title = '2010至2021年全国自杀率变化趋势',
    subtitle = '数据来源：中国卫生健康统计年鉴'
  ) +
  scale_x_continuous(breaks = seq(2010, 2021, 1)) +
  ylim(c(0, 11)) +
  scale_colour_manual(
    values = c(
      "农村-男" = "#28231DFF",
      "农村-女" = "#008E90FF",
      "城市-男" = "#58A449FF",
      "城市-女" = "#CEC917FF"
    )
  )
```

</code></pre>
</details>

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

如果只是知道自杀率为多少，似乎没有一个具体概念。由于此前曾经看过2020年人口普查数据，可以结合自杀率数据来粗略计算自杀人数。取2020年的自杀率数据，绘制下图，按年龄段来看，不论城乡或性别，自杀率随着年龄增加而升高。极其明显的是，老年人自杀率极高。

已知在2020年人口普查数据中，85岁及以上男性人数为610万，其中城市、农村男性自杀率分别为24.86、70.45，那么对应自杀人数的范围为1516至4297人。同理，2020年85岁及以上女性人数为931万，其中城市、农村女性自杀率分别为17.99、41.68，那么对应自杀人数的范围为1673至3876人。

<details>
<summary>
点击查看绘图的 R 代码
</summary>
<pre><code>


```r
data2.melt <- melt(
  data[ICD10 == '自杀' &
         year == 2020 & type %in% c('城市-男', '城市-女', '农村-男', '农村-女'),],
  id.vars = c('type', 'year'),
  measure.vars = c(
    '不满1岁',
    '1-4',
    '5-9',
    '10-14',
    '15-19',
    '20-24',
    '25-29',
    '30-34',
    '35-39',
    '40-44',
    '45-49',
    '50-54',
    '55-59',
    '60-64',
    '65-69',
    '70-74',
    '75-79',
    '80-84',
    '85岁及以上'
  ),
  variable.name = 'age_group',
  value.name = 'value'
)

ggplot(data = data2.melt) +
  geom_bar(mapping = aes(x = age_group, y = value, fill = type),
           stat = 'identity')  +
  theme_classic() +
  labs(
    x = '年龄段',
    y = '自杀率（1/10万）',
    fill = '城乡&性别',
    title = '2020年全国自杀率按年龄段变化趋势',
    subtitle = '数据来源：中国卫生健康统计年鉴'
  ) +
  facet_wrap(vars(type), ncol = 2) +
  scale_x_discrete(breaks = c('不满1岁', '15-19', '45-49', '85岁及以上')) +
  scale_fill_manual(
    values = c(
      "农村-男" = "#28231DFF",
      "农村-女" = "#008E90FF",
      "城市-男" = "#58A449FF",
      "城市-女" = "#CEC917FF"
    )
  ) +
  theme(panel.spacing.x = unit(2, "lines")) # 让分面后左右两边的图之间间距调大
```

</code></pre>
</details>

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-5-1.png" width="672" />

由于老年人自杀率往往比低年龄段自杀率高出几倍甚至数十倍，因此单独拿出10-34岁低年龄段的数据来看，会更清楚看到在低年龄段存在一些小小的波峰。如下表所示，在2020年，对城市女性和农村女性来说，在15-19岁存在一个自杀率波峰；对农村男性来说，在25-29岁存在一个自杀率波峰；而对城市男性来说，在21-24岁存在一个自杀率波峰。

只知存在这样一些个小小波峰，似乎也没什么具体概念。已知2020年人口普查数据中15-19岁女性人数为3363万，该年龄段城市、农村女性自杀率分别为3.19、2.84，那么对应自杀人数的范围应为955至1072人。同样已知2020年人口普查数据中25-29岁男性人数为4816万，该年龄段城市、农村男性自杀率分别为3.09、5.77，那么对应自杀人数的范围应为1488至2778人。

<details>
<summary>
点击查看绘图的 R 代码
</summary>
<pre><code>


```r
data3 <- dcast(data2.melt,
               year + age_group ~ type,
               value.var = 'value')[age_group %in% c('10-14', '15-19', '20-24', '25-29', '30-34'), c('year', 'age_group', '农村-女', '城市-女', '农村-男', '城市-男')]

datatable(
  data3,
  rownames = FALSE,
  colnames = c('年份', '年龄段', '农村-女', '城市-女', '农村-男', '城市-男'),
  options = list(dom='t')
) |>
  formatStyle(
    columns = '农村-女',
    background = styleColorBar(c(0, 6, data3$`农村-女`), color = "#008E90FF"),
    backgroundSize = '90% 90%',
    backgroundRepeat = 'no-repeat',
    backgroundPosition = 'center',
    color = 'white'
  ) |>
  formatStyle(
    columns = '城市-女',
    background = styleColorBar(c(0, 6, data3$`城市-女`), color = "#CEC917FF"),
    backgroundSize = '90% 90%',
    backgroundRepeat = 'no-repeat',
    backgroundPosition = 'center',
    color = 'white'
  ) |>
  formatStyle(
    columns = '农村-男',
    background = styleColorBar(c(0, 6, data3$`农村-男`), color = "#28231DFF"),
    backgroundSize = '90% 90%',
    backgroundRepeat = 'no-repeat',
    backgroundPosition = 'center',
    color = 'white'
  ) |>
  formatStyle(
    columns = '城市-男',
    background = styleColorBar(c(0, 6, data3$`城市-男`), color = "#58A449FF"),
    backgroundSize = '90% 90%',
    backgroundRepeat = 'no-repeat',
    backgroundPosition = 'center',
    color = 'white'
  )
```

</code></pre>
</details>
<div class="datatables html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-1" style="width:100%;height:auto;"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"filter":"none","vertical":false,"data":[[2020,2020,2020,2020,2020],["10-14","15-19","20-24","25-29","30-34"],[1.93,2.84,2.16,2.24,2.15],[1.51,3.19,2.27,2.18,1.5],[1.52,3.69,4.83,5.77,5.13],[1.88,2.95,4.24,3.09,3.37]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th>年份<\/th>\n      <th>年龄段<\/th>\n      <th>农村-女<\/th>\n      <th>城市-女<\/th>\n      <th>农村-男<\/th>\n      <th>城市-男<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"dom":"t","columnDefs":[{"className":"dt-right","targets":[0,2,3,4,5]}],"order":[],"autoWidth":false,"orderClasses":false,"rowCallback":"function(row, data, displayNum, displayIndex, dataIndex) {\nvar value=data[2]; $(this.api().cell(row, 2).node()).css({'color':'white','background':isNaN(parseFloat(value)) || value <= 0.000000 ? '' : 'linear-gradient(90.000000deg, transparent ' + Math.max(6.000000 - value, 0)/6.000000 * 100 + '%, #008E90FF ' + Math.max(6.000000 - value, 0)/6.000000 * 100 + '%)','background-size':'90% 90%','background-repeat':'no-repeat','background-position':'center'});\nvar value=data[3]; $(this.api().cell(row, 3).node()).css({'color':'white','background':isNaN(parseFloat(value)) || value <= 0.000000 ? '' : 'linear-gradient(90.000000deg, transparent ' + Math.max(6.000000 - value, 0)/6.000000 * 100 + '%, #CEC917FF ' + Math.max(6.000000 - value, 0)/6.000000 * 100 + '%)','background-size':'90% 90%','background-repeat':'no-repeat','background-position':'center'});\nvar value=data[4]; $(this.api().cell(row, 4).node()).css({'color':'white','background':isNaN(parseFloat(value)) || value <= 0.000000 ? '' : 'linear-gradient(90.000000deg, transparent ' + Math.max(6.000000 - value, 0)/6.000000 * 100 + '%, #28231DFF ' + Math.max(6.000000 - value, 0)/6.000000 * 100 + '%)','background-size':'90% 90%','background-repeat':'no-repeat','background-position':'center'});\nvar value=data[5]; $(this.api().cell(row, 5).node()).css({'color':'white','background':isNaN(parseFloat(value)) || value <= 0.000000 ? '' : 'linear-gradient(90.000000deg, transparent ' + Math.max(6.000000 - value, 0)/6.000000 * 100 + '%, #58A449FF ' + Math.max(6.000000 - value, 0)/6.000000 * 100 + '%)','background-size':'90% 90%','background-repeat':'no-repeat','background-position':'center'});\n}"}},"evals":["options.rowCallback"],"jsHooks":[]}</script>

在整体自杀率逐年下降和自杀率随年龄增长而升高的前提下，若单独按城乡和性别看每个年龄段的自杀率变化趋势，如下表可以看到在15-19岁青少年人群中，农村和城市女性自杀率在2011-2013年曾连续三年上升，之后出现下降趋势，但近几年又重新出现上升趋势，并且上升趋势更加陡峭；城市男性自杀率在2012-2014年也曾连续三年上升，之后出现下降趋势，但同样在2018-2019年重现极为陡峭的上升趋势。对此，我的猜测是15-19岁青少年是社会重点关注对象，倘若自杀率连续3年上升，社会上会更加重视这个问题并进行自杀干预，随后自杀率会重新下降，而自杀干预的效果算是治标不治本，几年后自杀率的上升趋势会变得更陡峭。

<details>
<summary>
点击查看绘图的 R 代码
</summary>
<pre><code>


```r
dt1.melt <- melt(
  data[ICD10 == '自杀' &
         type %in% c('城市-男', '城市-女', '农村-男', '农村-女', '城市-合计', '农村-合计'), ],
  id.vars = c('type', 'year'),
  measure.vars = c(
    # '不满1岁',
    # '1-4',
    # '5-9',
    '10-14',
    '15-19',
    '20-24',
    '25-29',
    '30-34',
    '35-39',
    '40-44',
    '45-49',
    '50-54',
    '55-59',
    '60-64',
    '65-69',
    '70-74',
    '75-79',
    '80-84',
    '85岁及以上'
  ),
  variable.name = 'age_group',
  value.name = '自杀率'
)

dt1.dcast <-
  dcast(dt1.melt,
        year + age_group ~ type,
        value.var = '自杀率')

dt1 <- dt1.dcast[, .(
  '农村-女' = spark_html(
    `农村-女`,
    type = "line",
    lineColor = "#008E90FF",
    # 折线的颜色
    fillColor = FALSE # 不展示折线下的面积
  ),
  '城市-女' = spark_html(
    `城市-女`,
    type = "line",
    lineColor = "#CEC917FF",
    # 折线的颜色
    fillColor = FALSE # 不展示折线下的面积
  ),
  '农村-男' = spark_html(
    `农村-男`,
    type = "line",
    lineColor = "#28231DFF",
    # 折线的颜色
    fillColor = FALSE # 不展示折线下的面积
  ),
  '城市-男' = spark_html(
    `城市-男`,
    type = "line",
    lineColor = "#58A449FF",
    # 折线的颜色
    fillColor = FALSE # 不展示折线下的面积
  )
),  keyby = .(age_group)]

datatable(
  dt1,
  colnames = c('年份', '农村-女', '城市-女', '农村-男', '城市-男'),
  rownames = FALSE,
  escape = FALSE,
  options = list(
    pageLength = 5,
    # 每次分页重新渲染，不加这个的话只有第一页有图
    drawCallback = JS('function(s) { HTMLWidgets.staticRender(); }'),
    language = list(
      lengthMenu = '展示 _MENU_ 每页记录数',
      search = '检索：',
      zeroRecords = '什么都没有找到',
      infoEmpty = '找不到记录',
      infoFiltered = '(从 _MAX_ 条数据中筛选)',
      info = '共 _TOTAL_ 条记录，从 _START_ 到 _END_',
      paginate = list(previous = '上一页', `next` = '下一页')
    )
  )
) |> spk_add_deps()
```

</code></pre>
</details>
<div class="datatables html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-2" style="width:100%;height:auto;"></div>
<script type="application/json" data-for="htmlwidget-2">{"x":{"filter":"none","vertical":false,"data":[["10-14","15-19","20-24","25-29","30-34","35-39","40-44","45-49","50-54","55-59","60-64","65-69","70-74","75-79","80-84","85岁及以上"],["<span id=\"htmlwidget-111344876802bb542305\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-111344876802bb542305\">{\"x\":{\"values\":[0.19,0.81,0.49,1.08,0.85,0.63,0.56,0.92,0.83,1.23,1.93,1.57],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-b4756799a252a6b8865b\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-b4756799a252a6b8865b\">{\"x\":{\"values\":[2.58,1.92,2.35,2.68,2.26,2.1,2.31,2.21,1.61,2.6,2.84,3.54],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-902f7c6634779b452707\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-902f7c6634779b452707\">{\"x\":{\"values\":[3.34,3.6,3.91,3.3,2.21,2.12,1.68,1.6,1.75,2.42,2.16,2.36],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-807627ec88baa66e57c1\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-807627ec88baa66e57c1\">{\"x\":{\"values\":[4.78,4.15,4.49,4.51,4.47,3.53,3.66,3.08,2.82,2.37,2.24,2.34],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-6a4d5be29ba88724a509\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-6a4d5be29ba88724a509\">{\"x\":{\"values\":[4.81,3.39,4.07,4.94,4.95,4.25,3.76,3.34,3.24,2.46,2.15,2.35],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-6d5b51e7980546898f2c\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-6d5b51e7980546898f2c\">{\"x\":{\"values\":[6.67,5.48,4.93,4.48,4.01,3.63,3.29,3.2,2.59,2.87,2.94,2.28],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-ceb322718ac7154ab948\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-ceb322718ac7154ab948\">{\"x\":{\"values\":[6.3,7.99,7.26,5.45,4.87,4.85,4.02,3.08,2.85,2.84,2.93,2.61],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-61047bb081bbaa4cd70c\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-61047bb081bbaa4cd70c\">{\"x\":{\"values\":[6.26,8.71,8.25,5.85,5.63,5.22,5.6,4.86,4.47,4.67,3.87,3.53],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-551ac203c1bc23b35f44\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-551ac203c1bc23b35f44\">{\"x\":{\"values\":[8.6,8.97,8.32,8.96,8.63,10.39,9.93,10.31,9.35,6.37,6.12,5.64],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-66e45383687e31a36076\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-66e45383687e31a36076\">{\"x\":{\"values\":[11.52,15.52,12.1,9.77,9.18,8.27,8.02,6.85,6.46,7.58,7.45,7.73],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-1d70a9cc12fb7719be5a\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-1d70a9cc12fb7719be5a\">{\"x\":{\"values\":[16.73,16.04,14.18,13.4,13.44,13.2,13.49,12.65,12.36,9.28,10.07,9.28],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-99df1114acdb8537cd9d\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-99df1114acdb8537cd9d\">{\"x\":{\"values\":[24.81,21.47,17.83,18.59,17.52,17.77,16.19,16.54,15.51,12.29,13.72,12.4],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-ac1a7c2e1281cbeec188\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-ac1a7c2e1281cbeec188\">{\"x\":{\"values\":[37.31,28.87,23.2,24.79,26.5,26.14,20.55,19.9,18.67,19.37,19.84,17.15],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-4968b9e61bbced944171\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-4968b9e61bbced944171\">{\"x\":{\"values\":[52.3,42.39,39.79,35.27,35.53,33.81,29.66,26.51,20.74,25.97,28.09,25.45],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-74b981cfa224399ea535\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-74b981cfa224399ea535\">{\"x\":{\"values\":[79.49,60.52,43.79,48.38,46.62,40.92,36.39,33.47,29.32,28.59,33.33,28.25],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-ec32aeec1b41a299dc1f\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-ec32aeec1b41a299dc1f\">{\"x\":{\"values\":[159.7,63.76,58.72,58.92,56.19,55.71,42.39,38.3,39.08,45.08,41.68,28.95],\"options\":{\"type\":\"line\",\"lineColor\":\"#008E90FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>"],["<span id=\"htmlwidget-35fa9c327245a46d7dfa\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-35fa9c327245a46d7dfa\">{\"x\":{\"values\":[0.47,0.29,0.84,0.38,0.84,1,0.66,0.46,0.61,1.25,1.51,1.88],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-c25662a03f8e1d7c39c3\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-c25662a03f8e1d7c39c3\">{\"x\":{\"values\":[2.09,0.98,1.2,1.87,1.6,0.97,1.54,0.96,1.89,2.2,3.19,3.53],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-c43db2764b40e2c5ddf8\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-c43db2764b40e2c5ddf8\">{\"x\":{\"values\":[2.87,2.05,1.98,2.52,1.57,1.27,1.2,1.29,1.2,1.99,2.27,2.85],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-696bb0b0ed34edac4678\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-696bb0b0ed34edac4678\">{\"x\":{\"values\":[3.66,2.01,1.96,3.06,3.06,2.58,2.32,1.71,1.71,1.5,2.18,2],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-ba7c3b39ebb9f53169ee\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-ba7c3b39ebb9f53169ee\">{\"x\":{\"values\":[3.59,2.2,2.16,3.15,2.75,2.32,2.49,2.32,2.38,1.7,1.5,1.55],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-52e8e71ed087013cdb94\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-52e8e71ed087013cdb94\">{\"x\":{\"values\":[3.95,2.74,3,3.1,2.74,2.08,2,1.77,1.63,1.87,1.49,1.54],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-525f56769614b29b1d97\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-525f56769614b29b1d97\">{\"x\":{\"values\":[4.62,3.81,2.96,4.26,2.86,3.23,2.94,2.23,1.92,2.03,2.06,1.99],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-fa3536b6482095406998\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-fa3536b6482095406998\">{\"x\":{\"values\":[4.92,3.8,3.99,3.18,3.14,3.33,3.17,3,2.81,3.03,3.14,2.69],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-c91d67eef62917559910\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-c91d67eef62917559910\">{\"x\":{\"values\":[4.88,4.79,4.43,4.68,4.69,5.89,6.52,5.42,5.87,3.01,4.31,2.79],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-0b3a468d017c97cd648f\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-0b3a468d017c97cd648f\">{\"x\":{\"values\":[7.02,5.75,4.62,5.55,4.6,4.68,4.65,3.58,3.43,4.93,3.83,4.26],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-b18458ae5ba82c4b1420\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-b18458ae5ba82c4b1420\">{\"x\":{\"values\":[10.05,7.33,6.38,7.47,8.77,8.13,8.78,8.43,7.8,5.06,6.51,5.56],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-c7f3e5f37e1105ea3af7\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-c7f3e5f37e1105ea3af7\">{\"x\":{\"values\":[13.88,9.85,9.19,9.58,10.65,10.69,10.08,9.08,8.63,6.01,6.46,6.97],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-6258ded8f0790833dfea\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-6258ded8f0790833dfea\">{\"x\":{\"values\":[20.98,12.19,12.56,12.41,12.56,13.86,10.18,11.49,9.78,7.04,10.08,8.54],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-51de8696efb5e6fe479c\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-51de8696efb5e6fe479c\">{\"x\":{\"values\":[26.65,24.07,18.79,15.12,15.42,15.11,13.39,11.1,9.24,12.23,11.92,9.19],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-eb5430fd00b3b016a52b\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-eb5430fd00b3b016a52b\">{\"x\":{\"values\":[48.47,32.57,25.18,25.1,23.29,21.53,22.57,16.4,16.35,13.11,18.63,13.26],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-1985fe8f6bb9c0d0a722\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-1985fe8f6bb9c0d0a722\">{\"x\":{\"values\":[71.95,34.94,30.5,22.28,30.61,35.35,30.98,20.15,26.92,18.31,17.99,16.44],\"options\":{\"type\":\"line\",\"lineColor\":\"#CEC917FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>"],["<span id=\"htmlwidget-f104b2810d92038f04f5\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-f104b2810d92038f04f5\">{\"x\":{\"values\":[0.33,0.88,0.83,1.09,0.93,1.1,1.13,0.96,1.27,0.89,1.52,1.73],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-5865a5492e5ae8b189a6\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-5865a5492e5ae8b189a6\">{\"x\":{\"values\":[2.1,2.9,2.64,3.34,2.89,3.44,2.73,2.73,2.96,3.31,3.69,3.74],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-f6491b998e13be98672b\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-f6491b998e13be98672b\">{\"x\":{\"values\":[4.67,5.54,3.9,3.61,3.57,3.63,3.13,3.33,3.11,4.59,4.83,4.79],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-8b0b8c21225e0f29ae91\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-8b0b8c21225e0f29ae91\">{\"x\":{\"values\":[5.02,4.16,4.94,5.04,5.83,5.7,5.88,5.82,5.36,5.18,5.77,5.82],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-d606199e20cc88bcbcff\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-d606199e20cc88bcbcff\">{\"x\":{\"values\":[4.61,3.47,4.44,6.3,5.77,5.28,6.71,6.47,6.68,5.18,5.13,4.74],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-120f99fec0cc929057cb\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-120f99fec0cc929057cb\">{\"x\":{\"values\":[5.11,5.38,6.11,5.96,5.51,5.24,5.45,4.65,4.66,4.23,4.45,5.46],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-4e12cb5072e4c6163ba4\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-4e12cb5072e4c6163ba4\">{\"x\":{\"values\":[6.08,7.25,7.36,7.4,7.47,6.91,6.24,5.55,5.06,4.73,4.34,4.62],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-36732e6be21ba24283c4\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-36732e6be21ba24283c4\">{\"x\":{\"values\":[8.87,9.11,9.64,8.1,8.13,8.93,7.81,7.38,6.45,6.51,6.14,5.99],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-8405a72f649ebed5ccf6\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-8405a72f649ebed5ccf6\">{\"x\":{\"values\":[9.51,10.3,9.77,12.62,11.46,12.63,13.87,13.15,11.87,8.27,9.19,8.55],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-833659a929b2708f45f5\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-833659a929b2708f45f5\">{\"x\":{\"values\":[15.87,19.18,14.33,13.84,13.24,13.11,11.28,9.37,9.13,10.87,11.18,11.42],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-2af534eaf1c9c0533fde\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-2af534eaf1c9c0533fde\">{\"x\":{\"values\":[18.57,19.48,16.71,17.62,16.8,16.63,18.6,18.3,17.11,13.21,14.28,12.46],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-3223294b93879c25aed1\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-3223294b93879c25aed1\">{\"x\":{\"values\":[29.19,29.57,21.64,25.47,25.31,26.14,23.35,24.47,21.58,17.84,19.06,16.41],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-2cc5e309bb6143ab57dc\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-2cc5e309bb6143ab57dc\">{\"x\":{\"values\":[51.44,41.69,29.9,37.05,35.46,32.95,30.04,29.11,25.95,27.47,26.3,21.41],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-79ea71ec831293a91ca1\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-79ea71ec831293a91ca1\">{\"x\":{\"values\":[88.71,50.99,47.5,53.66,49.16,46.4,38.63,37.17,34.07,38.03,39.75,33.47],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-d6021878fb46abfc45e8\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-d6021878fb46abfc45e8\">{\"x\":{\"values\":[151.03,104.13,64.93,73.17,67.51,66.9,53.93,54.52,45.13,51.73,54.41,42.56],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-0cb394fe329b674e3dab\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-0cb394fe329b674e3dab\">{\"x\":{\"values\":[256.81,148.44,92.21,95.03,93.54,81.78,76.23,65.52,67.62,73.5,70.45,53.56],\"options\":{\"type\":\"line\",\"lineColor\":\"#28231DFF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>"],["<span id=\"htmlwidget-cbfa0a45820a35e5eb82\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-cbfa0a45820a35e5eb82\">{\"x\":{\"values\":[0.43,0.94,0.61,0.52,1.06,1.14,1.25,1.39,1.33,1.21,1.88,1.55],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-e9e897ef1c5420330780\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-e9e897ef1c5420330780\">{\"x\":{\"values\":[1.97,1.91,1.61,1.79,2.21,1.62,1.58,1.81,1.71,3.29,2.95,3.17],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-223b31739a8a7d2ee3ab\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-223b31739a8a7d2ee3ab\">{\"x\":{\"values\":[3.25,2.8,2.92,3.21,2.09,2.26,1.9,1.87,2.18,3.8,4.24,3.99],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-26c854fdc0f5d4a93819\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-26c854fdc0f5d4a93819\">{\"x\":{\"values\":[2.95,3.07,2.59,3.61,3.6,4.02,3.25,3.66,3.76,2.89,3.09,3.98],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-e660513be703543191c5\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-e660513be703543191c5\">{\"x\":{\"values\":[3.57,2.87,2.19,4.02,3.33,3.33,4.24,3.38,3.92,3.66,3.37,3.13],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-3729083c84ea52541801\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-3729083c84ea52541801\">{\"x\":{\"values\":[4.2,4.6,3.03,4.03,2.93,2.96,2.88,2.92,2.97,3.31,3.09,3.44],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-35b9c7088a5e4899c7ce\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-35b9c7088a5e4899c7ce\">{\"x\":{\"values\":[5.19,5.53,4.93,5.41,4.46,5.16,4.49,3.59,2.72,3.63,3.42,3.43],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-ab3420fceb2f85d1bcd8\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-ab3420fceb2f85d1bcd8\">{\"x\":{\"values\":[6.27,5.65,5.43,4.83,5.09,4.88,4.57,4.12,3.59,4.27,4.01,3.5],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-2d4ed2fa76ea93bfdb58\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-2d4ed2fa76ea93bfdb58\">{\"x\":{\"values\":[7.64,6.41,5.46,7.02,7.74,8.56,8.15,8.81,7.6,4.92,5.49,5.24],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-aa6061fc17bab32ac399\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-aa6061fc17bab32ac399\">{\"x\":{\"values\":[8.86,7.49,6.07,8.94,6.46,7.52,7,5.52,5.98,7.51,7.69,6.37],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-7c3f9daa5de68122d95d\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-7c3f9daa5de68122d95d\">{\"x\":{\"values\":[13.02,9.35,8.61,10.6,10.84,11.25,12.53,9.78,9.38,7.43,9.56,7.36],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-db0cd776fb49d348e616\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-db0cd776fb49d348e616\">{\"x\":{\"values\":[17.27,9.86,11.83,13.79,15.06,15.67,13.76,12.09,11.79,10.04,10.49,11.45],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-ee9dacccded4ed914687\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-ee9dacccded4ed914687\">{\"x\":{\"values\":[29.25,15.97,17.35,17.15,19.37,16.88,17.32,14.78,13.62,12.49,12.94,13.25],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-ec9ec9b5898cd486cda6\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-ec9ec9b5898cd486cda6\">{\"x\":{\"values\":[39.88,24.14,25.83,23.39,24.08,21.62,21.05,17.38,14.25,18.76,18.56,17.65],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-1a972800d0add0613ff2\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-1a972800d0add0613ff2\">{\"x\":{\"values\":[68.88,42.83,32.92,34.9,28.56,33.17,26.29,27.8,22.06,19.44,23.54,17.51],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>","<span id=\"htmlwidget-1a6fbac5b1bc156d3949\" class=\"sparkline html-widget \"><\/span>\n<script type=\"application/json\" data-for=\"htmlwidget-1a6fbac5b1bc156d3949\">{\"x\":{\"values\":[117.48,45.08,35.19,40.02,57.34,49.91,46.18,33.04,37.67,33.4,24.86,24.68],\"options\":{\"type\":\"line\",\"lineColor\":\"#58A449FF\",\"fillColor\":false,\"height\":50,\"width\":100},\"width\":100,\"height\":50},\"evals\":[],\"jsHooks\":[]}<\/script>"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th>年份<\/th>\n      <th>农村-女<\/th>\n      <th>城市-女<\/th>\n      <th>农村-男<\/th>\n      <th>城市-男<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"drawCallback":"function(s) { HTMLWidgets.staticRender(); }","language":{"lengthMenu":"展示 _MENU_ 每页记录数","search":"检索：","zeroRecords":"什么都没有找到","infoEmpty":"找不到记录","infoFiltered":"(从 _MAX_ 条数据中筛选)","info":"共 _TOTAL_ 条记录，从 _START_ 到 _END_","paginate":{"previous":"上一页","next":"下一页"}},"columnDefs":[],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":["options.drawCallback"],"jsHooks":[]}</script>

而如果连续4年及以上自杀率维持上升趋势，可能说明自杀干预的治标效果也在减弱。下面按自杀率在更近年份连续4年上升作为重现连续上升趋势，若截止2021年自杀率没有下降，则在下表中记录重现上升趋势的年份，若截止2021年自杀率有下降，则一并标记趋势重新下降的年份。由于没能拿到2022-2023年的数据，仅从下表记录的这些年份来看，不论城乡或性别，青少年自杀问题已经不可遏制地变得越来越严重了。

| 年龄段  |     农村-女      | 城市-女 | 农村-男 |     城市-男      |
|:-------:|:----------------:|:-------:|:-------:|:----------------:|
| 10-14岁 | 2016（**2021**） |  2017   |  2019   |        \-        |
| 15-19岁 |       2018       |  2017   |  2017   |        \-        |
|  20-24  |        \-        |  2018   |  2018   | 2017（**2021**） |

# 二

本节使用的数据来源是：世界卫生组织。

在上节简单看完国内官方的自杀率数据后，再看看中国的自杀率在世界范围是何水平。如下所示，按照世界卫生组织的数据来看，自2000年至2019年世界自杀率水平不断下降，中国和日本近些年自杀率也在不断下降，中国的自杀率已经下降到世界水平以下，而美国的自杀率却在不算上升。

<details>
<summary>
点击查看绘图的 R 代码
</summary>
<pre><code>


```r
data.who <- data.who[geo_name_short %in% c('World',
                                           'Japan',
                                           'China',
                                           #'Republic of Korea',
                                           'United States of America'), c('geo_name_short',
                                                                          'dim_time',
                                                                          'dim_sex',
                                                                          'dim_age',
                                                                          'value_numeric')]

data.who[dim_sex == 'Female', dim_sex := '女性']
data.who[dim_sex == 'Male', dim_sex := '男性']
data.who[dim_sex == 'Total', dim_sex := '合计']
data.who[geo_name_short == 'China', geo_name_short := '中国']
data.who[geo_name_short == 'Japan', geo_name_short := '日本']
#data.who[geo_name_short == 'Republic of Korea', geo_name_short := '韩国']
data.who[geo_name_short == 'United States of America', geo_name_short := '美国']
data.who[geo_name_short == 'World', geo_name_short := '世界']
data.who[dim_age == '15 to 19 years', dim_age := '15-19']
data.who[dim_age == '15 to 24 years', dim_age := '15-24']
data.who[dim_age == '15 to 29 years', dim_age := '15-29']
data.who[dim_age == '25 to 34 years', dim_age := '25-34']
data.who[dim_age == '30 to 49 years', dim_age := '30-49']
data.who[dim_age == '35 to 44 years', dim_age := '35-44']
data.who[dim_age == '45 to 54 years', dim_age := '45-54']
data.who[dim_age == '55 to 64 years', dim_age := '55-64']
data.who[dim_age == '65 to 74 years', dim_age := '65-74']
data.who[dim_age == '75 to 84 years', dim_age := '75-84']
data.who[dim_age == '85 plus years', dim_age := '85岁及以上']
data.who[dim_age == 'Total years', dim_age := '全年龄段']

ggplot(
  data = data.who[dim_age == '全年龄段' &
                    dim_sex == '合计', ] ,
  mapping = aes(x = dim_time, y = value_numeric, colour = geo_name_short)
) + geom_line()  +
  geom_point() +
  theme_classic() +
  labs(
    x = '年份',
    y = '自杀率（1/10万）',
    colour = '国家',
    title = '2000至2019年自杀率变化趋势',
    subtitle = '数据来源：世界卫生组织'
  )+ ylim(c(0, 30)) 
```

</code></pre>
</details>

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-11-1.png" width="672" />

再看2019年按性别和年龄段的自杀率数据，如下所示，三个国家均是男性自杀率高于女性，但整体上看中国的男性与女性之间的自杀率差距更小。

<details>
<summary>
点击查看绘图的 R 代码
</summary>
<pre><code>


```r
# 15-24 25-34 35-44 45-54 55-64 65-74 75-84 85+
# 15-19
# 15-29 30-49

data.who.age <-
  data.who[!dim_age %in% c('15-19', '15-29', '30-49','全年龄段')&dim_sex%in%c('男性','女性'), ]

data.who.age$dim_age <-
  factor(
    data.who.age$dim_age,
    levels = c(
      '15-24',
      '25-34',
      '35-44',
      '45-54',
      '55-64',
      '65-74',
      '75-84',
      '85岁及以上'
    )
  )

ggplot(
  data = data.who.age,
  mapping = aes(
    x = dim_age,
    y = value_numeric,
    group = dim_sex,
    color = dim_sex
  )
) +
  geom_line()  +
  geom_point() +
  theme_classic() +
  labs(
    x = '年龄段',
    y = '自杀率（1/10万）',
    color = '性别',
    title = '2019年各国按年龄段的自杀率变化趋势',
    subtitle = '数据来源：世界卫生组织'
  ) + 
  theme(axis.text.x = element_text(angle = 45, hjust = 1)) +
  facet_wrap(vars(geo_name_short), ncol = 3) 
```

</code></pre>
</details>

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-13-1.png" width="672" />

值得一提的是，按照中国卫生健康统计年鉴数据，在2019年85岁及以上人群中，城市男性自杀率是33.4，农村男性自杀率是73.5，那么男性自杀率最高不超过73.5，而城市女性自杀率是18.31，农村女性自杀率是45.08，那么女性自杀率最高不超过45.08。根据世界卫生组织的数据，在2019年85岁及以上人群中，中国男性自杀率是110.56，中国女性自杀率是50.18。这说明两个口径的数据是存在差异的。

# 三

在看这些自杀率数据的过程中，我也上网找了许多不同类型的材料来看，下面三个值得记录下来以后再看。

- [中国自杀率陡降的30年：农村女性自杀率下降最快](https://www.thepaper.cn/newsDetail_forward_3894683)，2019年。

- [中国青少年的自杀现状](https://www.chinacdc.cn/jkzt/mxfcrjbhsh/zs/gwzskkjyf/200509/W020130219372225041587.pdf)，费立鹏（Michael PHILLIPS），2005年9月。

- [年轻中国农村女性的自杀未遂](https://www.chinacdc.cn/jkzt/mxfcrjbhsh/zs/gwzskkjyf/200509/P0200509074269287358699026666666666666666360.pdf) ，Veronica PEARSON，费立鹏（Michael PHILLIPS），何凤生，及惠郁，2005年9月。

另有一个发现是，韩国的自杀率有点高得离谱，按世卫组织的数据看，韩国全年龄段的自杀率为28.5，单看85岁及以上人群，男性自杀率为289.3、女性自杀率为48。韩国低年龄段人群的自杀率也是中国的好几倍。
