---
title: 使用RJDBC包连接Impala的笔记
author: yuanfan
date: 2022-03-17T09:48:38+0800
slug: rjdbc-impala
categories:
  - R
tags:
  - R
draft: no
---

<font face="微软雅黑">

<!--more-->

现在服务器上的 R 能连接 ORACLE 数据库，但是要分析的数据存储在 Hadoop 上面。为了把数据导入到 RStudio Server 上面进行分析，可以这么干：

+ 登录 HUE 网址，在 Impala 的查询窗口写 SQL，然后将执行得到的数据下载下来，但不知为何被限定了最多只能导出100万行数据。

+ 在上一步的基础上先建个临时表，然后登上服务器使用 Impala shell 下载全量数据，比如`$ impala-shell -q "select * from kudu.tmp_20220315" -B --output_delimiter="," --print_header -o /home/hadoop/data/output.csv`，但是 RStudio Server 在另一台服务器上面，要分析数据的话还得把下载下来的csv文件从一台服务器上面弄到另一台服务器上面去。

+ 以上解决方法实施起来很简单，但是不如花点时间研究下怎么在 RStudio Server 上面直接连接 Impala 。

一般使用 RJDBC 包连接数据库都会需要有 JDBC 驱动的 jar 包，可以去网上找对应版本下载，也可以从服务器上已经安装好的 Hadoop 目录下面找。笔者瞎碰乱试出来的办法就是，登录服务器，输入`$ hadoop version`查看 Hadoop 版本，在弹出来的信息最下面一条就是 jar 包文件所在目录。

>This command was run using /home/cloudera/parcels/CDH-6.3.2-1.cdh6.3.2.p0.1605554/jars/hadoop-common-3.0.0-cdh6.3.2.jar

在这个目录下翻到了**hive-jdbc-2.1.1-cdh6.3.2-standalone.jar**，挪到 RStudio Server 所在的那台服务器上面去，接着就能正常连上数据库了。

```r
options(java.parameters = "-Xmx8192m")
library(DBI)
library(rJava)
library(RJDBC)

#使用 Hive JDBC 驱动
drv <-
  JDBC(
    "org.apache.hive.jdbc.HiveDriver",
    "/home/hadoop/hive-jdbc-2.1.1-cdh6.3.2-standalone.jar"
  ) #jar包所在目录


conn <-
  dbConnect(drv,
            "jdbc:hive2://IP:21050/;auth=noSasl", #填IP地址，端口号默认填21050
            "xxx", #账户名
            "XXX") #密码

touch <- dbGetQuery(conn, "select * from kudu.tmp_20220315")  #查询数据

dbDisconnect(conn) #断开连接
```

默认端口号笔者在网上找了老半天，最后在<https://docs.cloudera.com/documentation/enterprise/5-12-x/topics/impala_jdbc.html#jdbc_connect__class_hive_driver>找到。

执行完`dbConnect()`会报下面这个错，但是依然能正常连接上，于是暂且先不管了。

>ERROR StatusLogger No log4j2 configuration file found. Using default configuration: logging only errors to the console. Set system property 'org.apache.logging.log4j.simplelog.StatusLogger.level' to TRACE to show Log4j2 internal initialization logging.