http://mybatis.org/spring-boot-starter/mybatis-spring-boot-autoconfigure/

## 引入依赖

```xml
<!--mybatis的starter依赖-->
<dependency>
  <groupId>org.mybatis.spring.boot</groupId>
  <artifactId>mybatis-spring-boot-starter</artifactId>
  <version>2.2.2</version>
</dependency>

<!--mysql驱动-->
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-java</artifactId>
  <scope>runtime</scope>
</dependency>

<!--postgresql驱动-->
<dependency>
  <groupId>org.postgresql</groupId>
  <artifactId>postgresql</artifactId>
  <scope>runtime</scope>
  <version>42.5.0</version>
</dependency>
```



## 编写配置文件

```properties
# mysql配置
spring.datasource.username=root
spring.datasource.password=123456
spring.datasource.url=jdbc:mysql://127.0.0.1:3306/spring_boot_mybatis?serverTimezone=GMT%2B8&useUnicode=true&characterEncoding=utf-8
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# postgresql配置
spring.datasource.username=postgres
spring.datasource.password=mysecretpassword
spring.datasource.url=jdbc:postgresql://127.0.0.1:5432/energy
spring.datasource.driver-class-name=org.postgresql.Driver

# mybatis (https://mybatis.org/mybatis-3/configuration.html#settings)
mybatis.mapper-locations=classpath:mappers/*.xml
mybatis.configuration.map-underscore-to-camel-case=true
mybatis.type-aliases-package=com.example.springbootwithmybatis.pojo
mybatis.configuration.cache-enabled=true

# 日志
logging.level.com.example.springbootwithmybatis.dao=debug
```



## 编写实体类

```java
import lombok.Data;
import lombok.ToString;

@Data
@ToString
public class Student {
    /**
     * 主键ID
     */
    private Long id;

    /**
     * 创建时间
     */
    private Date createTime;

    /**
     * 修改时间
     */
    private Date updateTime;

    /**
     * 姓名
     */
    private String name;

    /**
     * 年龄
     */
    private Integer age;
}
```



## 编写Mapper

```java
import org.apache.ibatis.annotations.*;

import java.util.List;

@Mapper
public interface StudentMapper {

    @Select("select * from student")
    List<Student> list();

    @Insert({"insert into student(name, age) values(#{name}, #{age})"})
    @Options(useGeneratedKeys = true, keyProperty = "id")
    int add(Student student);

    @Select("SELECT * FROM student WHERE name = #{name111}")
    Student findByName(@Param("name111") String name);
}
```



## 编写XML

在resources\mappers\StudentMapper.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.example.demo.StudentMapper">


</mapper>
```



## 测试方法

```java
@Autowired
StudentMapper studentMapper;

@Test
void contextLoads() {
  // 新增
  Student student = new Student();
  student.setName("zx");
  student.setAge(19);
  studentMapper.add(student);

  // 查询所有
  System.out.println(studentMapper.list());

  // 按条件查询
  // System.out.println(studentMapper.findByName("zx"));
}
```





## SQL

```sql
-- mysql


-- postgresql
create table student
(
    id          integer,
    create_time date,
    update_time date,
    name        varchar,
    age         integer
);
```

