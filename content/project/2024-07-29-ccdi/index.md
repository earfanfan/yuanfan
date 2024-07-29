---
title: 看一看我国纪检监察机关的统计数据
author: yuanfan
date: 2024-07-29T18:35:15+0800
slug: CCDI
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
<!--more-->

据键者所知，除了美国、加拿大、瑞士、墨西哥等少数国家的居民拥有持枪的权利，世界上绝大多数国家的法律都规定由政府统一垄断暴力。政府垄断暴力固然可以达到维护国家稳定的效果，但民心、民意、民情却无法用简单的方式来控制，通常需要设定复杂可行的监督制度，使人民与国家之间存在交流的渠道或空间。政府官员行使国家权力的过程需要被监督，这是一国政府能够长期执政的根本。现代任何民主国家其国家权力的合法来源都是人民的支持，却也由于存在不同的政治制度而演变出不同的监督制度。在我国的党政体制下，施行的是人民民主专政、民主集中制度，即代表民主的权力集中、决策集中，同时监督权力也以监察制度的形式集中。自2018年废除《行政监察法》而通过《监察法》后，监察机关从政府部门中独立出来，监察委成为与国务院平行的权力机构。

按照我国宪法第二章第三十五条，“中华人民共和国公民有言论、出版、集会、结社、游行、示威的自由”，即人民拥有组建组织的结社自由。但是按照党的执政特点，本着应建尽建的原则要按单位、按行业、按区域建立党组织实现全领域覆盖[^1]，因此除了法定机构不会存在其他有组织的集体去行使监督的权力。又但是，人民群众作为单个个体对于官员贪污腐败搞特权带来的不公现象都拥有共同的感受，于是在互联网络信息高效传播的今时今日，许多普通群众无意识地组成了无组织的集体，通过舆论监督的形式行使了监督的权力。

广大人民群众无组织的利益行动，也在无形之中推动政府和其他权力机关作出信息公开。虽然键者看待集权政治下的官民博弈仍然感到如坠迷雾，不过最近正好发现中央纪委国家监委有定期公开全国纪检监察机关的监督检查审查调查报告，这便动手整理了一番，看一看统计数据。

纪检监察机关公开的统计数据从2017年开始按照固定格式每季度公开，键者只手动整理了历年的数据，其中2024年仅含上半年的数据。而2011至2016年的数据也是从各类官方报告中整理得到，只是和后面年份相比信息不太全。

# 一、接收信访举报的数量

先看历年接受信访举报的总量，从2011年至今有一个阶梯形的变化。

- 在2011至2012年，总量的水平为135、131万件次。
- 到2013年跨上一个阶梯，到了195万件次，比上一年增长了48%。
- 再到2014至2017年间，平均每年270万件次，相比2013年又跨了一个阶梯，增长了38%。
- 再到2018至2023年，平均每年345万件次，相比270万件次再跨一个阶梯，增长了27%。

<details>
<summary>
点击查看数据导入以及绘图的 R 代码
</summary>
<pre><code>


```r
library(readxl)
library(data.table)
library(ggplot2)
library(DT)

# 2011至2024上半年
data <- read_xlsx('data/纪检监察统计数据.xlsx', sheet = 1)
setDT(data)

data[, ':='(value1 = round(`接收信访举报（万件次）`, 0))] |>
  ggplot(mapping = aes(x = `统计期`, y = value1)) +
  geom_bar(stat = 'identity') +
  theme_classic() +
  geom_text(aes(label = value1), vjust = -0.5) +
  scale_fill_discrete(guide = FALSE) +
  scale_x_continuous(breaks = data$统计期, labels = data$统计期) +
  labs(title = '2011年至2024上半年接收信访举报件数', y = '万件次') 
```

</code></pre>
</details>

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-1.png" width="672" />

针对这四段阶梯增长的变化，键者通过阅读网络上公开发表的官方材料得出这样的一套逻辑。

