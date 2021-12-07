
## spring boot应用
```yaml
version: '3'
services:
  app:
    image: oracle-server-jre:8u202
    restart: always
    ports:
      - 8080:8080
    volumes:
      - ./target/demo-0.0.1-SNAPSHOT.jar:/app.jar

    command: java -jar /app.jar
```

