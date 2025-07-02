---
title: 看一看我国火灾事故数据
author: yuanfan
date: 2025-07-02T22:04:30+0800
slug: fire-disaster-data
categories:
  - R
tags:
  - R
draft: no
output:
  blogdown::html_page:
    toc: true
---

<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/echarts-en.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/ecStat.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/dataTool.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r-binding/echarts4r.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/echarts-en.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/ecStat.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/dataTool.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r-binding/echarts4r.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/echarts-en.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/ecStat.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/dataTool.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r-binding/echarts4r.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/echarts-en.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/ecStat.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/dataTool.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r-binding/echarts4r.js"></script>
<link href="{{< blogdown/postref >}}index_files/htmltools-fill/fill.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/echarts-en.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/ecStat.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r/dataTool.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/echarts4r-binding/echarts4r.js"></script>
<!--more-->

6月是我国安全生产月，上班路上看到有公交车经过，上面都贴着标语——“人人讲安全，个个会应急”。有关机构来公司做宣讲，讲师曾经作为武警官兵参加过数百起火灾救援，提及事故案例中被人们忽视的种种细节往往感同身受、痛心疾首，我第一次被抓去听这样的内容，实不相瞒，留下了非常深刻的印象。作为统计学的世界观，通常更愿意通过数据去认识世界，宣讲中提及一处细节，约是武汉市的火灾数量在疫情期间暴增数倍，在展示幻灯片时，这一页很快就略过，讲师只是借此强调形势之严峻，我却留心又好奇背后趋势变化的原因。

宣讲结束后，我最先想做的是去找找官方数据来源，确认这一现象确实存在，可能是检索的方式不对，没找到武汉市的火灾事故数据。当然啦，好奇心一翻起来，没这么容易死心。后来在国家统计局“年度数据-公共管理、社会保障及其他-火灾事故”这个目录下找到了全国的数据，不过只有1990至2012年的数据。而2013年至2024年的数据散落在一些新闻稿里，只好又手动整理一波，具体来源见文末附录。

如下是1990至2024年我国火灾事故数据，有三个时间节点出现了数量上的倍增，分别是：

1.  1996-1997：从3.7万起升到14万起。
2.  2012-2013：从15.2万起升到38.9万起。
3.  2020-2021：从25.2万起升到74.8万起。

而在火灾数量出现三次倍增的时间节点之前，还都存在一种缓慢下降的趋势。

