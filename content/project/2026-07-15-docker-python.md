---
title: 使用 Docker 装 Python 环境
author: yuanfan
date: 2026-07-15T21:04:12+0800
slug: docker python
categories:
  - R
tags:
  - R
draft: false
---

<!--more-->

本月初接了个做图像分类的任务，给的时间相对充裕。没想到这次领导腾出来的资源居然也挺充裕，三处服务器算内存的话，一个128G，一个近500G，还有一个7个节点加起来1T（ps当然都是只有 CPU 的）。以前折腾装 R 我都是挨个服务器、挨个节点手动编译……这次有 AI 辅助，也不用离线鼓捣，方案改为直接从 DockerHub 拉取可用的镜像，然后 Dockerfile 编译即可。

# 了解服务器配置

登录服务器，在一切开始之前先了解系统环境。服务器装的是 Anolis os 系统，接近 Centos 8.9，架构类型是 x86_64。

检查操作系统的类型和版本。（ps.十几年前的老机型，又被从灰尘堆里淘出来用的。）

`uname -a`

>Linux DCG1JNYC2-R730 5.10.134-19.3.1.an8.x86_64 #1 SMP Sat May 2 16:03:33 CST 2026 x86_64 x86_64 x86_64 GNU/Linux

`cat /etc/os-release`

>NAME="Anolis OS"
VERSION="8.10"
ID="anolis"
ID_LIKE="rhel fedora centos"
VERSION_ID="8.10"
PLATFORM_ID="platform:an8"
PRETTY_NAME="Anolis OS 8.10"
ANSI_COLOR="0;31"
HOME_URL="https://openanolis.cn/"

查看 gcc 版本。

`gcc -v`

>gcc version 8.5.0 20210514 (Anolis 8.5.0-23.0.1) (GCC) 

查看 CPU 详细信息。

`lscpu`

>CPU(s):              48
Model name:          Intel(R) Xeon(R) CPU E5-2670 v3 @ 2.30GHz
CPU MHz:             3100

查看内存和磁盘的总量及已使用情况。

`free -h`

>              total        used        free      shared  buff/cache   available
Mem:          503Gi       2.4Gi       430Gi        21Mi        70Gi       497Gi
Swap:          63Gi          0B        63Gi

查看 Glibc 版本。

`ldd --version`

>ldd (GNU libc) 2.28

接着一层层配网络代理，按顺序给服务器  -> 包管理器（dnf/yum/rpm）  -> Docker 配代理，启动 Docker 容器时也要注意配代理。

# 部署环境

