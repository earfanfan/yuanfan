---
title: 使用 visNetwork 绘制可交互的关系网络图
author: yuanfan
date: 2026-01-14T19:52:46+0800
slug: visNetwork
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
<link href="{{< blogdown/postref >}}index_files/vis/vis-network.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/vis/vis-network.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/visNetwork-binding/visNetwork.js"></script>
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/vis/vis-network.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/vis/vis-network.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/visNetwork-binding/visNetwork.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/vis/vis-network.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/vis/vis-network.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/visNetwork-binding/visNetwork.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/vis/vis-network.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/vis/vis-network.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/visNetwork-binding/visNetwork.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/vis/vis-network.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/vis/vis-network.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/visNetwork-binding/visNetwork.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/vis/vis-network.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/vis/vis-network.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/visNetwork-binding/visNetwork.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/vis/vis-network.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/vis/vis-network.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/visNetwork-binding/visNetwork.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/vis/vis-network.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/vis/vis-network.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/visNetwork-binding/visNetwork.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/vis/vis-network.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/vis/vis-network.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/visNetwork-binding/visNetwork.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/vis/vis-network.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/vis/vis-network.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/visNetwork-binding/visNetwork.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/vis/vis-network.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/vis/vis-network.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/visNetwork-binding/visNetwork.js"></script>
<!--more-->

> 本文使用的 R 包版本分别是：visNetwork 2.1.4。

假设这里有四个节点分别名为 A、B、C、D，对应的唯一 id 分别是1、2、3、4。节点之间有两条线来连接，分别是`A->B`和`B->C`。如果把这个简单的例子看做流程图，我们可以使用 DiagrammeR 包，但这里我们将其看做关系图，使用 visNetwork 包来实现，后者的优势在于可以批量导入节点和线的数据。

visNetwork 包最重要的函数就是 `visNetwork()`，此函数必须填入的是两个数据框，即 nodes（节点数据）和 edges（线的数据）。在这个例子中，数据框的内容如下所示。

<div style="display: flex;">

<div style="width: 49%">

- nodes（节点数据）
  - id：每个节点的唯一id，不能重复。
  - label：每个节点的标签。

| id  | label |
|:---:|:-----:|
|  1  |   A   |
|  2  |   B   |
|  3  |   C   |
|  4  |   D   |

</div>

<div style="width: 2%">

</div>

<div style="width: 49%">

- edges（线的数据）
  - from：线的起点的节点id。
  - to：线的终点的节点id。
  - label：线的标签。
  - arrows：线的方向，取值有四种”to”、“from”、“middle”、“middle;to”。

| from | to  |  label  | arrows |
|:----:|:---:|:-------:|:------:|
|  1   |  2  | ‘A-\>B’ |  ‘to’  |
|  2   |  3  | ‘B-\>C’ |  ‘to’  |

</div>

</div>

</div>

``` r
library(visNetwork)

nodes <-
  data.frame(
    id = c(1:4),
    label = c('A', 'B', 'C', 'D')
  )
edges <-
  data.frame(
    from = c(1, 2),
    to = c(2, 3),
    label = c('A->B', 'B->C'),
    arrows = rep('to', 2)
  )
visNetwork(
  nodes,
  edges,
  # 图形容器的宽度
  width = '80%',
  # 图形容器的高度
  height = 400,
  # 图形容器的背景颜色 
  background = 'lightgray'
)
```

