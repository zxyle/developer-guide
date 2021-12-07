## 介绍
CentOS 7 防火墙



## 常用命令

- 查看防火墙状态 `firewall-cmd --state` 或 `systemctl status firewalld`        
- 停止防火墙     `systemctl stop firewalld`    
- 禁止开机启动   `systemctl disable firewalld` 
- 重启网卡       `systemctl restart network`
- 开启防火墙     `service firewalld start`
- 重启防火墙     `service firewalld restart`


## 添加开放端口(开放8080端口(tcp协议)) (需要重启)
```
firewall-cmd --zone=public --add-port=8080/tcp --permanent 
```

## 关闭端口(需要执行以下重启命令)
```
firewall-cmd --zone=public --remove-port=8080/tcp --permanent
```

## 重启命令
```
firewall-cmd --reload
```

## 查看开放端口
```
firewall-cmd --list-ports
```

## 查看防火墙规则
```shell
firewall-cmd --list-all 
```

## 查询是否开启
```
firewall-cmd --query-port=8080/tcp
```