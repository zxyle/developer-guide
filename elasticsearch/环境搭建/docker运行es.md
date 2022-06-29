## docker compose
```
# elasticsearch.yml
http.host: 0.0.0.0
```

```yaml
version: '3'
services:
  elasticsearch:
    image: elasticsearch:7.4.2
    volumes:
      - D:/developer/dockerdata/elasticsearch/7.4.2/config/elasticsearch.yml:/usr/share/elasticsearch/config/elasticsearch.yml
      - D:/developer/dockerdata/elasticsearch/7.4.2/plugins:/usr/share/elasticsearch/plugins
      - D:/developer/dockerdata/elasticsearch/7.4.2/data:/usr/share/elasticsearch/data
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