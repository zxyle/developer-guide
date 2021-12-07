
## 介绍
阿里出品的数据源 [github](https://github.com/alibaba/druid)

## 参数文档
补充官方参数文档

## spring xml版本
```xml
<!--druid数据源对象-->
<bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
    <property name="url" value="jdbc:mysql://localhost:3306/spring-tx?serverTimezone=Asia/Shanghai"/>
    <property name="username" value="root"/>
    <property name="password" value="123456"/>
    <!--连接池中最多支持多少个活动会话-->
    <property name="maxActive" value="5"/>
</bean>
```

## spring java config版本
```java
/**
 * 创建druid数据源
 * @return druid数据源
 */
@Bean
public DataSource dataSource() {
    DruidDataSource dataSource = new DruidDataSource();
    dataSource.setUrl(url);
    dataSource.setUsername(username);
    dataSource.setPassword(password);
    dataSource.setMaxActive(5);
    return dataSource;
}
```

## spring boot版本
### 1. pom文件引依赖
```xml
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid-spring-boot-starter</artifactId>
    <version>1.2.3</version>
</dependency>
```

### 2. `application.properies`添加配置信息
```properties
spring.datasource.type=com.alibaba.druid.pool.DruidDataSource
spring.datasource.druid.initial-size=5
spring.datasource.druid.min-idle=5
spring.datasource.druid.max-active=20
spring.datasource.druid.time-between-eviction-runs-millis=60000
spring.datasource.druid.min-evictable-idle-time-millis=300000
spring.datasource.druid.validation-query=SELECT 1
spring.datasource.druid.test-while-idle=true
spring.datasource.druid.test-on-borrow=false
spring.datasource.druid.test-on-return=false
spring.datasource.druid.pool-prepared-statements=true
spring.datasource.druid.max-pool-prepared-statement-per-connection-size=20
spring.datasource.druid.filters=stat,wall,slf4j
spring.datasource.druid.connection-properties=druid.stat.mergeSql\=true;druid.stat.slowSqlMillis\=5000
spring.datasource.druid.web-stat-filter.enabled=true
spring.datasource.druid.web-stat-filter.url-pattern=/*
spring.datasource.druid.web-stat-filter.exclusions=*.js,*.gif,*.jpg,*.bmp,*.png,*.css,*.ico,/druid/*
spring.datasource.druid.stat-view-servlet.url-pattern=/druid/*
spring.datasource.druid.stat-view-servlet.allow=127.0.0.1
spring.datasource.druid.stat-view-servlet.deny=192.168.1.73
spring.datasource.druid.stat-view-servlet.reset-enable=false
spring.datasource.druid.stat-view-servlet.login-username=admin
spring.datasource.druid.stat-view-servlet.login-password=123456
```

