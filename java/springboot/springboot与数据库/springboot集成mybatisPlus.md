
## 介绍
- [官网地址](https://baomidou.com/)
- [github地址](https://github.com/baomidou/mybatis-plus)



## 引入步骤

- pom
- 配置
- Mapper



## 引入依赖

```xml
<dependency>
  <groupId>com.baomidou</groupId>
  <artifactId>mybatis-plus-boot-starter</artifactId>
  <version>3.2.0</version>
</dependency>
<!--代码生成器-->
<dependency>
  <groupId>com.baomidou</groupId>
  <artifactId>mybatis-plus-generator</artifactId>
  <version>3.4.1</version>
</dependency>
<!-- mysql驱动 -->
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-java</artifactId>
  <scope>runtime</scope>
</dependency>
```



## 添加配置

```properties
```



## 常见注解
- @TableName   如表名不一致, 可以指定
- @TableId     主键注解
- @TableField  和数据库字段不一致的情况

## 增加
```java
User user = new User();
user.setName("TOM");
user.setAge(10);
user.setBirthday(new Date());
user.setId(3);

int i = userMapper.insert(user);
System.out.println(i);
```

## 删除
```java
// userDao.delete();
// userDao.deleteBatchIds();
// userDao.deleteById();
// userDao.deleteByMap();
```

## 更新
```java
// userDao.update()

// 根据id修改数据
User user = new User();
user.setId(1);
user.setName("Helen");
userMapper.updateById(user);
```

## 查询单条
```java
User user = userMapper.selectById(1);
System.out.println(user);
```

## 查询多条
```java
QueryWrapper<User> queryWrapper = new QueryWrapper<>();
// queryWrapper.eq("age", 26);  // 等于查询
queryWrapper.gt("age", 26);  // 大于查询
List<User> users = userMapper.selectList(queryWrapper);
System.out.println(users);
```

## 模糊查询
```java
QueryWrapper<User> queryWrapper = new QueryWrapper<>();
queryWrapper.like("name", "郑");   // %郑%
// queryWrapper.likeLeft()  // %郑
// queryWrapper.likeRight() // 郑%
List<User> users = userMapper.selectList(queryWrapper);
System.out.println(users);
```

## 分页查询
```java
IPage<User> iPage = new Page<>(1, 2);
IPage<User> page = userMapper.selectPage(iPage, null);
System.out.println(page);
System.out.println("总记录数: " + page.getTotal());
page.getRecords().forEach(System.out::println);
```


## 排序查询

## 分组查询
