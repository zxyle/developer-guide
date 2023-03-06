## 介绍

*SonarQube* 是一个开源的代码分析平台



## docker安装

```bash
# 使用内置h2数据库
docker run -d --name sonarqube -e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true -p 9000:9000 sonarqube:9.9.0-community

# 使用postgresql
docker run -d --name sonarqube \
    -p 9000:9000 \
    -e SONAR_JDBC_URL=jdbc:postgresql://some-postgres:5432/sonar \
    -e SONAR_JDBC_USERNAME=postgres \
    -e SONAR_JDBC_PASSWORD=mysecretpassword \
    --link some-postgres  sonarqube:9.9.0-community
```



## 使用

访问 http://127.0.0.1:9000/

使用admin / admin 登录

创建工程