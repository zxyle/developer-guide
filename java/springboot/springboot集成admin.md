## 介绍

Spring Boot Admin是用于监控Spring Boot服务, 



## 搭建服务端

### 1. 创建spring boot 工程，引入依赖

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
<dependency>
  <groupId>de.codecentric</groupId>
  <artifactId>spring-boot-admin-starter-server</artifactId>
</dependency>
```



### 2. 修改配置 

```properties
server.port=9001
```



### 3. 启动类增加注解

```java
@EnableAdminServer // 添加此行代码
@SpringBootApplication
public class SbaApplication {

    public static void main(String[] args) {
        SpringApplication.run(SbaApplication.class, args);
    }

}
```

然后启动服务 访问http://127.0.0.1:9001/



## 客户端接入

### 1. 引入依赖

```xml
<dependency>
  <groupId>de.codecentric</groupId>
  <artifactId>spring-boot-admin-starter-client</artifactId>
  <version>2.7.4</version>
</dependency>
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```



### 2. 添加配置

```properties
# Spring Boot Admin 监控服务器端地址
spring.boot.admin.client.url=http://localhost:9001

# 开启监控所有项
management.endpoints.web.exposure.include=*
```