<div id="htmlwidget-1" style="width:80%;height:400px;" class="visNetwork html-widget"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"nodes":{"id":[1,2,3,4],"label":["A","B","C","D"]},"edges":{"from":[1,2],"to":[2,3],"label":["A->B","B->C"],"arrows":["to","to"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot"},"manipulation":{"enabled":false}},"groups":null,"width":"80%","height":400,"idselection":{"enabled":false},"byselection":{"enabled":false},"main":null,"submain":null,"footer":null,"background":"lightgray"},"evals":[],"jsHooks":[]}</script>

# 1.样式

一般，自定义的样式有三类，分别是图形容器、节点、线。

- 图形容器（函数`visNetwork()`）
  - 主标题（`visNetwork(..., main = NULL)`）
  - 副标题（`visNetwork(..., submain = NULL)`）
  - 脚注（`visNetwork(..., footer = NULL)`）
  - 图例（函数`visLegend()`）

对于图形容器的主标题、副标题、脚注和图例标题等四处文本，对应的写法都是如`main = list(text = '文本内容', style = 'css样式')`，其中 css 样式可以修改的有四种，即`font-family`（字体）、`font-weight`（字体粗细）、`font-size`（字体大小）、`text-align`（文字对齐，只有 left、right、center）。

另外，图例必须基于节点分组的情况下才能正常显示，所以下面的节点数据增加了一列 group 作为分组的结果。

``` r
# 增加节点分组信息
nodes$group <- c('grp1', rep('grp2', 3))

visNetwork(
  nodes,
  edges,
  width = '80%',
  height = 350,
  background = 'lightgray' ,
  main = list(text = '这是主标题',
              style = 'font-family:Georgia, Times New Roman, Times, serif;font-weight:bold;font-size:20px;text-align:center;'),
  submain = list(text = '这是副标题',
                 style = 'font-weight:bolder;font-size:20px;text-align:left;'),
  footer = list(text = '这是脚注',
                style = 'font-size:20px;text-align:right;')
) %>%
  visLegend(
    # 图例位置
    position = 'right',
    # 图标之间纵向空间
    stepY = 50,
    # 图标的列数，默认为1
    ncol = 1,
    main = list(text = '节点分组的\n图例标题',
                style = 'font-size:20px;text-align:center;')
  )
```

<div id="htmlwidget-2" style="width:80%;height:350px;" class="visNetwork html-widget"></div>
<script type="application/json" data-for="htmlwidget-2">{"x":{"nodes":{"id":[1,2,3,4],"label":["A","B","C","D"],"group":["grp1","grp2","grp2","grp2"]},"edges":{"from":[1,2],"to":[2,3],"label":["A->B","B->C"],"arrows":["to","to"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot"},"manipulation":{"enabled":false}},"groups":["grp1","grp2"],"width":"80%","height":350,"idselection":{"enabled":false},"byselection":{"enabled":false},"main":{"text":"这是主标题","style":"font-family:Georgia, Times New Roman, Times, serif;font-weight:bold;font-size:20px;text-align:center;"},"submain":{"text":"这是副标题","style":"font-weight:bolder;font-size:20px;text-align:left;"},"footer":{"text":"这是脚注","style":"font-size:20px;text-align:right;"},"background":"lightgray","legend":{"width":0.2,"useGroups":true,"position":"right","ncol":1,"stepX":100,"stepY":50,"zoom":true,"main":{"text":"节点分组的\n图例标题","style":"font-size:20px;text-align:center;"}}},"evals":[],"jsHooks":[]}</script>

 

参照官方文档，[节点的样式](https://cran.r-project.org/web/packages/visNetwork/refman/visNetwork.html#visNodes)、[线的样式](https://cran.r-project.org/web/packages/visNetwork/refman/visNetwork.html#visEdges)可配置的参数非常多。整体上讲，自定义节点或线的样式的方法有以下几种。

1.  将自定义样式的值写入 nodes、edges 这两张表中。
2.  nodes 表中增加 group （分组）的列，然后将自定义节点样式通过 `visGroups()`引入。
3.  将自定义的样式通过 `visNodes()`、`visEdges()`这两个函数引入。
4.  通过`visSetOptions()`引入。

对比这几种方法，有这样几点注意事项：其一，`visGroups()`、`visNodes()`、`visEdges()`可以分别为节点和线设定全局样式，如果要为每个节点单独设置样式需要添加到 nodes、edges 表中；其二，四种方法的优先级是 nodes、edges \>\> `visGroups()` \>\> `visNodes()`、`visEdges()` \>\> `visSetOptions()`。

``` r
# 添加节点的提示信息
nodes$title <- c( "这是 A 的提示信息", "这是 B 的提示信息", "这是 C 的提示信息", "这是 D 的提示信息" )

# 添加线的提示信息
edges$color <- c('red', '#5a8d96')
edges$title <- rep('线的悬停提示信息', 2)

visNetwork(nodes, edges, background = 'lightgray') %>%
  visNodes(title = '看能不能覆盖？', color = 'blue') %>%
  visGroups(
    # 指定节点所属分组的名称
    groupname = 'grp1',
    # 节点颜色
    color = 'red',
    # 节点大小，默认25
    size = 30,
    # 节点形状
    shape = 'diamond',
    # 节点透明度
    opacity = 0.8
  ) %>% visEdges(
    # 线的颜色
    color = '#5a8d96',
    # 线的长度
    length = 200,
    # 线的宽度
    width = 2
  )
```

<div class="visNetwork html-widget html-fill-item" id="htmlwidget-3" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-3">{"x":{"nodes":{"id":[1,2,3,4],"label":["A","B","C","D"],"group":["grp1","grp2","grp2","grp2"],"title":["这是 A 的提示信息","这是 B 的提示信息","这是 C 的提示信息","这是 D 的提示信息"]},"edges":{"from":[1,2],"to":[2,3],"label":["A->B","B->C"],"arrows":["to","to"],"color":["red","#5a8d96"],"title":["线的悬停提示信息","线的悬停提示信息"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot","title":"看能不能覆盖？","color":"blue"},"manipulation":{"enabled":false},"groups":{"useDefaultGroups":true,"grp1":{"color":"red","size":30,"shape":"diamond","opacity":0.8}},"edges":{"length":200,"width":2,"color":"#5a8d96"}},"groups":["grp1","grp2"],"width":null,"height":null,"idselection":{"enabled":false},"byselection":{"enabled":false},"main":null,"submain":null,"footer":null,"background":"lightgray"},"evals":[],"jsHooks":[]}</script>

# 2.导出

visNetwork 包将可视化图形导出的方式有以下几种。

1.  函数`visExport()`

展示的图形容器中增加一个“导出按钮”，在浏览器中打开后点击按钮可导出为静态文件，可选文件类型有 png（默认）、jpeg、pdf。

``` r
visNetwork(nodes, edges) %>% visExport(type = 'pdf',
                                       name = '导出文件名称',
                                       label = '导出按钮名称')
```

2.  函数`visSave()`

导出为指定目录下的 html 文件。

``` r
visNetwork(nodes, edges) %>% visSave(file = '/文件路径/文件名称.html', selfcontained = TRUE)
```

3.  htmlwidgets 包的函数`saveWidget()`

由于 visNetwork 本质是通过 htmlwidgets 框架来封装 vis.js，也可使用 htmlwidgets 包来导出。

``` r
visNetwork(nodes, edges) %>% htmlwidgets::saveWidget('/文件路径/文件名称.html', selfcontained = TRUE)
```

# 3.聚合

当节点数量较多时，展示全部节点数据会难以迅速找到重点，因此需要聚合节点便于分析。visNetwork 支持不同的聚合方式：其一，用于展示机器学习算法的图形结果，比如使用 `visTree()`展示 rpart 包生成的分类树或回归树，以及使用`visHclust()`展示层次聚类的结果；其二，在关系网络的基础上按不同目的将节点聚合后展示，然后用鼠标单击查看具体的节点。

- 按颜色聚合

指定按照一种或多种颜色聚合。

``` r
nodes$color <- c(rep('red', 2), rep('blue', 2))
visNetwork(nodes, edges) %>%
  visClusteringByColor(colors = c("red", "blue")) 
```

<div class="visNetwork html-widget html-fill-item" id="htmlwidget-4" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-4">{"x":{"nodes":{"id":[1,2,3,4],"label":["A","B","C","D"],"group":["grp1","grp2","grp2","grp2"],"title":["这是 A 的提示信息","这是 B 的提示信息","这是 C 的提示信息","这是 D 的提示信息"],"color":["red","red","blue","blue"]},"edges":{"from":[1,2],"to":[2,3],"label":["A->B","B->C"],"arrows":["to","to"],"color":["red","#5a8d96"],"title":["线的悬停提示信息","线的悬停提示信息"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot"},"manipulation":{"enabled":false}},"groups":["grp1","grp2"],"width":null,"height":null,"idselection":{"enabled":false},"byselection":{"enabled":false},"main":null,"submain":null,"footer":null,"background":"rgba(0, 0, 0, 0)","clusteringColor":{"colors":["red","blue"],"label":"Cluster on color : ","shape":["database","database"],"force":[false,false]}},"evals":[],"jsHooks":[]}</script>

- 按分组聚合

指定按照一个或多个分组类别聚合。

``` r
# 去掉上段代码中的颜色，改用 visLegend 默认的
nodes$color <- NULL

visNetwork(nodes, edges) %>%
  visClusteringByGroup(groups = c('grp2'))%>%
  visLegend()
```

<div class="visNetwork html-widget html-fill-item" id="htmlwidget-5" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-5">{"x":{"nodes":{"id":[1,2,3,4],"label":["A","B","C","D"],"group":["grp1","grp2","grp2","grp2"],"title":["这是 A 的提示信息","这是 B 的提示信息","这是 C 的提示信息","这是 D 的提示信息"]},"edges":{"from":[1,2],"to":[2,3],"label":["A->B","B->C"],"arrows":["to","to"],"color":["red","#5a8d96"],"title":["线的悬停提示信息","线的悬停提示信息"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot"},"manipulation":{"enabled":false}},"groups":["grp1","grp2"],"width":null,"height":null,"idselection":{"enabled":false},"byselection":{"enabled":false},"main":null,"submain":null,"footer":null,"background":"rgba(0, 0, 0, 0)","clusteringGroup":{"groups":["grp2"],"label":"Cluster on group : ","shape":"database","color":"grey","force":false,"scale_size":true},"legend":{"width":0.2,"useGroups":true,"position":"left","ncol":1,"stepX":100,"stepY":100,"zoom":true}},"evals":[],"jsHooks":[]}</script>

- 按节点聚合

指定按照一个或多个节点 id 及其**直接连接**的相邻节点聚合。

``` r
visNetwork(nodes, edges) %>%
   visClusteringByConnection(nodes = 3)
```

<div class="visNetwork html-widget html-fill-item" id="htmlwidget-6" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-6">{"x":{"nodes":{"id":[1,2,3,4],"label":["A","B","C","D"],"group":["grp1","grp2","grp2","grp2"],"title":["这是 A 的提示信息","这是 B 的提示信息","这是 C 的提示信息","这是 D 的提示信息"]},"edges":{"from":[1,2],"to":[2,3],"label":["A->B","B->C"],"arrows":["to","to"],"color":["red","#5a8d96"],"title":["线的悬停提示信息","线的悬停提示信息"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot"},"manipulation":{"enabled":false}},"groups":["grp1","grp2"],"width":null,"height":null,"idselection":{"enabled":false},"byselection":{"enabled":false},"main":null,"submain":null,"footer":null,"background":"rgba(0, 0, 0, 0)","clusteringConnection":{"nodes":[3]}},"evals":[],"jsHooks":[]}</script>

- 按线的数量聚合

指定`size = n`，等同于`size >= n`，即大于等于 n 条线能互相连通的节点都聚合起来展示。

``` r
visNetwork(nodes, edges) %>%
   visClusteringByHubsize(size = 2)
```

<div class="visNetwork html-widget html-fill-item" id="htmlwidget-7" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-7">{"x":{"nodes":{"id":[1,2,3,4],"label":["A","B","C","D"],"group":["grp1","grp2","grp2","grp2"],"title":["这是 A 的提示信息","这是 B 的提示信息","这是 C 的提示信息","这是 D 的提示信息"]},"edges":{"from":[1,2],"to":[2,3],"label":["A->B","B->C"],"arrows":["to","to"],"color":["red","#5a8d96"],"title":["线的悬停提示信息","线的悬停提示信息"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot"},"manipulation":{"enabled":false}},"groups":["grp1","grp2"],"width":null,"height":null,"idselection":{"enabled":false},"byselection":{"enabled":false},"main":null,"submain":null,"footer":null,"background":"rgba(0, 0, 0, 0)","clusteringHubsize":{"size":2}},"evals":[],"jsHooks":[]}</script>

- 自动聚合

在动态图形放大缩小的过程中，自动展开或聚合。clusterFactor 参数取值在0到1之间，取值为0时，无论如何缩小都不会聚合。

``` r
visNetwork(nodes, edges) %>%
 visClusteringOutliers(clusterFactor = 1)
```

<div class="visNetwork html-widget html-fill-item" id="htmlwidget-8" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-8">{"x":{"nodes":{"id":[1,2,3,4],"label":["A","B","C","D"],"group":["grp1","grp2","grp2","grp2"],"title":["这是 A 的提示信息","这是 B 的提示信息","这是 C 的提示信息","这是 D 的提示信息"]},"edges":{"from":[1,2],"to":[2,3],"label":["A->B","B->C"],"arrows":["to","to"],"color":["red","#5a8d96"],"title":["线的悬停提示信息","线的悬停提示信息"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot"},"manipulation":{"enabled":false}},"groups":["grp1","grp2"],"width":null,"height":null,"idselection":{"enabled":false},"byselection":{"enabled":false},"main":null,"submain":null,"footer":null,"background":"rgba(0, 0, 0, 0)","clusteringOutliers":{"clusterFactor":1,"stabilize":false}},"evals":[],"jsHooks":[]}</script>

# 4.布局

节点数量较多时，若是随机排列，可能会显得很乱，通过设置`visLayout()`函数中的一些参数可以改善布局结果。

- randomSeed：数值型，设定布局的随机种子，方便复现结果。
- improvedLayout：默认取值为 TRUE，当节点数量超过100时，自动聚合并进行初始布局。
- clusterThreshold：设置聚类阈值，默认150，当节点数量超过阈值时，自动聚合并进行初始布局。
- hierarchical：默认取值为 FALSE，从上到下排列。

``` r
# 从上到下
visNetwork(nodes, edges) %>%
 visLayout(hierarchical = TRUE) 
```

<div class="visNetwork html-widget html-fill-item" id="htmlwidget-9" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-9">{"x":{"nodes":{"id":[1,2,3,4],"label":["A","B","C","D"],"group":["grp1","grp2","grp2","grp2"],"title":["这是 A 的提示信息","这是 B 的提示信息","这是 C 的提示信息","这是 D 的提示信息"]},"edges":{"from":[1,2],"to":[2,3],"label":["A->B","B->C"],"arrows":["to","to"],"color":["red","#5a8d96"],"title":["线的悬停提示信息","线的悬停提示信息"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot"},"manipulation":{"enabled":false},"layout":{"hierarchical":true}},"groups":["grp1","grp2"],"width":null,"height":null,"idselection":{"enabled":false},"byselection":{"enabled":false},"main":null,"submain":null,"footer":null,"background":"rgba(0, 0, 0, 0)"},"evals":[],"jsHooks":[]}</script>

``` r
# 从左到右
# visNetwork(nodes, edges) %>%
#  visHierarchicalLayout(direction = "LR")
```

# 5.动态交互

visNetwork 包中还有一些函数可以设置动态交互的参数，比如`visPhysics()`、`visInteraction()`、`visOptions()`等，不过一般默认值就算合用，所以这几个函数只是匆匆看过。

- `visInteraction()`
  - dragNodes: 默认取 TRUE，允许拖动未固定的节点。
  - dragView: 默认取 TRUE，允许拖动整个视图。
  - hover: 默认取 FALSE，取 TRUE 时鼠标悬停节点时，启用设置的颜色。
  - selectConnectedEdges: 默认取 TRUE，允许悬停节点时高亮与节点相连的线。
  - zoomView: 默认取 TRUE，允许缩放。
  - zoomSpeed：默认取1，代表缩放的速度。
  - navigationButtons：默认取 FALSE，取 TRUE 时添加导航按钮。

下面以设置悬停颜色为例，这里需要先去掉 nodes 中的 title、group 等信息，否则`visNodes()`优先级不够高，悬停颜色会不生效。

``` r
nodes$title <- NULL
nodes$group <- NULL
# 设置节点悬停颜色
visNetwork(nodes, edges) %>%
  visNodes(color = list(hover = "green")) %>%
  visInteraction(hover = TRUE, navigationButtons = TRUE)
```

<div class="visNetwork html-widget html-fill-item" id="htmlwidget-10" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-10">{"x":{"nodes":{"id":[1,2,3,4],"label":["A","B","C","D"]},"edges":{"from":[1,2],"to":[2,3],"label":["A->B","B->C"],"arrows":["to","to"],"color":["red","#5a8d96"],"title":["线的悬停提示信息","线的悬停提示信息"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot","color":{"hover":"green"}},"manipulation":{"enabled":false},"interaction":{"hover":true,"navigationButtons":true,"zoomSpeed":1}},"groups":null,"width":null,"height":null,"idselection":{"enabled":false},"byselection":{"enabled":false},"main":null,"submain":null,"footer":null,"background":"rgba(0, 0, 0, 0)","tooltipStay":300,"tooltipStyle":"position: fixed;visibility:hidden;padding: 5px;white-space: nowrap;font-family: verdana;font-size:14px;font-color:#000000;background-color: #f5f4ed;-moz-border-radius: 3px;-webkit-border-radius: 3px;border-radius: 3px;border: 1px solid #808074;box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);"},"evals":[],"jsHooks":[]}</script>

- `visOptions()`
  - highlightNearest：取 TRUE 时，被选中的节点及相连节点高亮显示，其他节点变灰。
  - nodesIdSelection：取 TRUE 时允许按照节点 id（标签）进行筛选。

``` r
visNetwork(nodes, edges) %>%
  visOptions(highlightNearest = TRUE, nodesIdSelection = TRUE)
```

<div class="visNetwork html-widget html-fill-item" id="htmlwidget-11" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-11">{"x":{"nodes":{"id":[1,2,3,4],"label":["A","B","C","D"]},"edges":{"from":[1,2],"to":[2,3],"label":["A->B","B->C"],"arrows":["to","to"],"color":["red","#5a8d96"],"title":["线的悬停提示信息","线的悬停提示信息"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot"},"manipulation":{"enabled":false}},"groups":null,"width":null,"height":null,"idselection":{"enabled":true,"style":"width: 150px; height: 26px","useLabels":true,"main":"Select by id"},"byselection":{"enabled":false,"style":"width: 150px; height: 26px","multiple":false,"hideColor":"rgba(200,200,200,0.5)","highlight":false},"main":null,"submain":null,"footer":null,"background":"rgba(0, 0, 0, 0)","highlight":{"enabled":true,"hoverNearest":false,"degree":1,"algorithm":"all","hideColor":"rgba(200,200,200,0.5)","labelOnly":true},"collapse":{"enabled":false,"fit":false,"resetHighlight":true,"clusterOptions":null,"keepCoord":true,"labelSuffix":"(cluster)"}},"evals":[],"jsHooks":[]}</script>
