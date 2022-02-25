
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



## ARG

```dockerfile
```

## WORKDIR - 工作目录
```dockerfile
```

## COPY
```dockerfile
```



## ENV - 环境变量

```dockerfile
```

## RUN
```dockerfile
```

## ADD 

解压

```dockerfile
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



## VOLUMN

```dockerfile
```



## ONBUILD

```dockerfile
```



## STOPSIGNAL
