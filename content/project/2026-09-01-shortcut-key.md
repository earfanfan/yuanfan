---
title: 常用快捷键及 Linux 命令
author: yuanfan
date: 2026-09-01T21:21:54+0800
slug: shortcut-key
categories:
  - R
tags:
  - R
draft: false
---

<!--more-->

现在工作中会用到四种编程语言，分别是 R、Python、Shell、SQL，这就需要操作不同的 IDE 工具。关于操作系统也涉及三种，工作用本地电脑是 UOS，个人用电脑是 Windows，工作中经常需要登录 Linux 服务器。因为使用的工具太杂，许多时候快捷键会弄混（ps或者想不起来的时候干脆乱试一通），基于这个简单的原因，这里整理一些常用的快捷键和命令。

# 快捷键

## Rstudio

1. 执行代码块：`Ctrl + Enter`
2. 代码格式化：`Ctrl + Shift + A`
3. 加注释：`Ctrl + Shift + C`

## Pycharm

1. 分段执行： `shift + alt + E`
2. 代码格式化： `ctrl + alt + L`
3. 加注释：`ctrl + /`

## Jupyter notebook

1. 切换块（Cell）：选中后，按 `M` 切换为 markdown，`Y` 切换为代码；
2. 执行块（Cell）：选中后，按 `Enter` 键进行编辑；按 `Shift+Enter` 进行渲染或执行单元格代码;
3. 批量加注释：`Ctrl + /`
4. `!`是 Jupyter/IPython 的魔法语法，表示把后面的内容当作 shell 命令执行，而不是 Python 代码。

## UOS & Windows

|功能|UOS 系统快捷键|Windows 系统快捷键|
|:--:|:--:|:--:|
|呼出终端|`Ctrl + Alt + T`|`Windows + R`再输入 cmd|
|打开文件夹|`Windows + E`|`Windows + E`|
|回到桌面|`Windows + D`|`Windows + D`|
|临时锁屏|`Windows + L`|`Windows + L`|

对于 UOS、Windows 这种有图形界面的系统，`Ctrl + C`（复制）、`Ctrl + V`（粘贴）、`Ctrl + S`（保存）这三个是通用的。但是在 Shell 终端，`Ctrl + C`代表中断进程。

# 注释符号

|语言|单行注释符号|多行注释符号|
|:--:|:--:|:--:|
|R|`#`|每行行首加上`#`|
|Python|`#`|多行收尾加上`'''`或`"""`|
|SQL|`--`|多行首尾加上`/*`和`*/`|
|Shell|`#`|每行行首加上`#`，或者多行收尾加上`:'`和`'`|

# 常用 Linux 命令

Linux 命令给我的感觉就是操纵文件，不同权限操作不同目录下的文件，有时要查看、移动文件，有时要搜索、查找文件，有时压缩文件后移动，或是解压缩文件。

## 权限

+ `sudo` ：superuser do ,以超级管理员的权限去执行。

比如`sudo mv /data/datafile2/2454984/07  /data/datafile2/data/07`，我要把`/data/datafile2/2454984/07`目录下所有文件夹都转移到`/data/datafile2/data/07`目录下，此时我是用 hadoop 用户登录的，直接执行转移命令会报错“Permission denied”，加上 `sudo` 命令就不报错了。

+ `chown` ： change owner，修改文件/目录的所属用户。

比如`sudo chown -R hadoop:hadoop /data/datafile2/yf/ImageClass`，`/data/datafile2/yf/ImageClass`目录现在属于 root 用户，而使用 hadoop 用户时只能看到，没权限对文件做其他操作，这里将文件改到hadoop用户下，就可以后续进行解压、转移等操作了。

+ `chmod` ： change mode，改变r（read，读）、w（write，写）、x（execute，执行）的权限。

## 目录

+ `cd` ： change directory，切换目录。

比如`cd /home/yuanfan`，指切换到`/home/yuanfan`的目录下。

+ `mkdir` ： make directory，创建新目录。

比如 `mkdir /tmp/uv/env`，指创建`/tmp/uv/env`这个新目录，其实就是创建一个新文件夹。

+ `rmdir` ： remove  directory，删除目录。

+ `..` ： 比如`cd ..`指回到上一级目录，`cd ../..`指回到上两级目录。

+ `pwd` ： print working directory，打印工作目录。

## 查看

+ `ls`  ：list，列出当前目录下的文件清单。 

其中，加上`-l`（long）表示列出详细清单，而加上`-a`（all）表示列出隐藏文件，使用`ls -al`表示列出所有包含隐藏文件的详细清单。

+ `ll` ： 等同于`ls -l`。

