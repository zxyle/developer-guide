

## 单独运行



## compose编排

```yaml
version: '3'
services:
  mysql:
    image: mysql:8.0.17
    ports:
      - 3307:3306
    environment:
      MYSQL_ROOT_PASSWORD: 123456
      # create a database
      MYSQL_DATABASE: spider
```





## k8s编排

