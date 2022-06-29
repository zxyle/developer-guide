

### 介绍





### 引入

```xml
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.24</version>
    <scope>provided</scope>
</dependency>
```



### @Data



### @ToString



### @Getter @Setter



### @Builder



### @Singular

```java
@AllArgsConstructor
@NoArgsConstructor
@Data
@Builder
public class Person {
    private String name;
    private int age;
    private String sex;

    @Singular
    private List<String> childrenInfos;
}
```



使用: 

```java
Person person = Person.builder().name("张三").age(18).sex("男")
                .childrenInfo("yzx").childrenInfo("zz").childrenInfo("xx").build();

System.out.println(person);
// Person(name=张三, age=18, sex=男 childrenInfos=[yzx, zz, xx])
```





### @AllArgsConstructor 

全参数构造函数

### @NoArgsConstructor

无参数构造函数



### @NonNull





### @Slf4j

