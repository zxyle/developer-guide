```bash
# 1. 执行以下命令，查看yum源中JDK版本。
yum list java*

# 2. 执行以下命令，使用yum安装JDK1.8。
yum -y install java-1.8.0-openjdk*

# 3. 执行以下命令，查看是否安装成功。
java -version
openjdk version "1.8.0_312"
OpenJDK Runtime Environment (build 1.8.0_312-b07)
OpenJDK 64-Bit Server VM (build 25.312-b07, mixed mode)
```



## 在线安装mysql

```bash
# 1. 执行以下命令，下载并安装MySQL官方的Yum Repository。
wget http://dev.mysql.com/get/mysql57-community-release-el7-10.noarch.rpm
yum -y install mysql57-community-release-el7-10.noarch.rpm
yum -y install mysql-community-server

# 2. 执行以下命令，启动 MySQL 数据库。
systemctl start mysqld.service

# 3. 执行以下命令，查看MySQL初始密码。
grep "password" /var/log/mysqld.log

# 4. 执行以下命令，输入上条命令中MySQL初始密码，登录数据库。
mysql -uroot -p

# 5. 执行以下命令，修改MySQL默认密码。
set global validate_password_policy=0;  #修改密码安全策略为低（只校验密码长度，至少8位）。
ALTER USER 'root'@'localhost' IDENTIFIED BY '12345678';

# 6. 执行以下命令，授予root用户远程管理权限。
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '12345678';

```



## 安装Tomcat

```bash
# 1. 执行以下命令，下载Tomcat压缩包。如果该镜像失效，请查看tomcat最新版本，并进行替换。
wget --no-check-certificate https://labfileapp.oss-cn-hangzhou.aliyuncs.com/apache-tomcat-8.5.72.tar.gz

# 2. 执行以下命令，解压刚刚下载Tomcat包。
tar -zxvf apache-tomcat-8.5.72.tar.gz

# 3. 执行以下命令，修改Tomcat名字。
mv apache-tomcat-8.5.72 /usr/local/Tomcat8.5

# 4. 执行以下命令，为Tomcat授权。
chmod +x /usr/local/Tomcat8.5/bin/*.sh

# 5. 执行以下命令，修改Tomcat默认端口号为80。
说明：Tomcat默认端口号为8080。
sed -i 's/Connector port="8080"/Connector port="80"/' /usr/local/Tomcat8.5/conf/server.xml

# 6. 启动Tomcat。
/usr/local/Tomcat8.5/bin/./startup.sh

```



## 卸载

```bash
rpm -qa|grep jdk
yum -y remove copy-jdk-configs-3.3-10.el7_5.noarch
```

