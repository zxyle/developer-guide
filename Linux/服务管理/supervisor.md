## 介绍
简单来说就是守护进程 更多内容参考[参考文档](http://www.supervisord.org/index.html)



## 安装

```
pip install supervisor 或者 yum install supervisor -y
```

## 增加开启启动
```
systemctl start  supervisord  --now
```

## 生成配置文件
```
echo_supervisord_conf > /etc/supervisord.conf
```

## 创建进程配置文件目录

```
mkdir -p /etc/supervisor/conf.d
```



## 修改上述位置的配置文件

* 将[inet_http_server]块内容 注销取消掉
* 将[inet_http_server]块中的127.0.0.1替换成0.0.0.0
* 将末尾的[include] 取消注释 并修改 files = /etc/supervisor/conf.d/*.conf



## 运行supervisor

```
supervisord -c /etc/supervisord.conf
```



## 重启/重加载supervisor

```
supervisorctl
Server requires authentication
Username: user
Password: 123
```



## 进程配置文件放到 /etc/supervisor/conf.d

```
; xxx的守护进程
[program:keep_login]
command=/opt/soft/wechat_venv/bin/python keep_login.py
directory=/opt/soft/wechat_spider/      ; 项目的文件夹路径
startsecs=5                            ; 启动5秒后没有异常退出，就当做已经正常启动
stopwaitsecs=0                         ; 终止等待时间
autostart=true                         ; 在supervisor启动时自动启动
autorestart=true                       ; 程序异常退出后自动重启
stdout_logfile=/tmp/spiderlog/supervisorlog/keep_login.log  ; log 日志
stderr_logfile=/tmp/spiderlog/supervisorlog/keep_login.err  ;错误日志
;environment=prefix='/opt/soft/scrapy_venv/bin/'    ; 环境变量
startretries = 3                       ; 启动失败 自动重试次数 默认是3次
;user=root                             ; 执行用户
;priority=100                          ; 优先级设置
stdout_logfile_maxbytes=200MB ; 输出日志文件大小限制 超过会切分
numprocs=1
process_name=%(program_name)s_%(process_num)02d
```



## Web管理后台

http://127.0.0.1:9001