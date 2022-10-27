
## 介绍
https://docs.docker.com/engine/reference/builder/



## FROM - 基础镜像

```dockerfile
FROM redis:6
```



## MAINTAINER(已废弃)

```
LABEL maintainer="zxyful@gmail.com"
```



## LABEL - 标签

```dockerfile
LABEL maintainer=Xiang Zheng
```



## ARG - 参数

```dockerfile
# 定义参数
ARG DOCKER_USERNAME=library

# 使用参数
FROM ${DOCKER_USERNAME}/alpine
```

## WORKDIR - 工作目录
```dockerfile
WORKDIR /opt/code
```

## COPY - 复制到容器
```dockerfile
COPY hadoop-env.sh /opt/soft/hadoop-${VERSION}/etc/hadoop/hadoop-env.sh
```



## ENV - 环境变量

```dockerfile
# 单个变量
ENV PATH=$PATH:$HADOOP_HOME/bin

# 多个变量
ENV HADOOP_HOME=/opt/soft/hadoop-${HADOOP_VERSION} \
    PATH=$PATH:$HADOOP_HOME/bin \
    PATH=$PATH:$HADOOP_HOME/sbin
```

## RUN - 执行命令
```dockerfile
RUN cmd1 && \
    cmd2 
```

## ADD 

复制并解压

```dockerfile
ADD hadoop-3.2.0.tar.gz /opt/soft/
```

## CMD
```dockerfile
```



## ENTRYPOINT

```dockerfile
ENTRYPOINT ["java", "-jar", "/app.jar"]
```



## EXPOSE - 开放端口

```dockerfile
EXPOSE 8080
```



## HEALTHCHECK - 健康检查

```dockerfile
```



## VOLUMN - 数据卷

```dockerfile
VOLUME ["/data"] 
```



## ONBUILD

```dockerfile
```



## STOPSIGNAL