其一，在共产党员网的一篇文章[^2]中提到“特别是党的十八大以后，针对一段时期党的领导被忽视、淡化、弱化的状况，我们党提出坚持和加强党的全面领导”，党的十八大是在2012年11月召开的，这篇文章指出十八大以前的一段时期党的领导被忽视、淡化、弱化，而十八大后加强党的全面领导，党内开始从严整治腐败问题，这个细节可以对应到信访举报件数从2012到2013大幅增长的时间点。

其二，人民网有一篇中央高层署名文章[^3]提到“政治腐败是最大的腐败，一是结成利益集团，妄图窃取党和国家权力；二是山头主义宗派主义搞非组织活动，破坏党的集中统一”，又提到“果断查处周永康、薄熙来、郭伯雄、徐才厚、孙政才、令计划严重违纪违法问题，铲除政治腐败和经济腐败相互交织的利益集团。5年来波澜壮阔的实践充分证明……”，这篇文章的发表时间是2017年11月，距离十八大召开正好过去了5年。那么可能存在一种逻辑，十八大以前的一段时期党的领导淡化弱化，党和国家内部出现了一些腐败问题极其严重的利益集团，而十八大之后的五年时间主要查处了这些贪腐势力较大的高层，打散了这些利益集团。

其三，2018年3月国家监察委员会成立，原先国务院下属的监察部不再保留，并入国家监委。行使监察权力的机关，其监察范围和权力进一步扩大，反腐败进入新的阶段。

需要说明的是，以上分析非常浅薄片面，因为我们无从得知每年接收信访举报的事件分布在哪些年份，也只是极简单地将接收信访举报件数发生大幅变化的时间点与一些反腐败的时间节点相关联，相关关系并不等于因果关系。这里还可以衍生出许多未曾深究的问题，比如为何反腐败力度大的年份接收信访举报件数更多，难道是因为反腐败力度小的年份人们不敢举报才导致举报件数少吗？还是说因为监察委独立之前，监察机关与行政机关权柄重叠，这才导致信访举报未被接收？

# 二、处置、立案、处分情况

信访举报被接收通常不代表百分百得到处置，监察机关也需分辨其真假，随后才会有处置、立案、处分的过程。下图中展示了两条随时间变化的折线，其中蓝色代表处置问题线索占接收信访举报的比例，红色折线代表立案案件占接收信访举报的比例。

<details>
<summary>
点击查看绘图的 R 代码
</summary>
<pre><code>


```r
data[, ':='(
  value1 = round(`处置问题线索（万件）` / `接收信访举报（万件次）`, 2),
  value2 = round(`立案（万件）` / `接收信访举报（万件次）`, 2)
)] |>
  ggplot(mapping = aes(x = `统计期`)) +
  geom_line(mapping = aes(y = value1, color = '处置')) +
  geom_line(mapping = aes(y = value2, color = '立案')) +
  geom_text(aes(y = value1, label = value1), nudge_y = 0.02) +
  geom_text(aes(y = value2, label = value2), nudge_y = 0.02) +
  theme_classic() +
  ylim(c(0, 0.6)) +
  scale_x_continuous(breaks = data$统计期, labels = data$统计期) +
  scale_color_manual(values = c('处置' = 'blue', '立案' = 'red')) +
  labs(title = '2011年至2024上半年--处置/立案占接收信访举报的比例',
       y = '比例',
       color = '类别')
```

</code></pre>
</details>

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />

蓝色折线的首段有一个陡峭的上升趋势，处置比例在2016年为0.29，到了2017年上升到0.46。我们知道《监察法》在2018年才立法通过，而在此之前就出现了处置比例大幅提升。根据互联网络上的公开资料[^4]，2016年10月正式开启监察法的立法工作，2016年11月在北京、山西、浙江开展监察体制改革试点，2017年10月全国各地推行监察体制改革，2017年11月监察法草案公开征求社会公众意见，此后经历多轮审议修改直至立法通过。很显然，监察法并不是最高领袖说立就立、说通过就通过的，一部法案的通过先经历过监察体制改革的试点，这才能可能可以解释2017年处置比例出现大幅提升。只不过网络上能收集到的官方信息只能体现事件的大致轮廓，具体情形并未透明公开，因此这里的“可能可以解释”只是键者的一种推理。

