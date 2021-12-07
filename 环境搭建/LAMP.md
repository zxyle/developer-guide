## 介绍

Linux Apache MySQL PHP的首字母缩写



## Apache

```bash
# 1. 执行如下命令，安装Apache服务及其扩展包。
yum -y install httpd httpd-manual mod_ssl mod_perl mod_auth_mysql

# 2. 执行如下命令，启动Apache服务。
systemctl start httpd.service

# 3. 测试
浏览器打开 http://192.168.98.16/
```



## MySQL

```bash
# 1. 执行以下命令，下载并安装MySQL官方的Yum Repository。
rpm -e mariadb-libs --nodeps
yum install -y https://mirrors.aliyun.com/mysql/MySQL-5.7/mysql-community-common-5.7.35-1.el7.x86_64.rpm
yum install -y https://mirrors.aliyun.com/mysql/MySQL-5.7/mysql-community-libs-5.7.35-1.el7.x86_64.rpm
yum install -y https://mirrors.aliyun.com/mysql/MySQL-5.7/mysql-community-libs-compat-5.7.35-1.el7.x86_64.rpm
yum install -y https://mirrors.aliyun.com/mysql/MySQL-5.7/mysql-community-client-5.7.35-1.el7.x86_64.rpm
yum install -y https://mirrors.aliyun.com/mysql/MySQL-5.7/mysql-community-server-5.7.35-1.el7.x86_64.rpm

# 2. 运行以下命令查看MySQL版本号。
mysql -V

# 3. 执行以下命令，启动 MySQL 数据库。
systemctl start mysqld.service

# 4. 执行以下命令，查看MySQL初始密码。
grep "password" /var/log/mysqld.log

# 5. 执行以下命令，登录数据库。
mysql -uroot -p

# 6. 执行以下命令，修改MySQL root账号密码。
set global validate_password_policy=0;  #修改密码安全策略为低（只校验密码长度，至少8位）。
ALTER USER 'root'@'localhost' IDENTIFIED BY '12345678';

# 7. 执行以下命令，授予root用户远程管理权限。
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '12345678';

#  8. 输入exit退出数据库。
exit;
```





## PHP

PHP（PHP：Hypertext Preprocessor递归缩写）中文名字是：“超文本预处理器”，是一种广泛使用的通用开源脚本语言，适合于Web网站开发，它可以嵌入HTML中。编程范型是面向对象、命令式编程的。

```bash
# 1. 执行以下下命令，安装PHP环境。
yum -y install php php-mysql gd php-gd gd-devel php-xml php-common php-mbstring php-ldap php-pear php-xmlrpc php-imap

# 2. 执行以下命令创建PHP测试页面。
echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php

# 3. 执行以下命令，重启Apache服务。
systemctl restart httpd

# 4. 访问
http://192.168.98.16/phpinfo.php
```





## phpMyAdmin

phpMyAdmin是一个MySQL数据库管理工具，通过Web接口管理数据库方便快捷。

```bash
# 1. 执行以下命令，创建phpMyAdmin数据存放目录。
mkdir -p /var/www/html/phpmyadmin

# 2. 执行以下命令，下载phpMyAdmin压缩包。
wget --no-check-certificate https://files.phpmyadmin.net/phpMyAdmin/4.0.10.20/phpMyAdmin-4.0.10.20-all-languages.zip

# 3. 执行以下命令，安装unzip并解压phpMyAdmin压缩包。
yum install -y unzip
unzip phpMyAdmin-4.0.10.20-all-languages.zip

# 4. 执行以下命令，复制phpMyAdmin文件到数据存放目录。
mv phpMyAdmin-4.0.10.20-all-languages/*  /var/www/html/phpmyadmin

# 5. 在本地浏览器的址栏中，输入http://实例公网 IP/phpmyadmin，访问phpMyAdmin。

# 6. 在phpMyAdmin登录页面，依次输入MySQL的用户名和密码，单击执行。
http://192.168.98.16/phpmyadmin/
```

