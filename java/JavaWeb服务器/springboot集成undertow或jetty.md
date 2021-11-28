## 介绍
Spring Boot 默认使用tomcat作为内置服务器，但也可以切换undertow或jetty



## 使用步骤

### 1. 添加其他服务器starter依赖
pom文件添加`spring-boot-starter-undertow` 或者 `spring-boot-starter-jetty` 依赖

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <!--在这里控制使用undertow还是jetty-->
    <!--<artifactId>spring-boot-starter-undertow</artifactId>-->
    <artifactId>spring-boot-starter-jetty</artifactId>
</dependency>
```



### 2. 排除默认的tomcat服务器

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <exclusions>
        <!--移除默认的Tomcat依赖-->
        <exclusion>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
        </exclusion>
    </exclusions>
</dependency>
```



## 配置项