接着看历年立案件数与处分人数的变化情况，从2011年至2018年有很明显的增长趋势，而从2018年开始每年的立案件数是多于处分人数的。由于不了解这份数据中立案件数与处分人数这两个指标的统计口径，也不了解现实世界中监察机关如何行使职权，因此立案与处分之间的数量差异这里不做进一步探究。

<details>
<summary>
点击查看绘图的 R 代码
</summary>
<pre><code>


```r
data[, ':='(value1 = round(`立案（万件）`, 0),
            value2 = round(`处分（万人）`, 0))] |>
  ggplot(mapping = aes(x = `统计期`)) +
  geom_col(
    mapping = aes(y = value1, fill = '立案（万件）'),
    just = -0.1,
    width = 0.3) +
  geom_col(
    mapping = aes(y = value2, fill = '处分（万人）'),
    just = 1.1,
    width = 0.3) +
  geom_text(aes(y = value1, label = value1),
            nudge_y = 1.5,
            nudge_x = 0.25) +
  geom_text(aes(y = value2, label = value2),
            nudge_y = 1.5,
            nudge_x = -0.25) +
  theme_classic() +
  scale_x_continuous(breaks = data$统计期, labels = data$统计期) +
  labs(title = '2011年至2024上半年--立案件数与处分人数', 
       y = '万（件）人', fill = '类别') 
```

</code></pre>
</details>

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-1.png" width="672" />

# 三、处分干部情况

下面是2023年对政府内部不同级别官员的立案与处分情况，由于以往并未公开历年各级别政府官员的立案人员数量，若仅以2023年的数据作为观察样本的话，可以得到的结论是省部级官员的处分比例低于其他级别官员。

|         级别         | 立案  |  处分  | 比例 |
|:--------------------:|:-----:|:------:|:----:|
|        省部级        |  87   |   49   | 56%  |
|        厅局级        | 3456  |  3144  | 91%  |
|        县处级        | 2.7万 | 2.4万  | 89%  |
|        乡科级        | 8.9万 | 8.2万  | 92%  |
|       一般干部       |       | 8.5万  |      |
| 农村、企业等其他人员 |       | 41.7万 |      |

公开的统计数据中有一部分是运用“四种形态”批评教育和处理的人数，按照处罚程度由轻到重分为如下四种。

- 第一种形态：批评教育、谈话函询。
- 第二种形态：纪律轻处分、组织调整。
- 第三种形态：纪律重处分、重大职务调整。
- 第四种形态：严重违纪涉嫌违法立案审查调查。

很明显地，处罚较轻的人更多，处罚较重的人更少。如下表所示，历年按第一种形态处罚的人数占比在60%-70%之间，而第二种形态的占比在23%-31%之间，第三种形态、第四种形态的占比在3%-5%之间。

<details>
<summary>
点击查看绘制表格的 R 代码
</summary>
<pre><code>


