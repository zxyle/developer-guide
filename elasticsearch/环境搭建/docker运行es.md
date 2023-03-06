## docker compose

### 1. 初始化工作

```bash
# 创建目录
mkdir -p es/config
mkdir -p es/data
mkdir -p es/plugins
```



### 2. 创建配置文件

vim es/config/elasticsearch.yml

```yaml
http.host: 0.0.0.0
```



### 3. 编写docker-compose.yml文件

```yaml
version: '3'
services:
  elasticsearch:
    image: elasticsearch:7.4.2
    volumes:
      - ./es/config/elasticsearch.yml:/usr/share/elasticsearch/config/elasticsearch.yml
      - ./es/plugins:/usr/share/elasticsearch/plugins
      - ./es/data:/usr/share/elasticsearch/data
    ports:
      - "9200:9200"
      - "9300:9300"
    environment:
      discovery.type: single-node
      ES_JAVA_OPS: -Xms128m -Xmx256m

  kibana:
    image: kibana:7.4.2
    ports:
      - "5601:5601"
    depends_on:
      - elasticsearch
```



## k8s

```yaml

```