

## 时区设置
### alpine：
```
apk add -U tzdata \
  && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

```dockerfile
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories \
    && apk update \
    && apk add tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone
```

### debian & centos:
```
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
     && echo "Asia/Shanghai" > /etc/timezone
```