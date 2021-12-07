
## 介绍



## 导入依赖

```xml
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-data-redis</artifactId>
</dependency>

<dependency>
	<groupId>org.springframework.session</groupId>
	<artifactId>spring-session-data-redis</artifactId>
</dependency>
```



## 配置

```properties
# session
spring.session.store-type=redis
server.servlet.session.timeout=30m
spring.session.redis.flush-mode=on_save
spring.session.redis.namespace=spring:session

# redis
spring.redis.host=localhost
spring.redis.password=
spring.redis.port=6379
```

## 主启动类
```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.session.data.redis.config.annotation.web.http.EnableRedisHttpSession;

@SpringBootApplication
@EnableRedisHttpSession
public class SpringSessionDemoApplication {

	public static void main(String[] args) {
		SpringApplication.run(SpringSessionDemoApplication.class, args);
	}

}
```



## 使用

```java
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import javax.servlet.http.HttpSession;

@RestController
public class HelloController {
    @RequestMapping("/")
    public String helloAdmin(HttpSession session) {
        // 设置cookie
        // session.setAttribute();
        // 获取cookie
        // session.getAttribute()
      
      	// 会话失效(一般用于退出登录，修改密码，账号禁用)
        // session.invalidate();
         
        return "hello admin";
    }
}
```