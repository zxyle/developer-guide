

## JDK环境dockerfile
- 下载[server jre](https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html) 
- 执行构建 `docker build -t oracle-server-jre:8u202 .`

```dockerfile
FROM docker.io/jeanblanchard/alpine-glibc
ADD server-jre-8u202-linux-x64.tar.gz /usr/local/

ENV JAVA_HOME=/usr/local/jdk1.8.0_202 \
    CLASSPATH=$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar  \
    PATH=$PATH:$JAVA_HOME/bin

# timezone 
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories \
    && apk update \
    && apk add tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone

```



## Python环境dockerfile

- 当前目录需要放置 `requirements.txt` 和 `pip.conf`

```dockerfile
FROM python:3.7.7

WORKDIR /usr/src/app

COPY requirements.txt ./

COPY ./pip.conf /etc/pip.conf

ENV TZ=Asia/Shanghai

RUN pip install --no-cache-dir --upgrade pip \
     && pip install --no-cache-dir -r requirements.txt
     
VOLUME /usr/src/app
```



## CentOS环境dockerfile

```dockerfile
FROM centos:7
```



## Debian环境dockerfile

```dockerfile
FROM debian:10.7

RUN sed -i s@/deb.debian.org/@/mirrors.aliyun.com/@g /etc/apt/sources.list \
    && sed -i s@/security.debian.org/@/mirrors.aliyun.com/@g /etc/apt/sources.list \
    && apt update \
    && apt install vim -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
     && echo "Asia/Shanghai" > /etc/timezone
```



## Ubuntu环境dockerfile

```dockerfile
FROM ubuntu:20.04

RUN sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list \
    && sed -i s@/security.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list \
    && apt update \
    && apt install tzdata -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
     && echo "Asia/Shanghai" > /etc/timezone
```



## 前端镜像制作

```dockerfile
FROM nginx

# 先解压前端包 unzip dist.zip
ADD dist/ /usr/share/nginx/html/
```

- 构建镜像: `docker build -t vue_demo .`
- 运行镜像： `docker run --rm -p 8080:80 vue_demo`

