## 介绍
centos 7以上安装及一些基本初始化配置

## 镜像下载
- [阿里云镜像站](https://mirrors.aliyun.com/centos/)
- [腾讯软件源](https://mirrors.cloud.tencent.com/centos/)
- [历史版本下载](https://mirrors.aliyun.com/centos-vault)
- [历史版本下载](https://mirrors.cloud.tencent.com/centos-vault)
- https://vault.centos.org

打开对应版本下的 `isos/x86_64/` 目录

## 配置
- 关闭防火墙

## 安装常用软件
```bash
yum install -y unzip zip wget vim lrzsz nmap
```

## 安装其他yum源
- `yum install -y epel-release`

## 网络配置
```bash
# 查看那一块网卡
ifconfig  / netstat -i

# 编辑网卡配置
vim /etc/sysconfig/network-scripts/ifcfg-<网卡名>

# 重启网络服务
service network restart
```



## yum
- `yum update`  更新系统中的一个或多个软件包
- `yum makecache`  创建元数据缓存
- `yum clean all` 删除缓存数据
- `yum -y install epel-release` 安装软件源
- `yum groupinstall "Development Tools"` 安装Development Tools 所有包
- `yum grouplist` 查看有哪些group
- `yum remove `
- `yum install`
- `yum search 关键字`
- `yum list` 查询所有可用软件包列表



## 软件源管理

/etc/yum.repos.d/CentOS-Base.repo



```
[base]
name=CentOS-$releasever
enabled=1
failovermethod=priority
baseurl=http://mirrors.cloud.aliyuncs.com/centos/$releasever/os/$basearch/
gpgcheck=1
gpgkey=http://mirrors.cloud.aliyuncs.com/centos/RPM-GPG-KEY-CentOS-7

[updates]
name=CentOS-$releasever
enabled=1
failovermethod=priority
baseurl=http://mirrors.cloud.aliyuncs.com/centos/$releasever/updates/$basearch/
gpgcheck=1
gpgkey=http://mirrors.cloud.aliyuncs.com/centos/RPM-GPG-KEY-CentOS-7

[extras]
name=CentOS-$releasever
enabled=1
failovermethod=priority
baseurl=http://mirrors.cloud.aliyuncs.com/centos/$releasever/extras/$basearch/
gpgcheck=1
gpgkey=http://mirrors.cloud.aliyuncs.com/centos/RPM-GPG-KEY-CentOS-7
```



## rpm

### 1. 软件包安装
```bash
rpm -ivh jdk-8u202-linux-x64.rpm
```
- -i 安装软件包
- -v 提供更多的详细信息输出
- -h 软件包安装的时候列出哈希标记 (和 -v 一起使用效果更好)

### 2. 软件包卸载
```
rpm -e 包名
```

### 3. 软件包更新
```
rpm
```

### 4. 查询软件列表
```bash
rpm -qa | grep mysql
```


### 5. rpm软件包编写


## 其他
- 查看版本: `cat /etc/redhat-release`



## 禁用swap分区
- 修改`/etc/fstab`, 注释掉最后一行
- 使用 `free -h` 查看swap那一行