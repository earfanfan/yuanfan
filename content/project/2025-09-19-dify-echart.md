---
title: Dify 生成 echarts 图表
author: yuanfan
date: 2025-09-19T20:43:02+0800
slug: dify echart
categories:
  - AI
tags:
  - AI
draft: no
---

<!--more-->

最近好领导把 Dify 生成图表琢磨出来了，征得同意后，在他的基础上我继续研究，然后自己琢磨写一篇技术博客。

为了便于直接测试生成图形的效果，本文记录的笔记都是在 Dify 上创建 Chatflow 来完成的。实际工作项目中一般是将绘图创建为一个工作流，然后在正式的 Chatflow 作为一个节点来引入。

# 一、调用 Echarts 图表生成工具

Dify 官方提供了一个名为“Echarts 图表生成”的工具，但目前仅支持线性图表（ps折线图）、柱状图、饼图等三种图形，而且可接受的数据格式也很受限制。在线性图表或柱状图的节点，对于输入数据有下面这样一行小字，这起码说明仅能输入一列数字，对应只能生成单条折线的图形。

>用于生成线性图表的数据，每个数字之间用 ";" 分隔

不过，这里还是要先弄懂“Echarts 图表生成”这个工具，后续才能扩展更多。整体流程如下图所示，准备好要输入的数据和图形类型，一步步直至生成最终图形。

<details>
<summary>折叠绘图的 R 代码</summary>
<pre><code>

```r
library(DiagrammeR)

grViz(diagram = "digraph{
 # 定义图形布局，从左到右
  graph[rankdir = LR]
 # 定义节点       
  node[shape = rectangle]
      A[label = '开始']
      B[label = '提取图形参数\n节点：代码执行']
      D[label = '判断图表类型分支\n节点：条件分支']
      E1[label = '线性图表\n工具：Echarts 图表生成']
      E2[label = '饼图\n工具：Echarts 图表生成']
      E3[label = '柱状图\n工具：Echarts 图表生成']
      F1[label = '直接回复1']
      F2[label = '直接回复2']
      F3[label = '直接回复3']

 # 定义线     
 edge[arrowsize = 1,style = solid]
  A -> B -> D 
  D -> E1;D->E2;D->E3;
  E1 -> F1; E2 -> F2; E3 -> F3
}")
```

</code></pre>
</details>

