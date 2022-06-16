

### docker 使用

```bash
docker pull postgres:14.3

docker run --name some-postgres -p 5432:5432 -e POSTGRES_PASSWORD=mysecretpassword -d postgres:14.3
```

默认用户名和数据库都是 postgres

```yaml
version: '3.1'

services:
  db:
    image: postgres:14.3
    restart: always
    expose:
      - "5432:5432"
    environment:
      POSTGRES_PASSWORD: example

  adminer:
    image: adminer
    restart: always
    ports:
      - "8080:8080"
```





### 层级

database 数据库

schema  架构

table 表
