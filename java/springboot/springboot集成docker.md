## pom文件添加plugin

```xml
<plugin>
  <groupId>com.spotify</groupId>
  <artifactId>dockerfile-maven-plugin</artifactId>
  <version>1.4.13</version>
  <executions>
    <execution>
      <id>default</id>
      <goals>
        <goal>build</goal>
        <goal>push</goal>
      </goals>
    </execution>
  </executions>
  <configuration>
    <repository>zxyle/${project.name}</repository>
    <tag>${project.version}</tag>
    <buildArgs>
      <JAR_FILE>${project.build.finalName}.jar</JAR_FILE>
    </buildArgs>
    <dockerfile>Dockerfile</dockerfile>
  </configuration>
</plugin>
```



## 编写dockerfile

```dockerfile
# 添加 Java 8 镜像来源
#FROM java:8
FROM zxyle/oracle-server-jre:8u202

# 添加参数
ARG JAR_FILE

# 添加 Spring Boot 包
ADD target/${JAR_FILE} app.jar

# 执行启动命令
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
```





## 编写docker-compose.yml

```yaml
version: '3'
services:
  springboot:
    image: zxyle/spring-boot-with-docker:0.0.1-SNAPSHOT
    ports:
      - 9090:8080

```



## 启动

```bash
# 编译及打包
mvn clean package -Dmaven.test.skip=true

# 使用docker-compose运行起来
docker-compose up

# 访问测试
curl http://127.0.0.1:9090/
```







## 待确认

```dockerfile
FROM maven:3-jdk-8-alpine

WORKDIR /usr/src/app

COPY . /usr/src/app
RUN mvn package

ENV PORT 5000
EXPOSE $PORT
CMD [ "sh", "-c", "mvn -Dserver.port=${PORT} spring-boot:run" ]

```



