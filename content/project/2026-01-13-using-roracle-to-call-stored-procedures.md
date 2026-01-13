---
title: 使用 ROracle 调用存储过程
author: yuanfan
date: 2026-01-13T20:19:54+0800
slug: Using ROracle to call stored procedures
categories:
  - R
tags:
  - R
draft: no
---

<!--more-->

# 安装 ROracle 包

# 服务器离线安装步骤

在服务器上离线安装 ROracle 包，如果只是下载 ROracle_1.5-1.tar.gz 然后直接装会报下面的错误。这是因为 ROracle 的编译步骤默认从 Oracle 官网下载所需客户端。

```
checking downloading instantclient-sdk-linuxx64.zip... 
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
  curl: (7) Failed to connect to download.oracle.com port 443: No route to host
configure: error: Failed to download instantclient-sdk-linuxx64.zip
ERROR: configuration failed for package ‘ROracle’
```

于是乎能正确安装的步骤应如下：

1. 从[官网](https://www.oracle.com/database/technologies/instant-client/linux-x86-64-downloads.html)下载版本对应的 basic 和 sdk 包，挪到服务器相关目录下并解压。这里要对应的版本信息有二：其一，服务器版本；其二，要连接的 ORACLE 数据库版本。官网写明安装 ORACLE 19的话也可以连 ORACLE 11，从 ORACLE 21 开始要求是 RedHat 9，综合考虑选了以下版本。

```bash
cd /xxxx/R/Oracle/

unzip instantclient-basic-linux.x64-19.29*.zip 
unzip instantclient-sdk-linux.x64-19.29*.zip
```
2. 配置环境变量。确认解压后的文件夹目录中能分别找到libclntsh.so和oci.h。执行`vim ~/.bashrc`打开配置文件，加入下面的内容，按 Esc 键加上`:wq`保存，再执行`source ~/.bashrc`使之生效。如果配置正常完成，再执行 `echo $LD_LIBRARY_PATH` 可以看到输出所在路径`/xxxx/R/Oracle/instantclient_19_29`。

```bash
# 确认文件存在
ls /xxxx/R/Oracle/instantclient_19_29/libclntsh.so
ls /xxxx/R/Oracle/instantclient_19_29/sdk/include/oci.h

# 以下加到配置文件中
export OCI_LIB=/xxxx/R/Oracle/instantclient_19_29
export OCI_INC=/xxxx/R/Oracle/instantclient_19_29/sdk/include
export LD_LIBRARY_PATH=$OCI_LIB:$LD_LIBRARY_PATH
```

3. 重启 R，在 R 中执行以下安装脚本。

```r
install.packages(
  "/xxxx/R/InstallPakages/source/ROracle_1.5-1.tar.gz",
  repos = NULL,
  type = "source",
  configure.args = c(
    paste0("--with-oci-lib=", "/xxxx/R/Oracle/instantclient_19_29"),
    paste0("--with-oci-inc=", "/xxxx/R/Oracle/instantclient_19_29/sdk/include")
  )
)
```

## 踩到的坑

在 RStudio Server 中加载 ROracle 包，随后在执行`drv <- dbDriver("Oracle")`时报出下面的错误，表明 rstudio 没有找到正确的路径。

>Error in .oci.Driver(.oci.drv(), interruptible = interruptible, unicode_as_utf8 = unicode_as_utf8,  : 
  Cannot locate a 64-bit Oracle Client library: "libnnz19.so: cannot open shared object file: No such file or directory". See  for help

执行`sudo systemctl edit rstudio-server.service`打开 rstudio 的配置文件，加入下面的内容，如果打开的是 nano 编辑器，那么 ctrl+o 保存、ctrl+x 退出。最后执行`sudo systemctl daemon-reload`使配置生效，再执行`sudo systemctl restart rstudio-server`重启服务。

```bash
[Service]
Environment="LD_LIBRARY_PATH=/xxxx/R/Oracle/instantclient_19_29"
Environment="OCI_LIB=/xxxx/R/Oracle/instantclient_19_29"
Environment="OCI_INC=/xxxx/R/Oracle/instantclient_19_29/sdk/include"
```

再次执行`drv <- dbDriver("Oracle")`，又报出下面的错误，表明 Linux 系统缺少 libnsl 包。

>Error in .oci.Driver(.oci.drv(), interruptible = interruptible, unicode_as_utf8 = unicode_as_utf8,  : 
  Cannot locate a 64-bit Oracle Client library: "libnsl.so.1: cannot open shared object file: No such file or directory". See  for help
  
执行`sudo yum install libnsl`安装上 libnsl 包，再执行`ls /usr/lib64/libnsl.so*`检查一遍路径是否正常输出。最后再重启服务，终于能够正常使用。

# 使用 ROracle 

## 连接数据库

提前查清楚两处细节。

1. 在要连接的 ORACLE 数据库 SQL 窗口执行以下语句，提前查一下字符集，一般默认是 AL32UTF8。再在 R 中执行`Sys.getenv("NLS_LANG")`，如果得到空，那么需要在连数据库之前加下初始设置，不然可能 R 中查到的数据会出现中文乱码。

```sql
SELECT * FROM NLS_DATABASE_PARAMETERS WHERE PARAMETER = 'NLS_CHARACTERSET';
```

2. 找到数据库的 IP 地址和服务名，就是下面的`HOST = xx.xx.1.128`和`SERVICE_NAME = service_name`这两个部分。

```
database1 = 
 (DESCRIPTION = 
   (ADDRESS = (PROTOCOL = TCP)(HOST = xx.xx.1.128)(PORT = 1521))
   (CONNECT_DATA = 
     (SERVICE = DEDTCATED)
     (SERVICE_NAME = service_name)
    )
  )
```

随后可以尝试连接数据库。

```r
# 加上初始设置，从 ORACLE 过来的数据不会出现中文乱码
Sys.setenv(NLS_LANG = "AMERICAN_AMERICA.AL32UTF8")

library(DBI)
library(ROracle)

# 连接数据库
drv <- dbDriver("Oracle")
con <- dbConnect(drv,
                 username = "username",
                 password = "password",
                 dbname = "//xx.xx.1.128:1521/service_name")

# 查看数据库中的表名称
#dbListTables(con)

# 注意：查询 sql 末尾不用加分号（;）
data_sql <- "select * from table_A"
# 直接查询数据到 R 中
res <- dbGetQuery(con, data_sql)

# 只发送 sql ，需要手动抓取结果，适合大批量数据
# res <- dbSendQuery(con, "select * from table_A")
# fetch(res)
# data <- fetch(res, n = 5)
# dbClearResult(res)

# 断开数据库连接
dbDisconnect(con)
# 释放驱动对象
dbUnloadDriver(drv)
```

## 调用 Oracle 存储过程

现在需求有三步：

1. 执行存储过程`pkg_claim_anti_fraud_add.p011_prepare_wait_match_one`，一个入参（case_no），一个出参，即可能会报出的错误。
2. 执行R脚本`antifraud_detection_one_case.R`，使用脚本中的`detect_one_case()`函数来得到每一个入参（case_no）的结果。
3. 执行存储过程`pkg_claim_anti_fraud_add.p014_match_one_result_list`，入参、出参与第一步相同。

使用 ROracle 调用存储过程非常简单，用 R base 中的`sprintf()`函数把参数拼接到 SQL 里面，再用 DBI 包中的`dbExecute()`直接执行即可。

```r
source("/xxxx/R/Rscripts/antifraud_detection_one_case.R")

# 三个步骤封装到一个函数里
run_one_case <- function(case_no, con) {
  # 拼接 SQL
  sql1 <- sprintf("
    DECLARE
      v_out VARCHAR2(100);
    BEGIN
      pkg_claim_anti_fraud_add.p011_prepare_wait_match_one(
          p_case_no => '%s',
          p_category_name => '意外医疗',
          exec_result => v_out
      );
      DBMS_OUTPUT.PUT_LINE(v_out);
    END;", case_no)

  sql2 <- sprintf("
    DECLARE
      v_out VARCHAR2(100);
    BEGIN
      pkg_claim_anti_fraud_add.p014_match_one_result_list(
          p_case_no => '%s',
          p_category_name => '意外医疗',
          exec_result => v_out
      );
      DBMS_OUTPUT.PUT_LINE(v_out);
    END;", case_no)

  # 第一步：执行 P011
  dbExecute(con, sql1)

  # 第二步：调用 R 函数
  detect_one_case(case_no, '意外医疗')

  # 第三步：执行 P014
  dbExecute(con, sql2)
}

case_list <- res$CASE_NO
# 循环调用
for (i in seq_along(case_list)) {
  cat("正在处理第", i, "个案件：", case_list[i], "\n")
  run_one_case(case_list[i], con)
}
```

# DBI 和 ROracle/RJDBC 的关系？ROracle 和 RJDBC 的区别？ 

`R -- DBI -- ROracle/RJDBC -- 数据库`

