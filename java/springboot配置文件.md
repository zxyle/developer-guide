

## mysql
```properties
spring.datasource.username=root
spring.datasource.password=123456
spring.datasource.url=jdbc:mysql://127.0.0.1:3306/electric?serverTimezone=GMT%2B8&useUnicode=true&characterEncoding=utf-8&useSSL=false
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.schema=classpath:department.sql
```



## JPA

```properties
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```



## Redis

```properties
spring.redis.host=localhost
spring.redis.password=
spring.redis.port=6379
```



## Session

```properties
spring.session.store-type=redis
server.servlet.session.timeout=30m
spring.session.redis.flush-mode=on_save
spring.session.redis.namespace=spring:session
```



## druid



## mybatis



## mybatis-plus



## json

```properties
# Json Properties
spring.jackson.default-property-inclusion=non_null
spring.jackson.date-format=yyyy-MM-dd HH:mm:ss
spring.jackson.time-zone=GMT+8
```

