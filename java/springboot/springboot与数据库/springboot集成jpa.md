
## 介绍
版本: 
- spring-data-jpa:2.3.4 
- mysql-driver:8.0.21 
- mysql:8

## 1. pom引入依赖
```xml
<!--jpa-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<!--mysql驱动-->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
</dependency>
```

## 2. 配置环境
```properties
# mysql
spring.datasource.username=root
spring.datasource.password=123456
spring.datasource.url=jdbc:mysql://127.0.0.1:3306/jpa?serverTimezone=Asia/Shanghai&useUnicode=true&characterEncoding=utf-8
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# jpa
# 更新或者创建数据表
spring.jpa.hibernate.ddl-auto=update
# 控制台显示SQL
spring.jpa.show-sql=true
spring.jpa.database=mysql
```

## 3. 编写Entity(实体)
```java

import lombok.Data;

import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.Table;


@Data
@Entity
@Table(name = "order")
public class Order {
    // 数据库每一个字段对应一个属性
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    // create_time
    // modify_time
    
    // name
    // age
    // bool

}


```

## 4. 编写Repository
```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;


public interface OrderRepository extends JpaRepository<Order, Long> {

}

```

## 5. 测试
```java

```



## 分页查询

```java
Pageable request = PageRequest.of(pageNum, pageSize);
Page<User> page = userRepository.findAll(request);
```