翻查网上能找到的资料，我看到1996年11月11日我国颁布了《[火灾统计管理规定](https://www.asirlaw.com/m/view.php?aid=11156)》，这项规定从1997年1月1日起开始实施，其中第五条规定“所有火灾不论损害大小，都列入火灾统计范围”。我猜可能是这项规定使得1997年开始火灾数据统计口径发生了调整，也就出现了第一次的数量倍增。

<div class="echarts4r html-widget html-fill-item" id="htmlwidget-1" style="width:100%;height:500px;"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true,"name":"火灾发生数(万起)"}],"xAxis":[{"type":"category"}],"legend":{"data":["火灾发生数"],"show":true,"type":"plain","top":"7%","itemStyle":{"color":"#5a8d95"}},"series":[{"data":[{"value":[1990,5.7],"itemStyle":{"color":"#5a8d95"}},{"value":[1991,4.5],"itemStyle":{"color":"#5a8d95"}},{"value":[1992,3.9],"itemStyle":{"color":"#5a8d95"}},{"value":[1993,3.8],"itemStyle":{"color":"#5a8d95"}},{"value":[1994,3.9],"itemStyle":{"color":"#5a8d95"}},{"value":[1995,3.7],"itemStyle":{"color":"#5a8d95"}},{"value":[1996,3.7],"itemStyle":{"color":"red"}},{"value":[1997,14],"itemStyle":{"color":"red"}},{"value":[1998,14.1],"itemStyle":{"color":"#5a8d95"}},{"value":[1999,18],"itemStyle":{"color":"#5a8d95"}},{"value":[2000,18.9],"itemStyle":{"color":"#5a8d95"}},{"value":[2001,21.7],"itemStyle":{"color":"#5a8d95"}},{"value":[2002,25.8],"itemStyle":{"color":"#5a8d95"}},{"value":[2003,25.4],"itemStyle":{"color":"#5a8d95"}},{"value":[2004,25.3],"itemStyle":{"color":"#5a8d95"}},{"value":[2005,23.6],"itemStyle":{"color":"#5a8d95"}},{"value":[2006,22.3],"itemStyle":{"color":"#5a8d95"}},{"value":[2007,16.4],"itemStyle":{"color":"#5a8d95"}},{"value":[2008,13.7],"itemStyle":{"color":"#5a8d95"}},{"value":[2009,12.9],"itemStyle":{"color":"#5a8d95"}},{"value":[2010,13.2],"itemStyle":{"color":"#5a8d95"}},{"value":[2011,12.5],"itemStyle":{"color":"#5a8d95"}},{"value":[2012,15.2],"itemStyle":{"color":"red"}},{"value":[2013,38.9],"itemStyle":{"color":"red"}},{"value":[2014,39.5],"itemStyle":{"color":"#5a8d95"}},{"value":[2015,33.8],"itemStyle":{"color":"#5a8d95"}},{"value":[2016,31.2],"itemStyle":{"color":"#5a8d95"}},{"value":[2017,28.1],"itemStyle":{"color":"#5a8d95"}},{"value":[2018,23.7],"itemStyle":{"color":"#5a8d95"}},{"value":[2019,23.3],"itemStyle":{"color":"#5a8d95"}},{"value":[2020,25.2],"itemStyle":{"color":"red"}},{"value":[2021,74.8],"itemStyle":{"color":"red"}},{"value":[2022,82.5],"itemStyle":{"color":"#5a8d95"}},{"value":[2023,87.8],"itemStyle":{"color":"#5a8d95"}},{"value":[2024,90.8],"itemStyle":{"color":"#5a8d95"}}],"name":"火灾发生数","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"cartesian2d","label":{"show":true,"position":"top"}}],"title":[{"left":"center","text":"1990至2024年全国火灾事故数量"}]},"dispose":true},"evals":[],"jsHooks":[]}</script>

再看历年火灾事故的平均情况，最近15年平均每10万起火灾死亡/手上人数存在下降趋势。再对比第二次、第三次火灾事故数量倍增的节点，平均每起火灾事故的经济损失也有下降。这些“下降”固然是因为分母陡然增大，另一方面也体现出，可能是相对损失更小的火灾数量变多，即居民遇到火灾报警的意识增强、火灾统计的制度细节更加完善。

| 节点一 | 平均每起事故经济损失（元） | 节点一 | 平均每起事故经济损失（元） |
|:------:|:--------------------------:|:------:|:--------------------------:|
|  2012  |           14309            |  2020  |           15909            |
|  2013  |           12465            |  2021  |            9024            |

<div class="echarts4r html-widget html-fill-item" id="htmlwidget-2" style="width:100%;height:500px;"></div>
<script type="application/json" data-for="htmlwidget-2">{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true,"name":"每10万起火灾\n死亡/受伤人数","max":16000},{"type":"value","name":"平均每起火灾\n经济损失(元)"}],"xAxis":[{"type":"category"}],"legend":{"data":["死亡人数","受伤人数","经济损失"],"show":true,"type":"plain","top":"7%"},"series":[{"data":[{"value":[1990,3677]},{"value":[1991,4529]},{"value":[1992,4917]},{"value":[1993,6476]},{"value":[1994,7234]},{"value":[1995,6010]},{"value":[1996,6037]},{"value":[1997,1940]},{"value":[1998,1684]},{"value":[1999,1525]},{"value":[2000,1597]},{"value":[2001,1077]},{"value":[2002,926]},{"value":[2003,977]},{"value":[2004,1012]},{"value":[2005,1058]},{"value":[2006,681]},{"value":[2007,989]},{"value":[2008,1112]},{"value":[2009,955]},{"value":[2010,909]},{"value":[2011,883]},{"value":[2012,676]},{"value":[2013,543]},{"value":[2014,460]},{"value":[2015,515]},{"value":[2016,507]},{"value":[2017,495]},{"value":[2018,594]},{"value":[2019,573]},{"value":[2020,469]},{"value":[2021,266]},{"value":[2022,249]},{"value":[2023,null]},{"value":[2024,220]}],"yAxisIndex":0,"xAxisIndex":0,"name":"死亡人数","type":"line","coordinateSystem":"cartesian2d","color":"#1C77A3FF"},{"data":[{"value":[1990,8241]},{"value":[1991,8321]},{"value":[1992,8601]},{"value":[1993,15690]},{"value":[1994,10809]},{"value":[1995,10152]},{"value":[1996,9301]},{"value":[1997,3514]},{"value":[1998,3463]},{"value":[1999,2541]},{"value":[2000,2328]},{"value":[2001,1744]},{"value":[2002,1322]},{"value":[2003,1216]},{"value":[2004,1175]},{"value":[2005,1062]},{"value":[2006,637]},{"value":[2007,593]},{"value":[2008,543]},{"value":[2009,503]},{"value":[2010,471]},{"value":[2011,455]},{"value":[2012,378]},{"value":[2013,421]},{"value":[2014,378]},{"value":[2015,329]},{"value":[2016,341]},{"value":[2017,314]},{"value":[2018,337]},{"value":[2019,359]},{"value":[2020,308]},{"value":[2021,297]},{"value":[2022,257]},{"value":[2023,null]},{"value":[2024,294]}],"yAxisIndex":0,"xAxisIndex":0,"name":"受伤人数","type":"line","coordinateSystem":"cartesian2d","color":"#67B8D6FF"},{"data":[{"value":[1990,8932]},{"value":[1991,11509]},{"value":[1992,17523]},{"value":[1993,29340]},{"value":[1994,31631]},{"value":[1995,29022]},{"value":[1996,27922]},{"value":[1997,10988]},{"value":[1998,10190]},{"value":[1999,7968]},{"value":[2000,8046]},{"value":[2001,6473]},{"value":[2002,5979]},{"value":[2003,6265]},{"value":[2004,6616]},{"value":[2005,5776]},{"value":[2006,3523]},{"value":[2007,6881]},{"value":[2008,13315]},{"value":[2009,12551]},{"value":[2010,14789]},{"value":[2011,16405]},{"value":[2012,14309]},{"value":[2013,12465]},{"value":[2014,11114]},{"value":[2015,11686]},{"value":[2016,11923]},{"value":[2017,12811]},{"value":[2018,15506]},{"value":[2019,15502]},{"value":[2020,15909]},{"value":[2021,9024]},{"value":[2022,8679]},{"value":[2023,null]},{"value":[2024,8524]}],"name":"经济损失","type":"bar","yAxisIndex":1,"xAxisIndex":0,"coordinateSystem":"cartesian2d","color":"#5a8d95"}],"title":[{"left":"center","text":"1990至2024年全国火灾平均情况"}],"tooltip":{"trigger":"axis"}},"dispose":true},"evals":[],"jsHooks":[]}</script>

