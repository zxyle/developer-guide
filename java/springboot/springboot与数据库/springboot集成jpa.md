
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



## 3. 主启动类

```java
// 主启动类增加 开启JPA审计

@EnableJpaAuditing
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
@EntityListeners(AuditingEntityListener.class) // JPA 审计
public class Order {
    // 数据库每一个字段对应一个属性
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @CreatedDate
    private Date createTime;

    @LastModifiedDate
    private Date updateTime;
    
    // 创建人
    // @CreatedBy 
    
    // 修改人
    // @LastModifiedBy
    
    // name
    // age
    // bool

}


```



常用注解：

| 注解            | 作用                                       | 取值                                                         |
| --------------- | ------------------------------------------ | ------------------------------------------------------------ |
| @Entity         | 标记一个类为实体类，将映射到指定的数据库表 |                                                              |
| @Table          |                                            | name: 指定表名 <br />catalog： 数据库目录<br />schema： 模式 <br />indexes |
| @Id             | 主键                                       |                                                              |
| @GeneratedValue | 主键的生成策略(strategy)                   | GenerationType.IDENTITY： 自增主键 <br />GenerationType.TABLE <br />GenerationType.SEQUENCE <br />GenerationType.IDENTITY <br />GenerationType.AUTO JPA自动选择合适的策略 |
| @Column         |                                            | name: 字段名 <br />unqiue <br />nullable<br />length: 字段长度，如果是`varchar`可以指定 columnDefinition: 可以指定Java不存在的字段类型，如text |
| @Transient      | 标记一个数据库不存在的字段(属性)           |                                                              |



## 4. 编写Repository

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;


public interface OrderRepository extends JpaRepository<Order, Long> {

}

```



常用方法:

| 方法                                                       | 来自类                     | 作用         |
| ---------------------------------------------------------- | -------------------------- | ------------ |
| `<S extends T> S save(S entity);`                          | CrudRepository             | 保存单条数据 |
| `<S extends T> Iterable<S> saveAll(Iterable<S> entities);` | CrudRepository             | 批量保存     |
| `Optional<T> findById(ID id);`                             | CrudRepository             |              |
| `boolean existsById(ID id);`                               | CrudRepository             |              |
| `Iterable<T> findAll();`                                   | CrudRepository             |              |
| `Iterable<T> findAllById(Iterable<ID> ids);`               | CrudRepository             |              |
| `long count();`                                            | CrudRepository             |              |
| `void deleteById(ID id);`                                  | CrudRepository             |              |
| `void delete(T entity);`                                   | CrudRepository             |              |
| `void deleteAll(Iterable<? extends T> entities);`          | CrudRepository             |              |
| `void deleteAll();`                                        | CrudRepository             |              |
| `Iterable<T> findAll(Sort sort);`                          | PagingAndSortingRepository |              |
| `Page<T> findAll(Pageable pageable);`                      | PagingAndSortingRepository |              |
|                                                            |                            |              |





## 5. 测试

```java

```



## 分页查询

```java
Pageable request = PageRequest.of(pageNum, pageSize);
Page<User> page = userRepository.findAll(request);
```