```
[yuanfan@DCG1JNYC2-R730 ~]$ ll
total 16
-rw-rw-r--  1 yuanfan yuanfan  784 Jul 15 14:43 Dockerfile
drwxrwxrwx 13 yuanfan yuanfan 4096 Sep  1 13:58 ImageClass
-rw-rw-r--  1 yuanfan yuanfan 2381 Jul  7 17:08 index.html
[yuanfan@DCG1JNYC2-R730 ~]$ ls
Dockerfile  ImageClass  index.html
```

## 查找

+ `which` ：查找某命令或工具的可执行文件安装目录。

比如`which python`、`which nano vim`等。

+ `find` ： 在指定目录按照指定条件进行搜索。

比如`find /data/datafile2/yf/ImageClass/data -name "267532464.jpg"`，在指定目录`/data/datafile2/yf/ImageClass/data`按照文件名进行匹配。

+ `grep` ： global regular expression print，按照正则表达式进行匹配。

## 移动

+ `cp` ：copy ，复制。 

+ `mv` ：move ，移动。

+ `rm` ： remove，删除。

## 压缩和解压缩

+ `tar` ： tape archive，磁带归档，用来打包或解包的工具。

+ `gzip` ：GNU zip，单个文件的压缩。

以`tar -zxvf R-4.2.2.tar.gz`为例，表示把 R-4.2.2.tar.gz 这个文件解压到当前目录下。`.tar.gz`文件是指，多个文件用 tar打包成一个整体，然后用 gzip 压缩。因此使用对应的解压缩、解包的方式就是z（gzip，解压.gz文件）、x（extract，提取）、v（verbose，输出详细过程）、f（file，文件名）。

对应`tar -czvf R-4.2.2.tar.gz R-4.2.2`，指把 R-4.2.2 这个目录整个打包压缩，其中c（create，创建）表示打包。

+ `pigz` ：Parallel Implementation of GZIP，可以并行的 gzip，用于高效压缩或解压大量文件。

以`pigz -dc -p 35 ./04.tar.gz | tar -xvf - -C /data/datafile2/yf/ImageClass/data`为例，用`|`作为管道连接了解压和解包两个步骤。前半部分d（decompress，解压）、c（cat）、p（parallel，并行），合起来`-dc -p 35`就是用35个线程并行解压，解压后进入管道。后半部分加上的C（change directory）是指解包到指定目录下。

在实际工作中，用hadoop用户登录，压缩包04.tar.gz放在`/data/datafile1/images`目录下，解压后应该放到`/data/datafile2/yf/ImageClass/data`目录下，以下是三个步骤。

```bash
# 切换到压缩包所在目录
cd /data/datafile1/images

# 给当前用户赋权指定目录的更高权限
sudo chown -R hadoop:hadoop /data/datafile2/yf/ImageClass

# 并行解压到指定目录
pigz -dc -p 35 ./04.tar.gz | tar -xvf - -C /data/datafile2/yf/ImageClass/data
```

## 特殊符号 

+ `-`：单横线，通常作为命令的功能开关，比如`ls -l`、`tar -xvf`。  

+ `--`：双横线，通常写长选项，比如`gcc --version`表示查看 gcc 的版本。 

+ `./`：常用语执行当前目录下的脚本或程序，比如`./R`代表打开R程序，`./script.sh`代表执行这个.sh脚本。 

+ `&&` 
  - A && B，表示若执行 A 成功则执行 B，若执行 A 失败则 B 跳过。
  - A ;  B，表示执行 A 无论成败都执行 B。
  - A || B，表示若执行 A 失败才执行 B，若执行 A 成功则 B 跳过。

+ `|`，管道符，和 R 中一样，管道前的输出可作为管道后的输入。 
                                                             
## 其他

+ `history` ：查看历史命令，比如`history 100`查看最近执行过的100条命令。

+ `ssh` ： secure shell，远程连接，比如本地 shell 终端执行`ssh -p 22 hadoop@xx.xx.x.xx`可以登录服务器上的 hadoop 用户。

+ `free -h` ：查看剩余内存。

+ `df -h`：查看剩余磁盘空间（disk free）。

[***橘子汽水***](https://kg.qq.com/node/play?s=f5b_WhfYOQtIhfNE&shareuid=6a9d9a83242f318f34&shareDescABType=1&topsource=&chain_share_id=co3dZLk3PPyaU2yWM427FOSTti1b4U1YZmcSXozxnro&pageId=details_of_creations)

[***橙子汽水***](https://kg.qq.com/node/play?s=XoN3wSXy21mFpXXT&shareuid=6a9d9a83242f318f34&shareDescABType=1&topsource=&chain_share_id=co3dZLk3PPyaU2yWM427FOSTti1b4U1YZmcSXozxnro&pageId=details_of_creations)
