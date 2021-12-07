

## 设置主机名

```bash
# 临时设置
hostname bigdata01

# 永久设置
hostenamectl set-hostname xxx

# 或者
编辑 /etc/hostname
```



## 查看内核版本

```bash
cat /proc/version

uname -a
```



## 查看系统版本

```bash
# centos
cat /etc/redhat-release
CentOS Linux release 7.9.2009 (Core)

# ubuntu
cat /etc/issue
Ubuntu 20.04.3 LTS \n \l
```



## 关闭SELinux

- 使用 `getenforce` 命令查看, 输出Enforcing代表开启
- 编辑 `/etc/selinux/config`
- 将`enforcing` 改为`disabled`
- 重启系统，使用`getenforce`再次检查, 输出 Disabled
- 一条命令: `sed -i 's/enforcing/disabled/'/etc/selinux/config` 



## 关闭虚拟内存

```bash
sed -ri 's/.*swap.*/#&/' /etc/fstab
```



## 开关机

- 立即关机: `shutdown -h now`
- 立即重启: `shutdown -r now`



## DNS 设置

编辑 `/etc/resolv.conf` 文件

添加以下两行

```
nameserver 223.5.5.5
nameserver 223.6.6.6
```

