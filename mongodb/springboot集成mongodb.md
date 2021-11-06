
## 介绍

## 操作步骤

### 1. 引入依赖
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-mongodb</artifactId>
</dependency>
```

### 2. 添加配置信息
```properties
# mongodb
spring.data.mongodb.authentication-database=admin
spring.data.mongodb.host=localhost
spring.data.mongodb.port=27017
spring.data.mongodb.username=root
spring.data.mongodb.password=example
spring.data.mongodb.database=persons
```

### 3. 常见操作
```java
@Autowired
MongoTemplate mongoTemplate;

// 插入对象
mongoTemplate.insert(obj);

// 删除

// 更新

// 查询
Query query = new Query();
query.addCriteria(Criteria.where("name").is("Tom"));

List<Person> people = mongoTemplate.find(query, Person.class);
System.out.println(people);
```