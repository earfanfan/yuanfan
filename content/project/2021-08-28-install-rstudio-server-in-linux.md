---
title: 在linux中安装Rstudio-server的笔记
author: yuanfan
date: '2021-08-28'
slug: install-rstudio-server-in-linux
categories:
  - R
tags:
  - R
draft: no
---

<font face="微软雅黑">

<!--more-->

由于最近频繁被抓去画原型而诞生了一个想法，如果本地用Rstudio写的Rmd文件能够放到服务器上并且生成html文件并且能直接展示给用户，再让Rmd文件中的数据能够固定频率更新，那么这种开发方式能直接省掉前端页面开发的步骤，初步想法是：

+ 第一步，在数据库中写存储过程来取数，不同情况视运行效率来看是把数据处理写到存过里还是放到R里；

+ 第二步，R可以连接数据库中的表，本地用flexdashboard、echarts4r等包画原型的Rmd文件调试好以后放到服务器上；

+ 第三步，服务器上可以用Rstudio-server来把Rmd文件生成html文件并且放到指定目录下；

+ 第四步，指定目录下的html文件可以直接通过前台页面访问。

+ 第五步，设置调度，让底层数据能固定频率更新，前台页面的数据也能固定频率更新。

其中第一、二、四步确认可行，关于调度的部分我是完全没接触过今日暂且不论，现在服务器上已经有R，只需要再装Rstudio-server，然后再装一些可视化方面的包就能继续验证想法。

I.去[官网](https://www.rstudio.com/products/rstudio/download-server/)下载安装包

II.安装

`sudo yum localinstall rstudio-server-rhel-1.4.1717-x86_64.rpm`

III.设置与端口相关的配置

```
#添加两个跟端口配置相关的文件
sudo vi /etc/rstudio/rserver.conf 
sudo vi /etc/rstudio/rsession.conf  #没有用，要删掉

#文件中增加下面两行
rsession-which-r=/R-xxx/bin/R  ##系统的R程序所在位置
www-port=8787 ### 通过ip的8787端口连接
```

这一步的两个文件是网上教程里写的，事实上第二个文件没有用而且还会报错。但是前面已经添加了这个文件，后面可以删掉这个文件，或者对这个文件重命名：

`sudo mv /etc/rstudio/rsession.conf /etc/rstudio/rsession.conf.bak`

网上教程里还写到要如何开启8787端口，但是由于本来就有能用的端口，也没有被占用，可以直接用，我也不可能有权限开端口，于是略过这一步。

IV.检查配置是否完整

`sudo rstudio-server verify-installation`

这一步报了一个错：

>R shared library (.../R-4.0.3/lib64/R/lib/libR.so) not found. If this is a custom build of R, was it built with the --enable-R-shlib option?

上网搜了搜，各个论坛异口同声说是装R的时候在`./configure`这步缺少`--enable-R-shlib`才会报这个错，于是要重装R。

V.重装R

由于服务器上本来就有R，之前装R的源码包也还在所以不用去官网重新下载，直接拷贝到一个新文件夹下面进行解压：

`tar -zxvf R-4.0.3.tar.gz`

比如新文件夹名字是r-temp，接着进入解压好的文件目录下比如../r-temp/R-4.0.3/重新编译R。由于目的是覆盖原来的，所以--prefix=..这里要填写原来已经装好的R的目录:

```
./configure --prefix=原来的R安装目录 --enable-R-shlib=yes --with-tcltk --with-pcre1
make
make install
```

这一步完成没报错的话就可以再次检查配置是否完整，要是还报错的话多半是各种依赖问题，老老实实去瞎碰乱试各种解决办法就可以了。当然，最好是先在测试环境试，搞定了再去生产环境上面弄。

VI.启动服务

```
#启动服务
sudo rstudio-server start
#重启服务
sudo rstudio-server restart
#查端口有无被占用
netstat -ano|grep 8787
#查看状态，当出现active时，配置完成
sudo rstudio-server status

● rstudio-server.service - RStudio Server
   Loaded: loaded (/usr/lib/systemd/system/rstudio-server.service; enabled; vendor preset: disabled)
   Active: active (running) since Sat 2021-08-28 10:05:11 CST; 10s ago
  Process: 35342 ExecStart=/usr/lib/rstudio-server/bin/rserver (code=exited, status=0/SUCCESS)
 Main PID: 35343 (rserver)
   CGroup: /system.slice/rstudio-server.service
           └─35343 /usr/lib/rstudio-server/bin/rserver

Aug 28 10:05:11 h85.hadoop systemd[1]: Starting RStudio Server...
Aug 28 10:05:11 h85.hadoop systemd[1]: Started RStudio Server.
```

到这一步就完成了，可以在浏览器里输入`IP:8787`然后登陆进去试试原来装的R包是不是都能正常加载。
