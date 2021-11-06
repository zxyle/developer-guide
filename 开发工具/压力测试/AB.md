## 介绍
Apache Benchmark

## 安装

```
# centos安装
yum -y install httpd-tools
````


## 使用示例
```
示例：ab -n 200000 -c 20000 http://192.168.1.179/ >>d:1.html

-n：请求数

-c：并发数
```

