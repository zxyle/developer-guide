## 介绍
netstat 命令用于显示网络状态。



## 安装

```bash
yum -y install net-tools
```



## 参数

| 参数 | 说明     |
| ---- | -------- |
| t    | TCP      |
| a    | 显示所有 |
| u    | UDP      |
|      |          |
|      |          |



## 用法
```
netstat -nlp | grep 端口号
```



```bash
# 查看端口信息
netstat -anp | grep 端口号
```

