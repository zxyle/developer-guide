
## 介绍
phpMyAdmin是一个MySQL数据库管理工具，通过Web接口管理数据库方便快捷。

## 安装步骤
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
http://[IP地址]/phpmyadmin/
```



### docker使用

```yaml
version: '3'
services:
  mysql:
    image: mysql:8-oracle
    ports:
      - "3306:3306"
    command:
      --character-set-server=utf8mb4
      --collation-server=utf8mb4_unicode_ci

    environment:
      MYSQL_ROOT_PASSWORD: ocnAYRtYFcxxrxPr
      # create a database
      MYSQL_DATABASE: app
      # create a user
      MYSQL_USER: demo
      MYSQL_PASSWORD: MDfhxIhfatpMGMjP

  phpmyadmin:
    image: phpmyadmin:5.2.0
    ports:
      - "8083:80"
    environment:
      - PMA_ARBITRARY=1
```

