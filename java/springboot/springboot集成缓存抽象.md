

## 介绍




## 引入依赖
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-cache</artifactId>
</dependency>
```



## 配置文件

```properties
# 缓存
spring.cache.type=redis
spring.cache.redis.time-to-live=3600000
spring.cache.redis.key-prefix=CACHE_
# 是否缓存空值, 防止缓存穿透
spring.cache.redis.cache-null-values=true
spring.cache.redis.use-key-prefix=true
```



## 主启动类添加注解

```java
@EnableCaching
```



## 使用注解

- @Cacheable 需要指定一个cacheNames属性
- 
