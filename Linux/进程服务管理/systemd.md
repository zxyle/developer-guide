## 简介

systemd是目前Linux 系统上主要的系统守护进程管理工具

- 官网 https://systemd.io/
- github https://github.com/systemd/systemd


## 一、systemctl常见命令
- 重新加载: systemctl daemon-reload
- 查看: systemctl status [服务名]
- 启动: systemctl start [服务名]
- 关闭: systemctl stop [服务名]
- 重启: systemctl restart [服务名]
- 重载: systemctl reload [服务名]
- 开机启动: systemctl enable  [服务名]
- 关闭自启: systemctl disable [服务名]
- 立即启动并设置开机自启: systemctl enable [服务名] --now
- 立即关闭并取消开机自启: systemctl disable [服务名] --now



## 二、service

### 编写.service文件

service文件放在/etc/systemd/system


```
[Unit]
Description=monitor-web server
After=network.target remote-fs.target nss-lookup.target

[Service]
Type=forking
User=root
EnvironmentFile=/opt/yqyd/package/monitor-web/config/monitor-web.env
WorkingDirectory=/opt/yqyd/package/monitor-web

ExecStartPre=/bin/sh -c 'if [ ! -d ${LOG_PATH} ]; then mkdir ${LOG_PATH}; fi'
ExecStart=/bin/sh -c '${JAVA_HOME}/java ${JVM_OPTIONS} -jar -Dloader.path=${APP_HOME}/lib ${APP_HOME}/${JAR_NAME} >${LOG_PATH}/stdout.log  2>&1 &'
ExecReload=/bin/kill -s HUP $MAINPID
ExecStop=/bin/kill -s QUIT $MAINPID

[Install]
WantedBy=multi-user.target
```



## 案例1: systemd部署springboot jar包

### 0. 准备

- 服务名称: monitor-web

- jar包名称： monitor-web-0.0.1-SNAPSHOT.jar
- 部署目录: /opt/yqyd/package/monitor-web/
  - env文件位置： /opt/yqyd/package/monitor-web/config
  - 日志文件位置: /opt/yqyd/package/monitor-web/logs
  - JAVA_HOME:  /usr/java/jdk1.8.0_181/bin



### 1. 编写service

> vim /etc/systemd/systemd/monitor-web.service

```
[Unit]
Description=monitor-web server
After=network.target remote-fs.target nss-lookup.target

[Service]
Type=forking
User=root
EnvironmentFile=/opt/yqyd/package/monitor-web/config/monitor-web.env
WorkingDirectory=/opt/yqyd/package/monitor-web

ExecStartPre=/bin/sh -c 'if [ ! -d ${LOG_PATH} ]; then mkdir ${LOG_PATH}; fi'
ExecStart=/bin/sh -c '${JAVA_HOME}/java ${JVM_OPTIONS} -jar -Dloader.path=${APP_HOME}/lib ${APP_HOME}/${JAR_NAME} > /dev/null  2>&1 &'
ExecReload=/bin/kill -s HUP $MAINPID
ExecStop=/bin/kill -s QUIT $MAINPID

[Install]
WantedBy=multi-user.target
```



### 2. 编写env

> monitor-web.env

```
JAR_NAME=monitor-web-0.0.1-SNAPSHOT.jar
PROFILE=prod
PROJ_HOME=/opt/yqyd/package/monitor-web
APP_HOME=$PROJ_HOME
LOG_PATH=$PROJ_HOME/logs

GC_LOG_OPTS="-XX:+PrintGC -XX:+PrintGCDetails -Xloggc:/opt/yqyd/package/monitor-web/logs/gc.log"
GC_OPTS=-XX:+UseG1GC
OTHER_OPTS=-Dspring.profiles.active=prod
JVM_OPTIONS="-server -Xms2g -Xmx8g $GC_OPTS $GC_LOG_OPTS $OTHER_OPTS"
JAVA_HOME=/usr/java/jdk1.8.0_181/bin
```



## 3. 编写重启脚本

> restart.sh

```sh
#!/usr/bin/env bash

systemctl restart  monitor-web
echo "web模块重启完成."
```



### 4. 使用

- systemctl daemon-reload
- systemctl enable monitor-web --now