```r
# 为了缩减代码数量，将表格中填充圆形图案的部分迁移出来
format_add <- function(...) {
  formatStyle(
    ...,
    # 'display' = 'flex', # 四个圆会竖向排列在一个单元格
    # 'display' = 'inline', # 四个圆会横向排列在一个单元格
    # 'display' = 'table-row', # 竖向的四个圆变成竖向的四个格子
    'display' = 'table-cell', # 四个圆分在四列
    'align-items' = 'center',
    'justify-content' = 'center',
    'width' = '1.875rem',
    'height' = '1.875rem',
    'border' = '0.5px solid rgb(0,0,0,0.1)',
    'border-radius' = '50%',
    'color' = '#000',
    'font-size' = '1.25rem',
    'letter-spacing' = '-1px'
  )
}
  
datatable(data = data[, ':='(
  `第一种形态` = round(`第一种形态（万人次）` / `运用四种形态批评教育和处理（万人次）`, 2),
  `第二种形态` = round(`第二种形态（万人次）` / `运用四种形态批评教育和处理（万人次）`, 2),
  `第三种形态` = round(`第三种形态（万人次）` / `运用四种形态批评教育和处理（万人次）`, 2),
  `第四种形态` = round(`第四种形态（万人次）` / `运用四种形态批评教育和处理（万人次）`, 2)
)][`统计期` >= 2017, c('统计期', '运用四种形态批评教育和处理（万人次）', '第一种形态', '第二种形态', '第三种形态', '第四种形态')],
rownames = FALSE,
options = list(dom = 't')) |>
  formatStyle(
    columns = '运用四种形态批评教育和处理（万人次）',
    background = styleColorBar(c(0, data$`运用四种形态批评教育和处理（万人次）`), 'steelblue'),
    # 填充条形
    # 填充背景的尺寸，第一个值为宽度，第二个值为高度
    backgroundSize = '100% 90%',
    backgroundRepeat = 'no-repeat',
    color = 'white'
  ) |>
  format_add(columns = '第一种形态', backgroundColor = "#FF6347") |>
  format_add(columns = '第二种形态', backgroundColor = "#ff2700") |>
  format_add(columns = c('第三种形态', '第四种形态'),
              backgroundColor = "#B50A2AFF") |>
  formatPercentage(columns = c(3:6), digits = 0)
```

