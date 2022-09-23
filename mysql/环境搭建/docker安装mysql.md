

## 单独运行

```bash
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:8.0.30


docker run -d \
--name mysql-master \
-p 3306:3306 \
-v /mysql/master/conf:/etc/mysql/conf.d \
-v /mysql/master/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=123456 \
mysql:8.0.30

vim /mysql/master/conf/my.cnf
[mysqld]
```





## compose编排

```yaml
version: '3'
services:
  mysql:
    image: mysql:8.0.30
    ports:
      - "3306:3306"
    environment:
      MYSQL_ROOT_PASSWORD: 123456
      # create a database
      MYSQL_DATABASE: spider
```





## k8s编排

```yaml
```

