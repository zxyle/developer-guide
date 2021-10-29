## 介绍

- https://systemd.io/
- https://github.com/systemd/systemd


## 一、systemctl常见命令
- 重新加载: systemctl daemon-reload
- 查看: systemctl status [服务名]
- 启动: systemctl start [服务名]
- 关闭: systemctl stop [服务名]
- 重启: systemctl restart [服务名]
- 开机启动: systemctl enable  [服务名]
- 关闭自启: systemctl disable [服务名]
- 启动并开机自启: systemctl enable [服务名] --now

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