仍然无法忽视的是，火灾数量的绝对值的翻倍增长。2012年我国总人口为13.68亿人，2024年我国总人口为14.08亿人，人口绝对值仅上升2.9%，但全国火灾数量从15.2万起上升到90.8万起，火灾数量绝对值上升近5倍。其中农村的火灾数量从4.7万起上升到53.4万起，火灾数量绝对值上升10倍多；而城市的火灾数量从5.2万起上升到35万起，其数量绝对值也上升将近6倍。

这里需要说明一点，在2012年，我国火灾统计按区域统计后的各项占比分别是，农村占31%、城市占33.9%、县城集镇占27%、其他区域占8.1%；而在2024年，我国城乡二元分化结构基本固定，对“县城集镇”的统计已分别纳入农村和城市，因而各项占比变成，农村占58.8%、城市占38.6%、其他区域占2.6%。

| 年份 | 农村-火灾数量（万起） | 农村-火灾占比 | 城市-火灾数量（万起） | 城市-火灾占比 |
|:----:|:---------------------:|:-------------:|:---------------------:|:-------------:|
| 2012 |          4.7          |      31%      |          5.2          |     33.9%     |
| 2013 |         12.6          |     32.4%     |                       |               |
| 2014 |         13.4          |     33.8%     |         11.9          |      30%      |
| 2015 |                       |               |         10.6          |     30.6%     |
| 2016 |         9.72          |     32.9%     |          9.4          |     30.6%     |
| 2020 |         12.4          |     49.3%     |                       |               |
| 2021 |         40.8          |     54.6%     |                       |               |
| 2022 |         46.2          |      56%      |                       |               |
| 2024 |         53.4          |     58.8%     |          35           |     38.6%     |

