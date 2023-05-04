---
title: 使用RStudio Server笔记之连接数据库
author: yuanfan
date: '2021-12-21'
slug: note2-on-using-rstudio-server
categories:
  - R
tags:
  - R
draft: no
---



<!--more-->

在服务器的 R 环境中已经安装好了 RJDBC 及其依赖包的情况下，（踩过坑以后）连接数据库很容易，一共分三步。

+ 第一步，先在 RStudio Server 的 Console 窗口中输入`getwd()`得到工作目录，把 ORACLE 版本对应的jar包放到该工作目录下。

+ 第二步，找到 Oracle 的 tnsnames.ora 文件，再找到想要连接的数据库的IP地址和端口（一般默认为1521）。

+ 第三步，在 RStudio Server 中写下面的代码，就能连上数据库了。

```r
###############################################################
##一定要在加载包之前运行下面的条件，改变数据能占用的Java内存空间大小
##1024不够的话，改成8192  
###############################################################
options(java.parameters = "-Xmx1024m")   
library(DBI)
library(rJava)
library(RJDBC)

drv <-
  JDBC("oracle.jdbc.driver.OracleDriver",
       "/home/hadoop/ojdbc6-11.2.0.1.0.jar")
conn <-
  dbConnect(drv,
            "jdbc:oracle:thin:@IP地址:端口:数据库名称",
            "账户名称",
            "密码")

data = dbGetQuery(conn, "select * from table")

#dbRemoveTable(conn, "temp_2021") 
#相当于在数据库中执行 truncate table temp_2021;
#dbWriteTable(conn, "temp_2021", data, overwrite  = TRUE)
#相当于把 R 环境中的 data 数据集写入数据库中的 temp_2021 表中
dbDisconnect(conn)
```

日常工作中接触到的数据库有三种：Oracle 、 MySQL、 Impala（查询），但能在 RStudio Server 中连上 Oracle 数据库对我来说就够用了，其他的以后有空再摸索吧。
