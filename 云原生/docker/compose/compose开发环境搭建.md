使用docker compose 来搭建开发环境

```yaml
version: "3"

services:
  mysql:
    image: mysql:latest
    restart: always
    ports:
      - "3306:3306"
    environment:
      - MYSQL_ROOT_PASSWORD=123456
      - MYSQL_DATABASE=spider
    # volumn
#    - ~/configs:/etc/configs/:ro

  redis:
    image: redis:latest
#    container_name:
    restart: always
    ports:
      - "6379:6379"

  mongo:
    image: mongo:latest
    restart: always
    ports:
      - "27017:27017"


  rabbitmq:
    image: rabbitmq:3-management
    restart: always
    ports:
      - "5672:5672"
      - "15672:15672"
    environment:
      - RABBITMQ_DEFAULT_USER=root
      - RABBITMQ_DEFAULT_PASS=123456

  postgres:
    image: postgres:latest
    restart: always
    ports:
      - "5432:5432"
    environment:
      - POSTGRES_PASSWORD=123456
      - POSTGRES_USER=postgres
```