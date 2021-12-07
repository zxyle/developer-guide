## 介绍

vsftpd（very secure FTP daemon）是一款在Linux发行版中最受推崇的FTP服务器。vsftpd支持匿名访问和本地用户模式两种访问方式。匿名访问方式任何用户都可以访问搭建的FTP服务；本地用户模式只支持添加的本地用户访问搭建的FTP服务。

> 说明: 匿名用户模式和本地用户模式只可同时配置一种。

```bash
# 1. 运行以下命令安装vsftpd。
yum install -y vsftpd

# 2. 运行以下命令设置FTP服务开机自启动。
systemctl enable vsftpd.service

# 3. 启动FTP服务。
systemctl start vsftpd.service

# 4. 运行以下命令查看FTP服务监听的端口。
yum -y install net-tools
netstat -antup | grep ftp

出现如下图所示界面，表示FTP服务已启动，监听的端口号为 21。此时，vsftpd默认已开启匿名访问功能，您无需输入用户名密码即可登录FTP服务器，但没有修改或上传文件的权限。

```

![img](https://img.alicdn.com/tfs/TB1PJdhDvb2gK0jSZK9XXaEgFXa-1129-96.jpg)



## 匿名用户模式配置

```bash
# 1. 修改配置文件vsftpd.conf。
vim /etc/vsftpd/vsftpd.conf

# 2. 将匿名上传权限 anon_upload_enable=YES 的注释解开。

# 3. 更改/var/ftp/pub目录的权限，为FTP用户添加写权限。
chmod o+w /var/ftp/pub/

# 4. 重启FTP服务。
systemctl restart vsftpd.service
```



## 本地用户模式配置

```bash
# 1. 为FTP服务创建一个Linux用户。
adduser ftptest

# 2. 为用户设置密码。
passwd ftptest

# 3. 创建一个供FTP服务使用的文件目录。
mkdir /var/ftp/test

# 4. 更改/var/ftp/test目录的拥有者为ftptest。
chown -R ftptest:ftptest /var/ftp/test

# 5. 修改vsftpd.conf配置文件。
配置FTP为主动模式请执行如下命令:
sed -i 's/anonymous_enable=YES/anonymous_enable=NO/' /etc/vsftpd/vsftpd.conf #禁止匿名登录FTP服务器 
sed -i 's/listen=NO/listen=YES/' /etc/vsftpd/vsftpd.conf #监听IPv4 sockets 
sed -i 's/listen_ipv6=YES/#listen_ipv6=YES/' /etc/vsftpd/vsftpd.conf #关闭监听IPv6 sockets 
sed -i 's/#chroot_local_user=YES/chroot_local_user=YES/' /etc/vsftpd/vsftpd.conf #全部用户被限制在主目录 
sed -i 's/#chroot_list_enable=YES/chroot_list_enable=YES/' /etc/vsftpd/vsftpd.conf #启用例外用户名单 
sed -i 's/#chroot_list_file=/chroot_list_file=/' /etc/vsftpd/vsftpd.conf #指定例外用户列表文件，列表中的用户不被锁定在主目录 
echo "allow_writeable_chroot=YES" >> /etc/vsftpd/vsftpd.conf 
echo "local_root=/var/ftp/test" >> /etc/vsftpd/vsftpd.conf #设置本地用户登录后所在的目录

配置FTP为被动模式请执行如下命令：
sed -i 's/anonymous_enable=YES/anonymous_enable=NO/' /etc/vsftpd/vsftpd.conf #禁止匿名登录FTP服务器 
sed -i 's/listen=NO/listen=YES/' /etc/vsftpd/vsftpd.conf #监听IPv4 sockets 
sed -i 's/listen_ipv6=YES/#listen_ipv6=YES/' /etc/vsftpd/vsftpd.conf #关闭监听IPv6 sockets 
sed -i 's/#chroot_local_user=YES/chroot_local_user=YES/' /etc/vsftpd/vsftpd.conf #全部用户被限制在主目录 
sed -i 's/#chroot_list_enable=YES/chroot_list_enable=YES/' /etc/vsftpd/vsftpd.conf #启用例外用户名单 
sed -i 's/#chroot_list_file=/chroot_list_file=/' /etc/vsftpd/vsftpd.conf #指定例外用户列表文件，列表中的用户不被锁定在主目录 
echo "allow_writeable_chroot=YES" >> /etc/vsftpd/vsftpd.conf 
echo "local_root=/var/ftp/test" >> /etc/vsftpd/vsftpd.conf #设置本地用户登录后所在的目录 

echo "pasv_enable=YES" >> /etc/vsftpd/vsftpd.conf #开启被动模式 
echo "pasv_address=<FTP服务器公网IP地址>" >> /etc/vsftpd/vsftpd.conf #本教程中为ECS服务器弹性IP 
echo "pasv_min_port=20" >> /etc/vsftpd/vsftpd.conf #设置被动模式下，建立数据传输可使用的端口范围的最小值 
echo "pasv_max_port=21" >> /etc/vsftpd/vsftpd.conf #设置被动模式下，建立数据传输可使用的端口范围的最大值

# 在/etc/vsftpd目录下创建chroot_list文件，并在文件中写入例外用户名单。
#使用vim命令编辑chroot_list文件，添加例外用户名单。此名单中的用户不会被锁定在主目录，可以访问其他目录。
vim /etc/vsftpd/chroot_list
说明: 没有例外用户时，也必须创建chroot_list文件，内容可为空。

# 6. 重启FTP服务。
systemctl restart vsftpd.service

# 测试
浏览器打开 ftp://139.0.0.1:21
```

