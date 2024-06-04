---
title: 使用 R 抓取网页数据--基于国务院政策文件库
author: yuanfan
date: 2024-04-24T22:16:16+0800
slug: r crawl data
categories:
  - R
tags:
  - R
draft: no
---

<!--more-->

本文主要参考了一篇统计之都主站的文章——[数据通灵术之爬虫技巧](https://cosx.org/2017/08/web-scrap-tools/)。所选案例为抓取中国政府网的政策文件名称和日期，以及文件的文本内容。

# 一、抓取政策文件的标题和日期

## 1.1. 静态网页抓取数据

进入此网页<https://www.gov.cn/zhengce/zuixin/>，可以看到页面下方显示当前有91页内容，第91页最后一个政策的日期是2016年1月，说明这里只能查到2016年及以后公布的政策文件。试着选择不同页数，会发现网页地址有变化，页面上可选的1-91页对应的网址后缀是`home_0.htm`到`home_90.htm`。

在浏览器中任选一页，打开“开发者模式”（PS 我使用的电脑是 Win11系统，使用的浏览器是 Microsoft Edge），用鼠标单击“元素选择器”（开发者工具最左边带箭头标记的图案），接着再用鼠标选择想要抓去的元素，会看到在“元素”中有如下内容，而每一组`<li>...</li>`点开都能看到想要抓取的政策文件的名称和日期。

```html
<li>
  ::marker
  <h4>
   <a href="../202404/content_6946880.htm" target="_blank"> 中共中央办公厅 国务院办公厅关于健全新时代志愿服务体系的意见 </a>
   <span class="date"> 2024-04-22 </span>
  </h4>
</li> 
```

```r
# 初始化一个空的数据框来存储所有页面的数据
all_data <- data.frame()

# 循环遍历每一页
for (i in 0:90) {
  # 下载一个页面的网页源代码
  url <- paste0('https://www.gov.cn/zhengce/zuixin/home_', i, '.htm')
  html_lines = readLines(url)
  doc = paste0(html_lines, collapse = '')
  
  # 提取政策名称，匹配包含 target="_blank" 字符的行
  title_lines = grep('target="_blank"', html_lines, value = T)
  # 用正则抽取>字符和<字符中间的字符
  titles = gsub('.*>(.*?)<.*', '\\1', title_lines, perl = T)
  
  # 提取政策对应的日期
  date_lines = grep('class="date"', html_lines, value = T)
  dates = gsub('.*>(.*?)<.*', '\\1', date_lines, perl = T)
  
  # 将政策名称和日期拼接到一起
  data <- data.frame(cbind(titles[8:27], dates))
  
  # 将每一页的数据添加到所有数据中
  all_data <- rbind(all_data, data)
}

all_data <- head(all_data, -7)
colnames(all_data)[1] <- "name"

# 导出数据
data.table::fwrite(all_data, '~/gov_zhengce.csv')
```

## 1.2. 动态网页抓取数据

要想查看全部政策文件的名称和日期，需要进入国务院政策文件库，即<https://sousuo.www.gov.cn/zcwjk/policyRetrieval>。打开网页，单击搜索按钮，可以看到一共有国务院文件5956条、国务院部门文件11005条、国务院公报13968条。这可能是个动态网页，因为不管跳转到第几页，网页地址并没有改变。此时依然需要使用浏览器的“开发者模式”，来找到想要抓取的数据究竟隐藏在哪里。

打开“开发者模式”，选择开发者工具中的“网络（Network）”，操作原来的网页比如单击搜索后选择新的一页，然后逐一查看出现的每个“名称（Name）”对应的“响应（Response）”中的内容（可以略过一些图片和 css 设置），看看想要抓取的文件名称等内容在哪里。

当找到含有所需抓取内容的“名称（Name）”，复制链接地址并粘贴出来，比较一下选择不同的页数和区分发布机构后的地址有何规律。

+ 不区分发布机构时，在`<https://sousuo.www.gov.cn/search-gov/data>`后面的内容是`?t=zhengcelibrary_gw_bm_gb`。而区分发布机构后，国务院文件对应的内容是`?t=zhengcelibrary_gw`，国务院部门文件对应的内容是`?t=zhengcelibrary_bm`，国务院公报对应的内容是`?t=zhengcelibrary_gb`。这里很容易猜到，gw 是国务二字的首字母，bm 是部门二字的首字母，gb 是公报二字的首字母。

+ 对比第1页和第2794页的地址，前者是`p=1&n=5`，后者是`p=2794&n=5`。猜测 p 对应的是页数，而 n 对应的是一页展示的条目数。

```
# 高级检索，不区分发布机构
# 第1页
https://sousuo.www.gov.cn/search-gov/data?t=zhengcelibrary_gw_bm_gb&q=&timetype=&mintime=&maxtime=&sort=score&sortType=1&searchfield=title:content:summary&pcodeJiguan=&childtype=&subchildtype=&tsbq=&pubtimeyear=&puborg=&pcodeYear=&pcodeNum=&filetype=&p=1&n=5&inpro=&bmfl=&dup=&orpro=&bmpubyear=
  
# 第2794页
https://sousuo.www.gov.cn/search-gov/data?t=zhengcelibrary_gw_bm_gb&q=&timetype=&mintime=&maxtime=&sort=score&sortType=1&searchfield=title:content:summary&pcodeJiguan=&childtype=&subchildtype=&tsbq=&pubtimeyear=&puborg=&pcodeYear=&pcodeNum=&filetype=&p=2794&n=5&inpro=&bmfl=&dup=&orpro=&bmpubyear=
  
# 只筛选国务院文件，每页5条记录，共1192页，下面为第2页
https://sousuo.www.gov.cn/search-gov/data?t=zhengcelibrary_gw&q=&timetype=&mintime=&maxtime=&sort=score&sortType=1&searchfield=title:content:summary&pcodeJiguan=&childtype=&subchildtype=&tsbq=&pubtimeyear=&puborg=&pcodeYear=&pcodeNum=&filetype=&p=2&n=5&inpro=&bmfl=&dup=&orpro=&bmpubyear= 
  
# 只筛选国务院部门文件，每页5条记录，共2202页，下面为第1页
https://sousuo.www.gov.cn/search-gov/data?t=zhengcelibrary_bm&q=&timetype=&mintime=&maxtime=&sort=score&sortType=1&searchfield=title:content:summary&pcodeJiguan=&childtype=&subchildtype=&tsbq=&pubtimeyear=&puborg=&pcodeYear=&pcodeNum=&filetype=&p=1&n=5&inpro=&bmfl=&dup=&orpro=&bmpubyear=
  
# 只筛选国务院公报，每页5条记录，共2794条，下面为第1页
https://sousuo.www.gov.cn/search-gov/data?t=zhengcelibrary_gb&q=&timetype=&mintime=&maxtime=&sort=score&sortType=1&searchfield=title:content:summary&pcodeJiguan=&childtype=&subchildtype=&tsbq=&pubtimeyear=&puborg=&pcodeYear=&pcodeNum=&filetype=&p=1&n=5&inpro=&bmfl=&dup=&orpro=&bmpubyear=
```

如果一次只抓取1页默认的5条数据，那么抓取效率显然会很低，试着直接将以上链接地址复制粘贴到浏览器中打开，发现将地址中的 n 从默认的5修改为10时能正常打开，若将 n 修改为100甚至1000时也能正常打开，但是若改为5000就会报错。那么后续抓取数据时，可以考虑按1页1000条来操作。

### 1.2.1. 抓取一个页面

为了找到想要抓取的数据所在位置，先只抓取一个页面的内容。由于抓取到的数据全是用大括号括起来的 json 字符串，需要使用 jsonlite 包来帮助解析数据。

```r
url <-
  'https://sousuo.www.gov.cn/search-gov/data?t=zhengcelibrary_gw_bm_gb&q=&timetype=&mintime=&maxtime=&sort=score&sortType=1&searchfield=title:content:summary&pcodeJiguan=&childtype=&subchildtype=&tsbq=&pubtimeyear=&puborg=&pcodeYear=&pcodeNum=&filetype=&p=1&n=5&inpro=&bmfl=&dup=&orpro=&bmpubyear='

html_lines = readLines(url)
doc = paste0(html_lines, collapse = '')

# 将 doc 中的数据写入一个临时空文件中
tmp_file <- tempfile()
writeLines(doc, tmp_file)

# 使用 stream_in() 函数读取临时文件
data_list <- jsonlite::stream_in(file(tmp_file))
```

但是解析后的列表内容繁杂，要想找到需要的数据，可以选择逐层查看列表中的元素，或者直接打开链接地址观察一下所需数据的格式规律。如下，可以看到所需数据存在一对`{}`里面，再往上一层是 listVO 用`[]`符号囊括了所需数据，继续找更上层，发现依然是用`{`囊括各项元素。那么，再往上一层是 gongwen，再往上一层是 catMap，再往上一层是 searchVO。

```js
{
    "code": 200,
    "msg": "操作成功",
    "data": null,
    "searchVO": {
    ...
    "sourcemap": null,
        "listVO": null,
        "catMap": {
            "gongwen": {
                "totalCount": 5956,
                "catName": "gongwen",
                "currentNum": 5,
                "listVO": [
                    {
                        "piclinksurl": "",
                        "code": "",
                        "pcode": "国发〔2024〕10号",
                        "source": "",
                        "title": "国务院关于加强监管防范风险推动资本市场高质量发展的若干意见",
                        "totalCount": 0,
                        "pubtimeStr": "2024.04.12",
    
    ...
```

按图索骥就可以依次得到分不同部门的数据。

```r
# 国务院文件
data_list$searchVO$catMap$gongwen$listVO

# 国务院部门文件
data_list$searchVO$catMap$bumenfile$listVO

# 国务院公报
data_list$searchVO$catMap$gongbao$listVO
```

### 1.2.2. 批量抓取全部页面

按照每页抓取1000条数据，一共3万多条数据，设置抓取31次。

```r
# 设置要抓取的页面数量
num_pages <- 31

# 初始化一个空列表来存储所有页面的数据
all_data <- list()

for (i in 1:num_pages) {
  # 更新 url 中的 p 值，n=1000
  url <- paste0(
    'https://sousuo.www.gov.cn/search-gov/data?t=zhengcelibrary_gw_bm_gb&q=&timetype=&mintime=&maxtime=&sort=score&sortType=1&searchfield=title:content:summary&pcodeJiguan=&childtype=&subchildtype=&tsbq=&pubtimeyear=&puborg=&pcodeYear=&pcodeNum=&filetype=&p=', 
    i, 
    '&n=1000&inpro=&bmfl=&dup=&orpro=&bmpubyear='
  )

  # 读取页面内容
  html_lines = readLines(url)
  doc = paste0(html_lines, collapse = '')

  # 将 doc 中的数据写入一个临时空文件中
  tmp_file <- tempfile()
  writeLines(doc, tmp_file)

  # 使用 stream_in() 函数读取临时文件
  data_list <- jsonlite::stream_in(file(tmp_file))

  # 将每个页面的数据添加到all_data列表中
  all_data[[i]] <- data_list
}

# 使用 lapply 函数将每个列表元素转换为数据框
gongwen <-
  lapply(all_data, function(x)
    as.data.frame(x$searchVO$catMap$gongwen$listVO))
gongwen <- do.call(rbind, gongwen)

bumenfile <-
  lapply(all_data, function(x)
    as.data.frame(x$searchVO$catMap$bumenfile$listVO))
bumenfile <- do.call(rbind, bumenfile)

gongbao <-
  lapply(all_data, function(x)
    as.data.frame(x$searchVO$catMap$gongbao$listVO))
gongbao <- do.call(rbind, gongbao)

# 转换为 data.table 格式
data.table::setDT(gongwen)
data.table::setDT(bumenfile)
data.table::setDT(gongbao)

# 国务院公报相比其他缺少两个字段
gongbao[, ':='(childtype = NA, puborg = NA)]

# 增加 label 字段用于区分部门
gongwen$label <- '国务院文件'
bumenfile$label <- '国务院部门文件'
gongbao$label <- '国务院公报'

char <- c('pcode','title','pubtimeStr','id','ptime','summary','index','url','pubtime','childtype','puborg','label')

# 合并所有数据
data <- rbind(gongwen[,..char], bumenfile[,..char], gongbao[,..char])

# 将时间戳转换为日期时间格式，ptime 对应成文日期
data$ptime_date <-
  as.POSIXct(data$ptime / 1000, origin = "1970-01-01", tz = "GMT")
# 转换为北京时间
data$ptime_date<-format(data$ptime_date, tz = "Asia/Shanghai")

# pubtime 对应发布日期
data$pubtime_date <-
  as.POSIXct(data$pubtime / 1000, origin = "1970-01-01", tz = "GMT")
data$pubtime_date <- format(data$pubtime_date, tz = "Asia/Shanghai")

# 导出保存
data.table::fwrite(data,'~/gov_zhengce_all.csv')
```

# 二、抓取政策文件的文本内容

前面批量抓取政策文件的标题时，也得到了每个文件的网页链接（url），据此可进一步将政策文件的文本内容也抓取下来。一切正式开始之前，需要先摸清楚文本嵌入网页源代码中的基本模式。

在浏览器中分别打开几个国务院文件、国务院部门文件、国务院公报的页面，可以观察到前两者和后一者之间有些区别：其一，前两者的网页链接（url）较为相似都是<https://www.gov.cn/zhengce/zhengceku/>，而国务院公报的网页链接（url）是<https://www.gov.cn/gongbao/>；其二，前两者的网页中，在文件的文本内容之前会有一些主题分类、发文机关之类的信息，而国务院公报的网页中没有这些信息。这说明，整个政策文件库中的文件不仅横跨多个年份，并且可能需要用不同的模式去匹配和抓取想要的文本内容。

抓取网页文本一共只有三个步骤：

1. 读取网页源代码，其中包含 HTML 元素、CSS 样式、网页文本。
2. 找到想要提取的文本所在的位置。
3. 提取文本。

其中第2步最关键，使用浏览器打开网页后，再打开“开发者模式”，用元素选择器选择网页文本中的一个自然段落，右键“复制”可以分别“复制 outerHTML”和“复制 XPath”。以下是三个不同的网页链接（url），分别复制得到的内容，从中可以总结出两个找到文本位置的方法。

+ 第一种，根据 CSS 样式匹配。由于文本被包裹在`<p>...</p>`之间，而`<p>`是一种 HTML 元素，表示一个文本段落，通常可以对每个段落设置不同的 CSS 样式。观察政策文件的文本段落样式，发现通常会设置`text-indent: 2em;`，即首行缩进。那么可以使用正则表达式匹配`style=""`中包含`text-indent: 2em;`，即按`style=".*text-indent: 2em;.*"`（.*代表匹配任意内容）的模式匹配所需文本。

+ 第二种，根据 XPath 匹配。比如一个文本段落的 XPath 是`//*[@id="UCAP-CONTENT"]/div[1]/p[12]`，那么查找整个文件所有文本段落应该是更上一级路径，即 XPath 应该是`//*[@id="UCAP-CONTENT"]/div[1]`。下面有三种不同的 XPath，分别是`//*[@id="UCAP-CONTENT"]/div[1]`、`//*[@id="UCAP-CONTENT"]`、`//*[@id="UCAP-CONTENT"]/div`。

```html
<!-- url:https://www.gov.cn/gongbao/2024/issue_11286/202404/content_6945590.html --->
<!-- 复制 outerHTML -->
<p data-index="-2" style="text-indent: 2em; margin-top: 2px; margin-bottom: 2px;">为了贯彻落实《国务院关于取消和调整一批罚款事项的决定》（国发〔2023〕20号），进一步优化营商环境，工业和信息化部决定对2部规章部分条款予以修改。</p>

<!-- 复制 XPath -->
//*[@id="UCAP-CONTENT"]/div[1]/p[12]
```

```html
<!-- url:https://www.gov.cn/gongbao/content/2023/content_5754544.htm --->
<!-- 复制 outerHTML -->
<p align="" style="margin-top: 0px; margin-bottom: 0px; text-indent: 2em; text-align: justify; font-family: 宋体;">《北京证券交易所向不特定合格投资者公开发行股票注册管理办法》已经2023年2月17日中国证券监督管理委员会2023年第2次委务会议审议通过，现予公布，自公布之日起施行。</p>

<!-- 复制 XPath -->
//*[@id="UCAP-CONTENT"]/p[5]
```

```html
<!-- url:https://www.gov.cn/zhengce/zhengceku/202404/content_6947234.htm --->
<!-- 复制 outerHTML -->
<p style="text-indent: 2em;">为深入落实中央经济工作会议精神和党中央、国务院决策部署，进一步发挥海关信用管理职能作用，持续提升高级认证企业（AEO企业）获得感，更好服务外贸质升量稳，海关总署决定在原有管理措施基础上，向高级认证企业实施以下便利措施：</p>

<!-- 复制 XPath -->
//*[@id="UCAP-CONTENT"]/div/p[2]
```

## 2.1. 使用基础 R 抓取网页文本

使用基础 R 函数来抓取网页文本时，通常要使用正则表达式来提取文本。对于跨年份跨类型的政策文件库来说，有时候文本就被放在`<p>`元素中，有时候却又被放在`<p>`元素中包裹的`<span>`元素中。如果要写一个正则表达式，可以把几万个网页中所有文本提取出来，那么会不得不写成一种超级冗长的模式。

```r
# url1
url <- 'https://www.gov.cn/zhengce/zhengceku/202404/content_6947234.htm' 
# url2: <span> 中有文本
url <- 'https://www.gov.cn/gongbao/2023/issue_10826/202311/content_6915819.html' 
# url3: <a> 中有文本
url <- 'https://www.gov.cn/zhengce/zhengceku/202405/content_6948904.htm' 
# url4
url <- 'https://www.gov.cn/gongbao/content/2023/content_5754544.htm' 

# 1. 读取网页源代码
html_lines <- readLines(url)

# 2. 匹配文本位置
content_lines <- grep('data-index="-2"|style=".*text-indent: 2em;.*"',
                      html_lines,
                      value = T)

# 3. 使用正则表达式提取文本
# 适用于 url1-3
content <- gsub('<p[^>]*>(.*?)</p>', '\\1', content_lines[1], perl = T)
# 适用于 url4
content <- gsub('.*>(.*?)<.*', '\\1', content_lines, perl = T)

# 将所有段落拼接为一个长字符串
content <- paste(content,collapse = " ")
content
```

## 2.2. 使用 xml2 包抓取网页文本

翻查 xml2 包的[官方文档](https://xml2.r-lib.org/articles/modification.html)，原来可以用`xml_text()`函数直接把 HTML/XML 中的文本提取出来，不需要再琢磨写复杂的正则表达式。

```r
x <- read_xml("<p>This is some <b>text</b>. This is more.</p>")
xml_text(x)
#> [1] "This is some text. This is more."
```

```r
library(xml2)

# 1. 读取网页源代码
html_lines <- read_html(url)

# 2. 使用 xml_find_all 函数查找文本位置
# 用 CSS 样式来查找
content_lines <- xml_find_all(
  html_lines,
  '//p[@data-index="-2"] | //p[contains(@style, "text-indent: 2em")] | //span[contains(@style, "text-indent:")]'
)
# 用 Xpath 来查找
# content_lines <- xml_find_all(html_lines, '//*[@id="UCAP-CONTENT"]/div[1] | //*[@id="UCAP-CONTENT"]|//*[@id="UCAP-CONTENT"]/div')

# 3. 使用 xml_text 提取文本段落
content <- xml_text(content_lines)

# 将所有段落拼接为一个长字符串
content <- paste(unique(gsub("\n| ","",content)), collapse = " ")
```

## 2.3. 批量提取网页文本

批量提取往往不会一次就成功，需要不断去核查网页链接（url）提取出来的文本为空的原因，大多是因为在查找那一步总结出来的模式还不齐全。需要注意的是用 CSS 样式和用 XPath 去查找文本是有区别的，后者往往能查找到更多内容，但不一定都是想要提取出来的。

```r
library(data.table)
library(xml2)

data <- fread('~/gov_zhengce_all.csv')

# 把根据 URL 提取网页文本封装成函数
get_content <- function(url) {
  html_lines <- read_html(url)
  content_lines <- xml_find_all(
    html_lines,
    '//p[@data-index="-2"] | //p[contains(@style, "text-indent: 2em")] | //span[contains(@style, "text-indent:")]'
  )
  # 检查content_lines是否为空
  if (length(content_lines) == 0) {
    return("")  # 返回一个空字符串
  }
  content <- xml_text(content_lines)
  content <- paste(unique(gsub("\n| ", "", content)), collapse = " ")
  return(content)
}

batch_size <- 1000 # 指定每批次数量

num_batches <- ceiling(nrow(data) / batch_size)  # 计算批次数量

for (i in 1:num_batches) {
  start_row <- (i - 1) * batch_size + 1
  end_row <- min(i * batch_size, nrow(data))
  
  data[start_row:end_row, ':='(content = unlist(lapply(url, get_content)))]
  Sys.sleep(180)  # 暂停3分钟
}

fwrite(data, '~/gov_zhengce_content.csv')
```

# 三、批量下载国务院公报1954-1999

政策文件库里只有1999年以后的电子版，[历史公报](https://www.gov.cn/zhengce/gongbao/guowuyuan1954_1999/)只上传了 PDF 文件。

```r
# 加载httr包
library(httr)

# 定义保存PDF的本地路径
path <- "~/国务院公报/"

# 定义年份和编号
years <- c(1954:1966,1980:1999)
nums <- list(
  c(195401:195403),
  c(195501:195523),
  c(195601:195647),
  c(195701:195754),
  c(195801:195837),
  c(195901:195930),
  c(196001:196036),
  c(196101:196119),
  c(196201:196215),
  c(196301:196324),
  c(196401:196418),
  c(196501:196516),
  c(196601:196605),
  c(198001:198020),
  c(198101:198127),
  c(198201:198221),
  c(198301:198326),
  c(198401:198431),
  c(198501:198536),
  c(198601:198635),
  c(198701:198730),
  c(198801:198828),
  c(198901:198928), #198909
  c(199001:199030),
  c(199101:199146),
  c(199201:199233),
  c(199301:199331),
  c(199401:199432),
  c(199501:199533),
  c(199601:199638),
  c(199701:199740),
  c(199801:199835),
  c(199901:199936)
)

# 循环下载文件
for (j in 1:length(years)) {
  for (i in nums[[j]]) {
    url <- paste0("https://www.gov.cn/gongbao/shuju/",
                  years[j],
                  "/gwyb",
                  i,
                  ".pdf")
    destfile <- paste0(path, "gwyb", i, ".pdf")
    GET(url, write_disk(destfile, overwrite = TRUE))
  }
}
```