以上只是一些数量的展示，由于收集到的数据实在有限，无法详细分析具体原因。下面展开的部分仅仅只是俺的推测，没有通过任何统计学的理论检验。

按起火原因统计，在2012年占比最多的两项分别是，电气原因占32.2%、生活用火不慎占17.9%；而在2024年则是，电气原因占32.3%、生活用火不慎占21.8%。电气原因涵义丰富，大致是电线短路、过负荷、电气设备故障、违规使用电气等等，可归结为与电气设备相关。而生活用火不慎，表层原因是用火之人粗心大意，但深层原因更可能是用火的安全意识不够强。

下面先看城乡二元结构下平均每百户居民的电动车拥有量，2013年城镇、农村的电动车拥有量十分接近，都是每百户40辆左右，到了2024年城镇每百户70.5辆、农村每百户89.1辆，这个差距或许是造成农村火灾数量更高的原因之一。而电动车拥有量的倍增，本身也是火灾数量倍增的部分原因。

<div class="echarts4r html-widget html-fill-item" id="htmlwidget-3" style="width:100%;height:500px;"></div>
<script type="application/json" data-for="htmlwidget-3">{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true,"name":"居民平均每百户\n电动助力车拥有量(辆)"}],"xAxis":[{"type":"category"}],"legend":{"data":["城镇","农村"],"show":true,"type":"plain","top":"7%"},"series":[{"data":[{"value":[2013,39]},{"value":[2014,42.5]},{"value":[2015,45.8]},{"value":[2016,49.7]},{"value":[2017,53.1]},{"value":[2018,55]},{"value":[2019,59.4]},{"value":[2020,62]},{"value":[2021,68.8]},{"value":[2022,70.5]},{"value":[2023,67.09999999999999]},{"value":[2024,70.5]}],"name":"城镇","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"cartesian2d","color":"#1C77A3FF","label":{"show":true,"position":"top"}},{"data":[{"value":[2013,40.3]},{"value":[2014,45.4]},{"value":[2015,50.1]},{"value":[2016,57.7]},{"value":[2017,61.1]},{"value":[2018,64.90000000000001]},{"value":[2019,70.09999999999999]},{"value":[2020,73.09999999999999]},{"value":[2021,80.7]},{"value":[2022,82.5]},{"value":[2023,84.90000000000001]},{"value":[2024,89.09999999999999]}],"name":"农村","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"cartesian2d","color":"#67B8D6FF","label":{"show":true,"position":"top"}}],"tooltip":{"trigger":"axis"},"title":[{"left":"center","text":"2013至2024年城乡二元电动车拥有量"}]},"dispose":true},"evals":[],"jsHooks":[]}</script>

再看城乡二元结构下的人口比例，2012年城镇人口占比53%、农村人口占比37%，到了2024年变为城镇人口占比67%、农村人口占比33%。我国近三分之二人口生活在城市，面临着城市住宅房屋老化、楼房人口密集等带来的隐患，同时也带来的是政府将投入更多的人力物力去宣导提升城镇居民的消防安全生产意识、以及更多的公共资源去排除火灾隐患。而在土地广袤的农村，基层政权无法像城市一样通过社区网格迅速触及每户人家，这可能会使得农村居民用火的安全意识相对城市居民更为薄弱，自2006年农业税全面免除后，农民进城打工作为农民工为城市各行各业做出贡献，而国家的收入二次分配在农村的公共财政支出却占比极低，农民自身收入低加上公共财政分配的福利少也会导致农村使用电气的安全隐患更难被去除，甚至可能因为电商平台的迅猛发展，而购买到更多低价但假冒伪劣的电气商品，一切种种因素的叠加造成了占总人口33%的农村居民却发生了火灾数量的58.5%。

<div class="echarts4r html-widget html-fill-item" id="htmlwidget-4" style="width:100%;height:500px;"></div>
<script type="application/json" data-for="htmlwidget-4">{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true,"name":"百分比(%)","axisLabel":{"formatter":"function(value, index) {\n        var fmt = new Intl.NumberFormat('en', {\"style\":\"percent\",\"minimumFractionDigits\":0,\"maximumFractionDigits\":0,\"currency\":\"USD\"});\n        return fmt.format(value);\n    }"}}],"xAxis":[{"type":"category"}],"legend":{"data":["城镇人口占比","农村人口占比"],"show":true,"type":"plain","top":"7%"},"series":[{"data":[{"value":[1990,0.26]},{"value":[1991,0.27]},{"value":[1992,0.27]},{"value":[1993,0.28]},{"value":[1994,0.29]},{"value":[1995,0.29]},{"value":[1996,0.3]},{"value":[1997,0.32]},{"value":[1998,0.33]},{"value":[1999,0.35]},{"value":[2000,0.36]},{"value":[2001,0.38]},{"value":[2002,0.39]},{"value":[2003,0.41]},{"value":[2004,0.42]},{"value":[2005,0.43]},{"value":[2006,0.44]},{"value":[2007,0.46]},{"value":[2008,0.47]},{"value":[2009,0.48]},{"value":[2010,0.5]},{"value":[2011,0.52]},{"value":[2012,0.53]},{"value":[2013,0.54]},{"value":[2014,0.5600000000000001]},{"value":[2015,0.57]},{"value":[2016,0.59]},{"value":[2017,0.6]},{"value":[2018,0.62]},{"value":[2019,0.63]},{"value":[2020,0.64]},{"value":[2021,0.65]},{"value":[2022,0.65]},{"value":[2023,0.66]},{"value":[2024,0.67]}],"yAxisIndex":0,"xAxisIndex":0,"name":"城镇人口占比","type":"line","coordinateSystem":"cartesian2d","color":"#1C77A3FF","markPoint":{"label":{"formatter":"67%"},"data":[{"type":"max"}]}},{"data":[{"value":[1990,0.74]},{"value":[1991,0.73]},{"value":[1992,0.73]},{"value":[1993,0.72]},{"value":[1994,0.71]},{"value":[1995,0.71]},{"value":[1996,0.7]},{"value":[1997,0.68]},{"value":[1998,0.67]},{"value":[1999,0.65]},{"value":[2000,0.64]},{"value":[2001,0.62]},{"value":[2002,0.61]},{"value":[2003,0.59]},{"value":[2004,0.58]},{"value":[2005,0.57]},{"value":[2006,0.5600000000000001]},{"value":[2007,0.54]},{"value":[2008,0.53]},{"value":[2009,0.52]},{"value":[2010,0.5]},{"value":[2011,0.48]},{"value":[2012,0.47]},{"value":[2013,0.46]},{"value":[2014,0.44]},{"value":[2015,0.43]},{"value":[2016,0.41]},{"value":[2017,0.4]},{"value":[2018,0.38]},{"value":[2019,0.37]},{"value":[2020,0.36]},{"value":[2021,0.35]},{"value":[2022,0.35]},{"value":[2023,0.34]},{"value":[2024,0.33]}],"yAxisIndex":0,"xAxisIndex":0,"name":"农村人口占比","type":"line","coordinateSystem":"cartesian2d","color":"#67B8D6FF","markPoint":{"label":{"formatter":"33%"},"data":[{"type":"min"}]}}],"tooltip":{"trigger":"item","formatter":"function(params, ticket, callback) {\n        var fmt = new Intl.NumberFormat('en', {\"style\":\"percent\",\"minimumFractionDigits\":0,\"maximumFractionDigits\":0,\"currency\":\"USD\"});\n        var idx = 0;\n        if (params.name == params.value[0]) {\n            idx = 1;\n        }\n        return params.value[0] + '<br>' +\n               params.marker + ' ' +\n               params.seriesName + ': ' + fmt.format(parseFloat(params.value[idx]));\n    }"},"title":[{"left":"center","text":"1990至2024年城乡二元人口比例"}]},"dispose":true},"evals":["opts.yAxis.0.axisLabel.formatter","opts.tooltip.formatter"],"jsHooks":[]}</script>

