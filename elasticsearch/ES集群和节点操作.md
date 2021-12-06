## 1. 查看节点信息
```
GET /
```

响应信息:
```json
{
    "name": "MacBook-Pro-3.local",
    "cluster_name": "elasticsearch",
    "cluster_uuid": "N3Lljs9fQaSNZri4k9IIuQ",
    "version": {
        "number": "7.8.0",
        "build_flavor": "default",
        "build_type": "tar",
        "build_hash": "757314695644ea9a1dc2fecd26d1a43856725e65",
        "build_date": "2020-06-14T19:35:50.234439Z",
        "build_snapshot": false,
        "lucene_version": "8.5.1",
        "minimum_wire_compatibility_version": "6.8.0",
        "minimum_index_compatibility_version": "6.0.0-beta1"
    },
    "tagline": "You Know, for Search"
}
```


## 2. 查看所有节点
```
GET /_cat/nodes
```

响应信息:
```
127.0.0.1 16 100 20 2.03   dilmrt * MacBook-Pro-3.local
```

解释:
- 标 * 号为主节点

## 3. 查看es健康状况
```
GET /_cat/health
```

响应信息:
```
1623242431 12:40:31 elasticsearch yellow 1 1 9 9 0 0 12 0 - 42.9%
```

补充解释信息

## 4. 查看主节点
```
GET /_cat/master
```

响应信息:
```
8LTt4Wh2SWOyt2wngJfwXQ 127.0.0.1 127.0.0.1 MacBook-Pro-3.local
```

## 5. 查看集群健康信息
```
GET /_cluster/health
```

响应信息:
```json
{
    "cluster_name": "elasticsearch",
    "status": "yellow",
    "timed_out": false,
    "number_of_nodes": 1,
    "number_of_data_nodes": 1,
    "active_primary_shards": 9,
    "active_shards": 9,
    "relocating_shards": 0,
    "initializing_shards": 0,
    "unassigned_shards": 12,
    "delayed_unassigned_shards": 0,
    "number_of_pending_tasks": 0,
    "number_of_in_flight_fetch": 0,
    "task_max_waiting_in_queue_millis": 0,
    "active_shards_percent_as_number": 42.857142857142854
}
```