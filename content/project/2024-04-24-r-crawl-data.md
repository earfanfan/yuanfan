---
title: 使用基础 R 抓取网页数据
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

本文主要参考了一篇统计之都主站的文章——[数据通灵术之爬虫技巧](https://cosx.org/2017/08/web-scrap-tools/)。所选案例为抓取中国政府网的政策文件名称和日期。

# 静态网页抓取数据

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

# 动态网页抓取数据

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

## 抓取一个页面

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

## 批量抓取全部页面

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