</code></pre>
</details>
<div class="datatables html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-1" style="width:100%;height:auto;"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"filter":"none","vertical":false,"data":[[2024,2023,2022,2021,2020,2019,2018,2017],[87.9,171.8,183.8,212.5,195.4,184.9,173.7,131.6],[0.62,0.64,0.67,0.7,0.68,0.67,0.64,0.6],[0.31,0.29,0.26,0.23,0.25,0.25,0.28,0.31],[0.04,0.04,0.03,0.03,0.04,0.04,0.05,0.05],[0.04,0.04,0.03,0.03,0.03,0.04,0.03,0.04]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th>统计期<\/th>\n      <th>运用四种形态批评教育和处理（万人次）<\/th>\n      <th>第一种形态<\/th>\n      <th>第二种形态<\/th>\n      <th>第三种形态<\/th>\n      <th>第四种形态<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"dom":"t","columnDefs":[{"targets":2,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatPercentage(data, 0, 3, \",\", \".\", null);\n  }"},{"targets":3,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatPercentage(data, 0, 3, \",\", \".\", null);\n  }"},{"targets":4,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatPercentage(data, 0, 3, \",\", \".\", null);\n  }"},{"targets":5,"render":"function(data, type, row, meta) {\n    return type !== 'display' ? data : DTWidget.formatPercentage(data, 0, 3, \",\", \".\", null);\n  }"},{"className":"dt-right","targets":[0,1,2,3,4,5]}],"order":[],"autoWidth":false,"orderClasses":false,"rowCallback":"function(row, data, displayNum, displayIndex, dataIndex) {\nvar value=data[1]; $(this.api().cell(row, 1).node()).css({'color':'white','background':isNaN(parseFloat(value)) || value <= 0.000000 ? '' : 'linear-gradient(90.000000deg, transparent ' + Math.max(212.500000 - value, 0)/212.500000 * 100 + '%, steelblue ' + Math.max(212.500000 - value, 0)/212.500000 * 100 + '%)','background-size':'100% 90%','background-repeat':'no-repeat'});\nvar value=data[2]; $(this.api().cell(row, 2).node()).css({'color':'#000','background-color':'#FF6347','display':'table-cell','align-items':'center','justify-content':'center','width':'1.875rem','height':'1.875rem','border':'0.5px solid rgb(0,0,0,0.1)','border-radius':'50%','font-size':'1.25rem','letter-spacing':'-1px'});\nvar value=data[3]; $(this.api().cell(row, 3).node()).css({'color':'#000','background-color':'#ff2700','display':'table-cell','align-items':'center','justify-content':'center','width':'1.875rem','height':'1.875rem','border':'0.5px solid rgb(0,0,0,0.1)','border-radius':'50%','font-size':'1.25rem','letter-spacing':'-1px'});\nvar value=data[4]; $(this.api().cell(row, 4).node()).css({'color':'#000','background-color':'#B50A2AFF','display':'table-cell','align-items':'center','justify-content':'center','width':'1.875rem','height':'1.875rem','border':'0.5px solid rgb(0,0,0,0.1)','border-radius':'50%','font-size':'1.25rem','letter-spacing':'-1px'});\nvar value=data[5]; $(this.api().cell(row, 5).node()).css({'color':'#000','background-color':'#B50A2AFF','display':'table-cell','align-items':'center','justify-content':'center','width':'1.875rem','height':'1.875rem','border':'0.5px solid rgb(0,0,0,0.1)','border-radius':'50%','font-size':'1.25rem','letter-spacing':'-1px'});\n}"}},"evals":["options.columnDefs.0.render","options.columnDefs.1.render","options.columnDefs.2.render","options.columnDefs.3.render","options.rowCallback"],"jsHooks":[]}</script>

# 四、附数据说明

本文使用的数据来源于中央纪委国家监委网站、中国政府网、人民网，历年数据从以下文章中手动整理得到。

| 文章名称                                                               |                          网页链接（url）                          |
|:-----------------------------------------------------------------------|:-----------------------------------------------------------------:|
| 中央纪委国家监委通报2024年上半年全国纪检监察机关监督检查、审查调查情况 |  <https://www.ccdi.gov.cn/toutiaon/202407/t20240725_363777.html>  |
| 中央纪委国家监委通报2023年全国纪检监察机关监督检查审查调查情况         |  <https://www.ccdi.gov.cn/toutiaon/202401/t20240125_324375.html>  |
| 中央纪委国家监委通报2022年全国纪检监察机关监督检查审查调查情况         |  <https://www.ccdi.gov.cn/toutiaon/202301/t20230113_241506.html>  |
| 中央纪委国家监委通报2021年全国纪检监察机关监督检查审查调查情况         |  <https://www.ccdi.gov.cn/toutiaon/202201/t20220121_166060.html>  |
| 中央纪委国家监委通报2020年全国纪检监察机关监督检查、审查调查情况       |  <http://fanfu.people.com.cn/n1/2021/0126/c64371-32012165.html>   |
| 2019年全国纪检监察机关处分58.7万人 包括41名省部级干部                  |    <https://www.gov.cn/xinwen/2020-01/17/content_5470136.htm>     |
| 2018年全国纪检监察机关处分62.1万人 包括51名省部级及以上干部            |    <https://www.gov.cn/xinwen/2019-01/09/content_5356088.htm>     |
| 中央纪委通报2017年全国纪检监察机关纪律审查情况                         |  <https://www.ccdi.gov.cn/toutiao/201801/t20180110_161529.html>   |
| 中央纪委通报2016年全国纪检监察机关纪律审查情况                         |  <http://fanfu.people.com.cn/n1/2017/0105/c64371-29001051.html>   |
| 中纪委：2015年全国共立案33万件 处分33.6万人                            | <http://politics.people.com.cn/n1/2016/0115/c1001-28057743.html>  |
| 中央纪委监察部通报2013年度党风廉政建设等情况                           |     <https://www.gov.cn/gzdt/2014-01/11/content_2564326.htm>      |
| 十八届中央纪委五次全会工作报告解读                                     | <https://www.ccdi.gov.cn/lswh/lilun/201502/t20150203_119647.html> |
| 人民日报人民时评：深化监察改革，清除监督死角                           |  <http://opinion.people.com.cn/n1/2016/1110/c1003-28848980.html>  |
| 中纪委监察部通报2012年全国纪检机关查办案件工作                         |     <https://www.gov.cn/gzdt/2013-01/09/content_2308283.htm>      |
| 中央纪委监察部召开纪2011年查办案件情况通气会                           |     <https://www.gov.cn/jrzg/2012-01/06/content_2038597.htm>      |

实际上从2017年官方会按季度来通报全国纪检监察机关的统计报告，但键者时间有限（犯懒），仅按年整理数据，如下。

| 统计类别                                       | 2024上半年 | 2023年 | 2022年 | 2021年 | 2020年 | 2019年 | 2018年 | 2017年 | 2016年 | 2015年 | 2014年 |  2013年  |  2012年  |  2011年  |
|:-----------------------------------------------|:----------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:--------:|:--------:|:--------:|
| 接收信访举报（万件次）                         |   175.4    | 345.2  | 344.4  | 386.2  | 322.9  | 329.4  |  344   | 273.3  | 253.8  | 281.3  |  272   | 195.0374 | 130.6822 | 134.5814 |
| 其中检举控告类信访举报（万件次）               |    47.7    | 105.7  | 104.4  |        |        |        |        |        |        |  53.4  |        | 122.0191 | 86.6957  | 96.0461  |
| 处置问题线索（万件）                           |    97.1    | 173.3  |  154   | 182.6  | 170.3  | 170.5  | 166.7  | 125.1  |  73.4  |        |        |          |          |          |
| 其中谈话函询（万件）                           |            |  36.3  |  32.5  |  34.4  |  36.4  |  37.7  |  34.1  |  28.4  |  14.1  |  5.4   |  4.9   |  6.0834  |          |          |
| 立案（万件）                                   |    40.5    |  62.6  |  59.6  |  63.1  |  61.8  |  61.9  |  63.8  |  52.7  |  41.3  |   33   |  22.6  | 17.2532  | 15.5144  | 13.7859  |
| 立案省部级干部                                 |     41     |   87   |        |        |        |        |        |        |        |        |        |          |          |          |
| 立案厅局级干部                                 |    2127    |  3456  |        |        |        |        |        |        |        |        |        |          |          |          |
| 立案县处级干部（万人）                         |    1.7     |  2.7   |        |        |        |        |        |        |        |        |        |          |          |          |
| 立案乡科级干部（万人）                         |    5.6     |  8.9   |        |        |        |        |        |        |        |        |        |          |          |          |
| 立案现任或原任村党支部书记、村委会主任（万人） |    4.7     |  6.1   |        |        |        |        |        |        |        |        |        |          |          |          |
| 处分（万人）                                   |    33.2    |   61   |  59.2  |  62.7  |  60.4  |  58.7  |  62.1  |  52.7  |  41.5  |  33.6  |  23.2  | 18.2038  | 16.0718  | 14.2893  |
| 党纪处分（万人）                               |    26.6    |  49.8  |  48.9  |  52.4  |  52.2  |  50.2  |  52.6  |  44.3  |  34.7  |        |        | 15.0053  |          | 11.8006  |
| 政务处分（万人）                               |    9.3     |  16.2  |  14.9  |        |        |        |        |        |        |        |        |   4.89   |          |  3.5934  |
| 处分省部级干部                                 |     25     |   49   |   53   |   36   |   27   |   41   |   51   |   58   |   76   |        |        |          |          |          |
| 处分厅局级干部                                 |    1806    |  3144  |  2450  |  3024  |  2859  |  4000  |  3500  |  3300  |  2700  |        |        |          |          |          |
| 处分县处级干部（万人）                         |    1.3     |  2.4   |  2.1   |  2.5   |  2.2   |  2.4   |  2.6   |  2.1   |  1.8   |        |        |          |          |          |
| 处分乡科级干部（万人）                         |    4.3     |  8.2   |  7.4   |  8.8   |  8.3   |  8.5   |  9.1   |  7.8   |  6.1   |        |        |          |          |          |
| 处分一般干部（万人）                           |    4.6     |  8.5   |  8.3   |  9.7   |  9.9   |  9.8   |  11.1  |  9.7   |  7.6   |        |        |          |          |          |
| 处分农村、企业等其他人员（万人）               |    22.9    |  41.7  |  41.3  |  41.4  |  39.8  |  37.7  |   39   |  32.7  |  25.6  |        |        |          |          |          |
| 运用四种形态批评教育和处理（万人次）           |    87.9    | 171.8  | 183.8  | 212.5  | 195.4  | 184.9  | 173.7  | 131.6  |        |        |        |          |          |          |
| 第一种形态（万人次）                           |    54.2    | 109.6  | 123.2  | 148.7  |  133   | 124.6  | 110.4  |  78.6  |        |        |        |          |          |          |
| 第二种形态（万人次）                           |    27.1    |  49.2  |  47.8  |  49.4  |  48.5  |  46.3  |  49.5  |  41.2  |        |   20   |        |          |          |          |
| 第三种形态（万人次）                           |    3.1     |  6.4   |  6.4   |   7    |  7.1   |  7.2   |  8.2   |   7    |        |  8.2   |        |          |          |          |
| 第四种形态（万人次）                           |    3.6     |  6.6   |  6.4   |  7.4   |  6.8   |  6.8   |  5.5   |  4.8   |        |        |        |          |          |          |
| 立案行贿人员（万人）                           |    1.2     |  1.7   |        |        |        |        |        |        |        |        |        |          |          |          |
| 移送司法机关                                   |    1941    |  3389  |        |        |        |        |        |        |        | 1.4万  | 1.2万  |          |          |          |
| 处分违纪纪检监察干部                           |            |        |        |        |        |        |        |        |        |  2479  |  1575  |          |          |          |

值得一提的是，此文收集整理的只是“全国纪检监察机关的监督检查审查调查报告”，实际上中央纪委国家监委还会通报各年的“对纪检监察干部监督检查审查调查情况”，比如[2023年份](https://www.ccdi.gov.cn/toutiaon/202401/t20240125_324532.html)的情况如下。不过这部分数据就先挖坑不埋吧。

> 全国纪检监察系统共接收涉及纪检监察干部问题线索或反映4.65万余件次，处置涉及纪检监察干部问题线索4.37万余件，谈话函询纪检监察干部1.46万余人次，立案纪检监察干部8977人，处分7817人，移送司法机关474人，其中，处分厅局级干部207人、县处级1382人。
>
> 各级纪检监察机关运用“四种形态”批评教育和处理纪检监察干部3.72万余人次。其中，运用第一种形态批评教育和处理2.87万余人次，运用第二种形态处理7031人次，运用第三种形态处理884人次，运用第四种形态处理562人。

另外，除了全国的汇总统计数据，各省也会公布省级数据，比如[湖北省纪委监委通报2022年全省纪检监察机关监督检查审查调查情况](http://www.whdi.gov.cn/yaowenguanzhu/hubei/20230203/18685.html)。

[^1]: 见中国政府网的[中共中央办公厅印发《关于加强社会组织党的建设工作的意见（试行）》](https://www.gov.cn/xinwen/2015-09/28/content_2939936.htm)。

[^2]: 文章标题是《学习问答 \| 95.如何理解党政军民学，东西南北中，党是领导一切的？》，文章链接是<https://www.12371.cn/2021/09/24/ARTI1632437750600229.shtml>。

[^3]: 文章标题是《开启新时代 踏上新征程》，文章链接是<http://cpc.people.com.cn/n1/2017/1107/c64094-29630544.html>。

[^4]: 1.监察委的历史沿革<https://www.ccdi.gov.cn/xxgk/lsyg/201712/t20171230_159887.html>。1927年，设立中央监察委员会。1928年改为中央审查委员会。1949年成立中央人民政府政务院人民监察委员会。1954年改为国务院监察部。1969年取消监察机关。1977年恢复设立党的纪律检查委员会。1986年设立中华人民共和国监察部。2018年成立国家监察委员会。</br>2.监察法的立法纪实<https://www.ccdi.gov.cn/yaowen/201803/t20180321_166942.html>。</br>3.监察体制的改革试点<http://politics.people.com.cn/n1/2021/0502/c1001-32093886.html>。