![](https://yuanfan.rbind.io/images/2025/20250919-01.png)

接下来，依次梳理各个节点的细节。

## 1.1.开始

“开始”节点。设置必填的输入字段有两个，如下所示。

+ `query_data`，输入的 JSON 格式数据，字段类型选段落（长文本），最大长度往大了填如65536。
+ `chart_type`，输入的图表类型，仅限折线图、饼图、柱状图。

>注意：JSON 要求所有键和字符串值都必须用双引号`"`包裹，换用单引号会报错的。

下面是测试时使用的输入数据。

### 1.1.1.折线图

+ query_data

```js
[
  {"月份": "2024-01","月达成": 1619 },
  {"月份": "2024-02", "月达成": 452},
  {"月份": "2024-03", "月达成": 692},
  {"月份": "2024-04", "月达成": 324}
]
```

+ chart_type：折线图。

### 1.1.2.饼图

+ query_data

```js
[
  { "value": 4, "name": "甲" },
  { "value": 3, "name": "乙" },
  { "value": 2, "name": "丙" },
  { "value": 5, "name": "丁" }
]
```

+ chart_type: 饼图。

### 1.1.3.柱状图

+ query_data

```js
[
  { "value1": 1048, "name": "甲" },
  { "value1": 735, "name": "乙" },
  { "value1": 580, "name": "丙" },
  { "value1": 484, "name": "丁" }
]
```

+ chart_type: 柱状图。

## 1.2.提取图形参数

“代码执行”节点，调用 python 将输入的 JSON 格式数据解析，并生成下一个节点所需数据。默认的逻辑是将数值型的字段作为 Y 轴的数据，将非数值的字段作为 X 轴的数据。

+ 输入变量
  - `query_data`：`</>开始/(x)query_data`，string 类型。
  - `chart_type`：`</>开始/(x)chart_type`，string 类型。
+ 输出变量
  - `report_name`，string 类型，图表名称。
  - `data_x`，string 类型，横轴数据。
  - `data_y`，string 类型，纵轴数据。
  - `x_name`，string 类型，横轴坐标轴名称。
  - `y_name`，string 类型，纵轴坐标轴名称。
  - `report_type`，string 类型，图表类型。
  
具体可执行的 python 代码如下。  

```python
import json

def main(chart_type: str, query_data: str) -> dict:
    # 解析 query_data 字符串为 Python 列表
    try:
        data_list = json.loads(query_data)
    except Exception as e:
        raise ValueError(f"query_data 格式错误：{e}")

    if not isinstance(data_list, list) or len(data_list) == 0:
        raise ValueError("query_data 必须是非空列表")

    # 获取字段名
    keys = list(data_list[0].keys())
    if len(keys) < 2:
        raise ValueError("query_data 中至少需要两个字段")

    # 自动识别字段类型
    x_key = None
    y_key = None

    for key in keys:
        sample_value = data_list[0][key]
        if isinstance(sample_value, (int, float)):
            if y_key is None:
                y_key = key
        elif isinstance(sample_value, str):
            if x_key is None:
                x_key = key

    if x_key is None or y_key is None:
        raise ValueError("无法自动识别 x 轴和 y 轴字段，请确保包含字符串和数值字段")

    # 构造数据串
    data_x = ";".join(str(item[x_key]) for item in data_list)
    data_y = ";".join(str(item[y_key]) for item in data_list)

    # 映射图表类型
    chart_map = {
        "折线图": "line",
        "柱状图": "bar",
        "饼图": "pie"
    }
    report_type = chart_map.get(chart_type)
    if report_type is None:
        raise ValueError(f"chart_type 不支持：{chart_type}")

    return {
        "data_x": data_x,
        "data_y": data_y,
        "report_name": f"{x_key} 与 {y_key} 的 {chart_type}",
        "report_type": report_type,
        "x_name": x_key,
        "y_name": y_key
    }
```

## 1.3.判断图表类型分支

根据上一节点输出的变量`report_type`来判断，如果包含`line`则选择下一分支为线性图表，如果包含`pie`则选择下一分支为饼图，如果包含`bar`则选择下一分支为柱状图。 

## 1.4.Echarts 图表生成

Echarts 图表生成是官方开发的工具，当前仅支持绘制线性图表、饼图、柱状图，要将“提取图形参数”节点的输出变量作为这些绘图节点的输入变量

+ 线性图表/柱状图
  - 标题：`</>提取图形参数/(x)report_name`
  - 数据：`</>提取图形参数/(x)data_y`
  - X轴：`</>提取图形参数/(x)data_x`
+ 饼图
  - 标题：`</>提取图形参数/(x)report_name`
  - 数据：`</>提取图形参数/(x)data_y`
  - 分类：`</>提取图形参数/(x)data_x`

而该节点输出的变量是固定的如下三组内容。值得注意的是，似乎暂时在输出时只有`text`有值，所以对应下一个直接回复节点也要选`text`。

```
text   string
工具生成的内容
files  array[file]
工具生成的文件
json   array[object]
工具生成的 json
```

## 1.5.直接回复

成功执行一次后，逐一观察每个节点输入和输出的内容，可以看到“Echarts 图表生成”这个节点输出的仅仅只是如下的 echart 代码。随后在“直接回复”节点输入的也是 echart 代码，但输出的就是 echart 图形。这说明 Dify 环境里可以通过执行 echart 代码生成图形。

````
{
  text:{```echart
  ---代码内容---
```},
  file:{ },
  json:{ data:[ ]}
}
````

# 二、自定义 echart 代码

Dify 内置了 Echarts 这个 JavaScript 组件，所以其实只要生成正常的 echart 代码，就能生成图形。 

本章节流程如下所示，准备好要输入的数据和图形类型，解析数据，拼接 echart 代码，最后生成图形

![](https://yuanfan.rbind.io/images/2025/20250919-02.png)

## 2.1.开始

“开始”节点。设置必填的输入字段有两个，如下所示。

+ `query_data`，输入的 JSON 格式数据，字段类型选段落（长文本），最大长度往大了填如65536。
+ `chart_type`，输入的图形类型，可填 line、bar、pie、scatter 等（ps 由于上一章填写的是汉字的图形类型，于是提取图形参数时多了转换成英文单词的步骤，本章节这里改为直接填写英文单词）。

下面是测试时使用的一些数据。

```js
[
  { "value1": 1048,"value2": 1048,"value3": 1048,"name": "甲" },
  { "value1": 735, "value2": 1048,"value3": 1048,"name": "乙" },
  { "value1": 580, "value2": 1048,"value3": 1048,"name": "丙" },
  { "value1": 484, "value2": 1048,"value3": 1048,"name": "丁" }
]


[
  { "value1": 1048,"value2": 1048,"value3": 1048,"年份": "2022"},
  { "value1": 735, "value2": 1048,"value3": 2000,"年份": "2023" },
  { "value1": 580, "value2": 1048,"value3": 1048,"年份": "2024" },
  { "value1": 484, "value2": 1048,"value3": 2000,"年份": "2025" }
]


[
  { "value": 0.4, "name": "甲" },
  { "value": 0.3, "name": "乙" },
  { "value": 0.2, "name": "丙" },
  { "value": 0.5, "name": "丁" }
]
```

## 2.2.提取图形参数

“代码执行”节点，调用 python 将输入的 JSON 格式数据解析，并生成下一个节点所需数据。与上一章节的区别是，将输入数据中所有数值列组合为一个列表，然后直接和输入的图形类型组合为一个完整的`series_data`（数据系列），包含`name`（数据系列的名称）、`type`（图形类型）、`data`（数据）。这样的话，输入数据中含有多个数值列时，可以绘制多条折线、多个柱子或者散点图。

+ 输入变量
  - `query_data`：`</>开始/(x)query_data`，string 类型。
  - `chart_type`：`</>开始/(x)chart_type`，string 类型。
+ 输出变量
  - `report_name`，string 类型，图表名称。
  - `x_values`，string 类型，横轴数据。
  - `series_data`，string 类型，纵轴数据。
  - `x_name`，string 类型，横轴坐标轴名称。
  - `y_name`，string 类型，纵轴坐标轴名称。
  - `chart_type`，string 类型，图表类型。

具体可执行的 python 代码如下。

```python
import json

def main(chart_type: str, query_data: str) -> dict:
    try:
        data_list = json.loads(query_data)
    except Exception as e:
        raise ValueError(f"query_data 格式错误：{e}")

    if not isinstance(data_list, list) or len(data_list) == 0:
        raise ValueError("query_data 必须是非空列表")

    keys = list(data_list[0].keys())
    if len(keys) < 2:
        raise ValueError("query_data 中至少需要两个字段")

    # 自动识别字段类型
    x_key = None
    y_keys = []

    for key in keys:
        sample_value = data_list[0][key]
        if isinstance(sample_value, (int, float)):
            y_keys.append(key)
        elif isinstance(sample_value, str) and x_key is None:
            x_key = key

    if x_key is None or len(y_keys) == 0:
        raise ValueError("无法自动识别 x 轴和 y 轴字段，请确保包含字符串和数值字段")

    # 提取 X 轴标签
    x_values = [item[x_key] for item in data_list]
    x_values_str = str(x_values)

    # 构造 series_data 为 JSON 字符串
    series_data = []
    for y_key in y_keys:
        series_data.append({
            "name": y_key,
            "type": chart_type,
            "data": [item[y_key] for item in data_list]
        })
    series_data_str = json.dumps(series_data, ensure_ascii=False)

    return {
        "x_name": x_key,
        "y_name": ";".join(y_keys),
        "report_name": "与".join(keys) + f"的{chart_type}",
        "x_values": x_values_str,
        "series_data": series_data_str,
        "chart_type": chart_type
    }

```

## 2.3.生成 echart 代码（折、柱、饼、散点）

“代码执行”节点，调用 python 将上个节点提取到的数据拼接成完整的 echart 代码。下面是在 Apache Echarts 官网找的一些配置项，分别按照折线图和柱状图、饼图、散点图所需内容拼接。

```python
import json

def main(x_values: str, series_data: str, x_name: str, y_name: str, report_name: str, chart_type: str) -> dict:
    x_data = json.loads(x_values.replace("'", '"'))
    series_raw = json.loads(series_data)
    
    # 拼接 柱状图、散点图
    if chart_type in ["bar", "line"]:
        echarts_config = {
            "title": {
                "left": "center",
                "text": report_name
            },
            "tooltip": {
                "trigger": "axis"
            },
            "legend": {
                "top": "bottom"
            },
            "xAxis": {
                "type": "category",
                "name": x_name,
                "data": x_data
            },
            "yAxis": {
                "type": "value",
                "name": y_name
            },
            "series": series_raw
        }

    # 拼接 饼图
    elif chart_type == "pie":
        pie_data = []
        for i in range(len(x_data)):
            pie_data.append({
                "value": series_raw[0]["data"][i],
                "name": str(x_data[i])
            })

        echarts_config = {
            "title": {
                "left": "center",
                "text": report_name
            },
            "tooltip": {
                "trigger": "item"
            },
            "legend": {
                "top": "bottom"
            },
            "series": [
                {
                    "name": report_name,
                    "type": "pie",
                    "radius": "50%",
                    "data": pie_data,
                    "label": {
                        "position": "outer",
                        "alignTo": "labelLine",
                        "formatter": "{b}: {c},{d}%"
                    },
                    "emphasis": {
                        "itemStyle": {
                            "shadowBlur": 10,
                            "shadowOffsetX": 0,
                            "shadowColor": "rgba(0, 0, 0, 0.5)"
                        }
                    }
                }
            ]
        }
     
    # 拼接 散点图
    elif chart_type == "scatter":
        if len(series_raw) < 2:
            raise ValueError("散点图至少需要两个数值列作为 X 和 Y 坐标")

        # 只取前两个数值列
        x_series = series_raw[0]["data"]
        y_series = series_raw[1]["data"]

        if len(x_series) != len(y_series):
            raise ValueError("X 和 Y 数据长度不一致，无法生成散点图")

        scatter_points = [[x_series[i], y_series[i]] for i in range(len(x_series))]

        echarts_config = {
            "title": {
                "left": "center",
                "text": report_name
            },
            "tooltip": {
                "trigger": "item"
            },
            "xAxis": {
                "type": "value",
                "name": series_raw[0]["name"]
            },
            "yAxis": {
                "type": "value",
                "name": series_raw[1]["name"]
            },
            "series": [
                {
                    "type": "scatter",
                    "symbolSize": 20,
                    "data": scatter_points
                }
            ]
        }

    else:
        raise ValueError(f"不支持的图表类型: {chart_type}")

    echarts_script = f"```echarts\n{json.dumps(echarts_config, ensure_ascii=False, indent=2)}\n```"

    return {
        "echarts_code": echarts_script
    }
```

# 三、其他

1. 如果做 AI 辅助数据分析的项目，应该调用 LLM 节点根据用户输入的自然语言来生成图形类型、图表标题、坐标轴名称等信息。

2. 本文仅涉及针对包含一个维度列、多个数值列的数据的情况，正式项目中生成图表的上一个节点往往是让 AI 生成 sql 取数，应该把两个节点联合起来控制，比如生成 sql 时都顺便排序。

3. 本来还花了不少时间琢磨用 Dify 调用“AntV 可视化图表”工具，不晓得为撒一直报错 timed out，暂时放弃。

4. 除了折线图、柱状图、饼图、散点图，理论上还可以绘制更多不同类型的图形。本文的 echart 代码都是在 Echarts 官网示例里面翻的。

5. 本文的 python 代码都是描述需求后让 copilot 写的。
