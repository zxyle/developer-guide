

## 引入依赖

```xml
<dependency>
  <groupId>com.dtflys.forest</groupId>
  <artifactId>forest-spring-boot-starter</artifactId>
  <version>1.5.23</version>
</dependency>
```



## 编写Client

```java
import com.dtflys.forest.annotation.Request;
import org.springframework.stereotype.Component;

@Component
public interface MyClient {

    @Request("http://httpbin.org/ip")
    String helloForest();

}
```





## 调用

```java
@Autowired
private MyClient myClient;

@Test
public void testClient() {
    String result = myClient.helloForest();
    System.out.println(result);
}
```

