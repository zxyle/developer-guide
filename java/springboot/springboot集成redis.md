
## 介绍

## 引入依赖
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-redis</artifactId>
</dependency>
```

## 配置文件
```properties
# redis
spring.redis.host=localhost
spring.redis.port=6379
spring.redis.database=0
spring.redis.password=
```

## 使用
```java
import org.springframework.data.redis.core.StringRedisTemplate;

@Autowired
StringRedisTemplate stringRedisTemplate;  // 操作字符串

// incr
Long times = stringRedisTemplate.opsForValue().increment("numbers");

```
