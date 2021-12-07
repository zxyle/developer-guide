

## 引入依赖

```xml
<!--mybatis的starter依赖-->
<dependency>
  <groupId>org.mybatis.spring.boot</groupId>
  <artifactId>mybatis-spring-boot-starter</artifactId>
  <version>2.1.3</version>
</dependency>

<!--mysql驱动-->
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-java</artifactId>
  <scope>runtime</scope>
</dependency>
```



## 编写配置文件

```properties
# mysql
spring.datasource.username=root
spring.datasource.password=123456
spring.datasource.url=jdbc:mysql://127.0.0.1:3306/spring_boot_mybatis?serverTimezone=GMT%2B8&useUnicode=true&characterEncoding=utf-8
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# mybatis (https://mybatis.org/mybatis-3/configuration.html#settings)
mybatis.mapper-locations=classpath:mappers/*.xml
mybatis.configuration.map-underscore-to-camel-case=true
mybatis.type-aliases-package=com.example.springbootwithmybatis.pojo
mybatis.configuration.cache-enabled=true

# 日志
logging.level.com.example.springbootwithmybatis.dao=debug
```

