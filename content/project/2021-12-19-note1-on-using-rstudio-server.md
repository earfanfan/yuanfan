---
title: 使用RStudio Server笔记之安装R包
author: yuanfan
date: '2021-12-19'
slug: note1-on-using-rstudio-server
categories:
  - R
tags:
  - R
draft: no
---



<!--more-->

现在服务器上已经装好 RStudio Server 了[^1]，但是由于不能连上外网，所以安装R包的步骤略有一些复杂。总的来说，有三步：

+ 第一步，在本地下载R包，比如我是放到'D:/R/R-install'目录下。

+ 第二步，把本地下载的R包挪到服务器的指定目录下。

+ 第三部，在服务器上安装R包。

## 本地下载 R 包

在刚装好的 RStudio Server 上的菜单栏单击`File`->`New File`->`R Markdown`会卡一下，然后提示有好几个包需要安装。于是先在本地用 R 下载这些包，只需下载一个包的写法类似，如`myPackages <- c("cluster")`。

```r
getPackages <- function(packs) {
  packages <- unlist(
    tools::package_dependencies(
      packs,
      available.packages(),
      which = c("Depends", "Imports"),
      recursive = TRUE
    )
  )
  packages <- union(packs, packages)
  packages
}

#这里写入需要下载的包的名字
myPackages <-
  c("evaluate",
    "highr",
    "knitr",
    "markdown",
    "rmarkdown",
    "tinytex",
    "xfun")

packages <- getPackages(myPackages)

download.packages(packages, destdir = "D:/R/R-install", type = "source")
```

## 将本地下载的 R 包文件放到服务器上

我对 Linux 不熟，对 Shell 也不熟，所以我转移 R 包是这么干的：进入 Xshell，写`cd /home/package/R-4.0.3/source/`命令进入'source'文件夹（存放待安装 R 包的地方），打开 Xftp 把需要装的R包手动拖过去。

## 安装R包

在服务器上先放好用于安装 R 包的 R 脚本，如'install_Rpkg.R'。写`cd /home/package/R-4.0.3/R_scripts/`进入'R_scripts'文件夹（存放R脚本的地方），在这个目录下执行`../bin/Rscript install_Rpkg.R evaluate highr knitr markdown rmarkdown tinytex xfun`来安装这些R包。这里注意多个包的名字中间要用空格隔开，只装一个包的写法类似，如`../bin/Rscript install_Rpkg.R cluster`。

'install_Rpkg.R'中的内容如下。

```r
library(tools)
myPackages = commandArgs(T)

if (length(myPackages) == 0) {
  cat("Usage: Rscript install_Rpkg.R package1 package2 package3 ...")
  cat("\n")
  quit("no")
}

path <- "/home/package/R-4.0.3/source"
write_PACKAGES(path, type = "source")
install.packages(myPackages,
                 contriburl = paste("file:", path, sep = ''),
                 type = "source")
```

安装成功了的话，Xshell 的窗口会有提示。接下来就可以在 RStudio Server 里面新建 R Markdown 文档了。

## 安装 R 包失败时

安装过程中，如果出现'had non-zero exit status'错误或者版本对不上的错误，重新安装即可。

+ 单个包下载路径：<https://cran.r-project.org/src/contrib/Archive/> 。
+ 包依赖查询路径：比如查'data.table'包，就是<https://cran.r-project.org/web/packages/data.table/>。
+ R 语言源码包：比如查 R3.X 版本，就是<https://cran.r-project.org/src/base/R-3/>，查 R4.X 版本，就是<https://cran.r-project.org/src/base/R-4/>。

## 在 RStudio Server 上 knit

建好 R Markdown 文档了，直接单击 knit 按钮会报错，大概是'no png support in this R'、'failed to load cairo DLL Execution halted'之类的。要是这里傻乎乎地以为 cairo 是个 R 包就会大错特错，一番折腾后会发现这里缺少的 cairo 是 Linux 系统包，安装命令应该是`sudo yum install cairo-devel`。

装好后，接下来在 R Markdown 文档的 setup 代码段里加上`dev="CairoPNG"`参数就能正常 knit 了。

````
```{r setup, include=TRUE,dev="CairoPNG"}
knitr::opts_chunk$set(echo = TRUE,dev="CairoPNG")
```
````

## 在 Linux 的 R 环境中 knit

进入服务器上面安装好的 R 的 bin 目录下，写`cd /home/package/R-4.0.3/bin/`，再写`./R`就能进入 R 环境，然后用`rmarkdown::render`函数来实现。

```r
Sys.setenv(RSTUDIO_PANDOC="/usr/lib/rstudio-server/bin/pandoc")

rmarkdown::render('/home/package/R-4.0.3/RData/RMD/input.Rmd',output_file='/home/package/R-4.0.3/RData/RMD/output.html')
```

[^1]:本文大多数内容都是之前在同事帮助下完成的，但这位同事几个月前离职了，以后服务器上的东西只能自己瞎鼓捣了。这位同事人很好，共事的几年里虽也无意中坑过我几回，但帮助我的时候占多数。记得有一次下班后我们一起走去地铁站，天空丢了一些毛毛细雨下来，他带了伞而我没带，他问我下了地铁还要多久才能回家，我说走的话要走十分钟，于是他就把他的伞给我了。希望好人一生平安。
