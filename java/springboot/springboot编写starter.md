

## stater是什么?
场景启动器



## 编写步骤

- 创建 xxx-spring-boot-starter maven工程

- 引入jar包
- 编写`AutoConfiguration` 配置类
- 在`resources\META-INF`目录下, 创建`spring.factories`文件, 将自动配置添加进去



## spring.factories模板

```
org.springframework.boot.autoconfigure.EnableAutoConfiguration=com.example.springbootwithstarter.MyAutoConfiguration
```