在收集数据的过程中，我还发现了一个离谱的数据增长，在多项起火原因之中，吸烟引发火灾的比例从2012年的6.2%上升到了2024年的15.3%。前几天无意中看到深圳卫健委发布的一篇文章，《[二手烟，其实是一种霸凌](https://mp.weixin.qq.com/s/olh6GIOt8WfTcPoWBePehg)》，文中提到2020年烟草产业带来的收益约1.52万亿元，但因为吸烟导致的直接医疗花费及人员生产力损失却有2.43万亿元，若是再加上吸烟引发火灾造成的经济损失，非吸烟者暴露于二手烟造成的慢性疾病带来的损失……所以我真是讨厌在公共场所吸烟的人，每天上班路上、街边吃早餐的时候都会碰到吸烟的人，扯远了……

<div class="echarts4r html-widget html-fill-item" id="htmlwidget-5" style="width:100%;height:500px;"></div>
<script type="application/json" data-for="htmlwidget-5">{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true,"axisLabel":{"formatter":"{value}%"}}],"xAxis":[{"type":"category"}],"legend":{"data":["吸烟引发火灾的比例"]},"series":[{"data":[{"value":[2012,6.2]},{"value":[2014,6]},{"value":[2015,5.6]},{"value":[2016,5.2]},{"value":[2017,8]},{"value":[2018,7.3]},{"value":[2021,10.9]},{"value":[2024,15.3]}],"name":"吸烟引发火灾的比例","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"cartesian2d","color":"red","label":{"show":true,"position":"top","fontSize":24,"formatter":"{@[1]}%"}}]},"dispose":true},"evals":[],"jsHooks":[]}</script>

- 附录（2012-2024数据来源）
- 2024: <https://www.119.gov.cn/qmxfxw/mtbd/wzbd/2025/48022.shtml>
- 2023: <https://news.qq.com/rain/a/20240105A06B4100>
- 2022: <https://www.119.gov.cn/qmxfxw/xfyw/2023/36210.shtml?eqid=e0f3be5a0012a4040000000364816cd3>
- 2021: <https://news.cyol.com/gb/articles/2022-01/20/content_n23bnie3x.html>
- 2020: <http://society.people.com.cn/n1/2021/0130/c1008-32017707.html>
- 2019: <https://news.cctv.com/2020/01/11/ARTI6aJfesXIvbGCKUTVUpre200111.shtml>
- 2018: <https://www.fire114.cn/index/article/detail?i=67960>
- 2017: <https://www.fire114.cn/index/article/detail?i=68151>
- 2016: <https://www.mps.gov.cn/n2255079/n5590589/n5596621/n5596628/c5598172/content.html>/<https://www.mps.gov.cn/n2255079/n5590589/n5596621/n5596628/c5598172/content.html>/<http://www.xfkerich.com/web/newsdetail.do?id=101>
- 2015: <https://www.gov.cn/xinwen/2016-01/19/content_5034356.htm>/<http://www.xfkerich.com/web/newsdetail.do?id=102>
- 2014: <https://www.gov.cn/xinwen/2015-02/13/content_2819433.htm>/<http://www.xfkerich.com/web/newsdetail.do?id=103>
- 2013: <http://www.ncfcsa.cn/1/5474.aspx>/<http://www.xfkerich.com/web/newsdetail.do?id=104>
- 2012: <http://www.xfkerich.com/web/newsdetail.do?id=105>/<https://www.doc88.com/p-1117283485671.html>