找 AI 描述需求，让推荐一个合适的镜像：[continuumio/miniconda3](https://hub.docker.com/r/continuumio/miniconda3/)。

## 拉取镜像并启动

1. 拉取镜像，执行`docker pull continuumio/miniconda3`。

2. 启动镜像。注意配置代理，其中`-v /home/hadoop/yf:/opt/notebooks`用于指定脚本的存储路径，由于8888端口被占用改为8787。

```bash
docker run -i -t -p 8787:8888 \
-v /home/hadoop/yf:/opt/notebooks \
-e HTTPS_PROXY=http://xx.xx.xx.xx:10809 \
-e HTTP_PROXY=http://xx.xx.xx.xx:10809 \
-e NO_PROXY=localhost,127.0.0.1,.xxxx.com.cn,10. \
continuumio/miniconda3 /bin/bash -c "\
     conda config --set remote_read_timeout_secs 120 && \
     conda config --set remote_connect_timeout_secs 30 && \
     conda config --set remote_max_retries 5 && \
     conda install jupyter -y --quiet && \
     mkdir -p /opt/notebooks && \ 
     jupyter notebook --notebook-dir=/opt/notebooks --ip=0.0.0.0 --port=8888 --no-browser --allow-root"
```

镜像启动完成后，日志里面会有类似如下内容。

>To access the server, open this file in a browser:<br/>
file:///root/.local/share/jupyter/runtime/jpserver-1-open.html<br/>
Or copy and paste one of these URLs:<br/>
http://e15f101bece4:8888/tree?token=f10e2c3d855cd7fb220be9dee94af8d29ef589f6c98a1c4f<br/>
http://127.0.0.1:8888/tree?token=f10e2c3d855cd7fb220be9dee94af8d29ef589f6c98a1c4f

根据提示的 URL 地址从浏览器登录，但正确的地址应该把 IP 和端口号改成<服务器IP:8787>。登陆以后能正常使用 jupyter，就不需要改用别的镜像了。

注意，如果重启容器，容器内生成的 token 不一样。

## 用 Dockerfile 构建新镜像

1. 创建 Dockerfile 文件。

初次构建镜像是在`/home/hadoop/yf`目录下，但是报了下面的错。AI 的说法是“Trash-0 是 Linux 桌面环境的回收站文件夹，Docker 在打包构建上下文时遇到了权限问题。”于是换到新目录`/home/hadoop/yf/docker-build`，然后就顺利地构建成功了。

>error checking context: 'can't stat '/home/hadoop/yf/.Trash-0''.”，

```bash
# 查看当前目录及内容
pwd && ls -la

# 进入指定目录
cd /home/hadoop/yf/docker-build

# 创建 Dockerfile 文件
# 粘贴内容，按 Ctrl+O 回车保存，Ctrl+X 退出
nano Dockerfile

# 确认文件存在
ls -l Dockerfile
```

下面是要放到 Dockerfile 里面的内容，主要是配代理，以及写明需要安装的 python 包。此前在两台服务器都单独拉取了“continuumio/miniconda3”镜像，但是前后隔了几天版本就差了许多，新版本里面封装的 python 版本变成3.14，出现很多不稳定的因素，而老版本封装的 python 是3.13还算稳定，所以 Dockerfile 里面干脆写死镜像的版本号。

```bash
FROM continuumio/miniconda3:26.3.2-2
ENV HTTPS_PROXY=http://xx.xx.xx.xx:10809
ENV HTTP_PROXY=http://xx.xx.xx.xx:10809
ENV NO_PROXY=localhost,127.0.0.1,.xxxx.com.cn,10.
RUN conda config --set remote_read_timeout_secs 120 && \
    conda config --set remote_connect_timeout_secs 30 && \
    conda config --set remote_max_retries 5 && \
    conda install jupyter -y --quiet && \
    conda install -c conda-forge zbar -y
RUN pip install --proxy http://xx.xx.xx.xx:10809 \
    numpy pandas matplotlib scikit-learn \
    opencv-python-headless pillow joblib tensorflow torch torchvision tqdm \
    scikit-image pyzbar easyocr lightgbm xgboost
RUN mkdir -p /opt/notebooks
EXPOSE 8888
CMD jupyter notebook --notebook-dir=/opt/notebooks \
    --ip=0.0.0.0 --port=8888 --no-browser --allow-root
```

2. 构建新镜像。

其中`image-class:v1`是`<新镜像名称>:<标签>`，`--progress=plain`表示显示构建进度。

```bash
# 使用绝对路径
# docker build -t image-class:v1 --progress=plain /home/hadoop/yf/docker-build

# 使用相对路径
cd /home/hadoop/yf/docker-build
docker build -t image-class:v1 --progress=plain  .

# 查看镜像
docker images image-class:v1
```

3. 启动容器，检查是否正常。

下面`--name myjupyter`是对启动后的容器重命名，后续与容器相关的操作使用容器名称，但镜像名称要保持一致。

```bash
# 启动容器
docker run -d -p 8787:8888 \
  -v /home/hadoop/yf:/opt/notebooks \
  --name myjupyter \
  image-class:v1 \
  jupyter notebook --notebook-dir=/opt/notebooks \
    --ip=0.0.0.0 --port=8888 --no-browser --allow-root

# 查看容器状态，是否正常生成
docker ps   

# 如果生成失败就删了重来
docker stop myjupyter && docker rm myjupyter

# 查看容器日志，找一下 URLs，在浏览器看是否正常登录 jupyter
docker logs myjupyter
```

4. 临时安装 python 包。

jupyter 里检查到 opencv-python 未安装，执行`import cv2`报下面的错误。

>ImportError: libGL.so.1: cannot open shared object file: No such file or directory

据 AI 所说 opencv-python 有系统依赖，要想成功安装还得装些依赖包，不如改成安装 opencv-python-headless。嫌重新构造镜像再重启容器有点费时间，找了写临时安装的方法。

其一，直接在 jupyter 里安装，比如`!pip install scikit-image opencv-python-headless`。`!`是 Jupyter/IPython 的魔法语法，表示把后面的内容当作 shell 命令执行，而不是 Python 代码。

其二，如果新安装的 python 包还需要装系统依赖包，临时使用需要进入运行中的容器来装。比如 pyzbar 这个 python 包依赖系统的 ZBAR 库，在 jupyter 执行`!pip install scikit-image`能安装 python 包但使用时会报错，错误是“ImportError: Unable to find zbar shared library”。

```bash
# 进入容器 docker exec -it <容器名称或容器id> bash
docker exec -it myjupyter bash

# 在容器里执行安装 zbar 库
conda install -c conda-forge zbar -y

# 在容器里执行安装 pyzbar 包
pip install --proxy http://xx.xx.xx.xx:10809 pyzbar

# 在容器里验证
python -c "import ctypes; ctypes.cdll.LoadLibrary('libzbar.so'); print('OK')"
python -c "from pyzbar.pyzbar import decode; print('pyzbar OK')"
```

5. 按需重构镜像。

```bash
# 1. 停止并删除旧容器 docker stop <容器名称或容器id> && docker rm <容器名称或容器id>
docker stop myjupyter && docker rm myjupyter

# 2. 修改 Dockerfile
cd /home/hadoop/yf/docker-build
nano Dockerfile

# 3. 重新构建镜像（覆盖之前的）
docker build -t image-class:v1 --progress=plain /home/hadoop/yf/docker-build

# 4. 用镜像新标签启动容器
docker run -d -p 8787:8888 \
  -v /home/hadoop/yf:/opt/notebooks \
  --name myjupyter \
  image-class:v1 \
  jupyter notebook --notebook-dir=/opt/notebooks \
    --ip=0.0.0.0 --port=8888 --no-browser --allow-root
```

## 踩的坑

最开始给 AI 描述需求后，给的方案里有一个是直接在 docker 容器里安装需要的 python 包，然后另存为固定的镜像名称。这样做的好处是依次安装包的时候，遇到报错可以立刻发现。

 - 运行镜像。
 - 按 Ctrl+P 然后 Ctrl+Q — 脱离容器（detach），容器会在后台继续运行。
 - 执行 `docker ps`查看容器id。
 - 回到容器，执行`docker attach <容器名>`。
 - 安装 python 包。
 - 再次按 Ctrl+P 然后 Ctrl+Q，脱离容器后执行 docker commit
 
```bash
# 运行镜像
docker run -i -t continuumio/miniconda3 /bin/bash

# 在容器内执行，安装 python 包
pip install --proxy http://xx.xx.xx.xx:10809 numpy pandas matplotlib scikit-learn
pip install --proxy http://xx.xx.xx.xx:10809 opencv-python pillow joblib tensorflow torch torchvision tqdm

# 另存为新镜像，其中 magical_perlman 是容器名称（names）
docker commit magical_perlman my-miniconda:latest

# 或者，其中 a22a1f516ddc 是容器 id
docker commit a22a1f516ddc my-miniconda:latest
```

然鹅，直接`docker commit`，周末出去折腾一圈周一回来还是没反应，查原因是`Native Overlay Diff: false`，按照 AI 的说法是“意味着 Docker 无法使用内核的 overlay diff 来快速计算容器改动，而会退化为逐层 tar 全量拷贝。如果你的容器可写层数据量大（装了 conda、pip 大量包），这个退化的 commit 会极其慢，看起来就是卡死两天不动。”

>Storage Driver: overlay2
  Backing Filesystem: xfs
  Supports d_type: true
  Native Overlay Diff: false
  userxattr: false

究其根本是系统版本的问题。于是乎，这才认栽，然后换方案。
