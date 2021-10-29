## 介绍

- 安装: `yum install iptables-services`
- 重启: `systemctl restart iptables.service`
- 自启: `systemctl enable iptables.service`

## 基本操作
```shell
# 查看防火墙状态
service iptables status  

# 停止防火墙
service iptables stop  

# 启动防火墙
service iptables start  

# 重启防火墙
service iptables restart  

# 永久关闭防火墙
chkconfig iptables off  

# 永久关闭后重启
chkconfig iptables on　
```

## 开启端口
```shell
vim /etc/sysconfig/iptables

# 加入如下代码
-A INPUT -m state --state NEW -m tcp -p tcp --dport 80 -j ACCEPT

保存退出后重启防火墙
service iptables restart
```