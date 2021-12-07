## 介绍

Apache开源的消息队列, https://activemq.apache.org/



## 安装步骤

- 下载: [阿里云镜像](https://mirrors.aliyun.com/apache/activemq/) 或 [官网](http://activemq.apache.org/components/classic/download/)

- 解压
- 启动activemq `./bin/activemq [start|stop|restart|status]`
- 通过端口查询进程信息命令`netstat -anp | grep 61616`
- 通过`http://localhost:8161/admin/`进行访问，账号密码都为`admin`