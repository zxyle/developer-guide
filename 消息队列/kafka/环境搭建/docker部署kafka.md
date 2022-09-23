## 拉取镜像
```bash
docker pull wurstmeister/zookeeper 
docker pull wurstmeister/kafka:latest
```



## 运行镜像

```bash
docker run -d --name zookeeper -p 2181:2181 -t wurstmeister/zookeeper 

docker run -d --name kafka --publish 9092:9092 --link zookeeper \
--env KAFKA_ZOOKEEPER_CONNECT=zookeeper:2181 \
--env KAFKA_ADVERTISED_HOST_NAME=localhost \
--env KAFKA_ADVERTISED_PORT=9092 \
wurstmeister/kafka:latest 
```



