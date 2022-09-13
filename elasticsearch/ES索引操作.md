## 介绍
ES的索引可以理解为mysql的数据库

## 1. 创建索引

> 类似mysql: CREATE DATABASE xxx;

```
PUT /索引名
```

响应信息:
```json
{
    "acknowledged": true,
    "shards_acknowledged": true,
    "index": "索引名"
}
```

## 2. 查看索引信息

> 类似mysql： SHOW CREATE DATABASE xxx

```
GET /索引名
```

响应信息:
```json
{
    "索引名": {
        "aliases": {}, # 别名
        "mappings": {}, # 映射
        "settings": {   # 设置
            "index": {  # 设置 - 索引
                "creation_date": "1623239329897",  # 索引创建时间
                "number_of_shards": "1",   # 主分片数量
                "number_of_replicas": "1",  # 副分片数量
                "uuid": "-90ySoL4SReG3HV6OsZsCQ",  # 索引唯一标识
                "version": {  # 索引版本
                    "created": "7080099"
                },
                "provided_name": "shopping"  # 索引名称
            }
        }
    }
}
```

字段含义:
- `aliases`:  别名
- `mappings`: 映射信息
- `settings`: 索引设置信息

## 3. 删除索引
```
DELETE /索引名
```

响应信息:
```json
{
    "acknowledged": true
}
```

## 4. 查看所有索引

> SHOW DATABASES;

```
GET /_cat/indices?v
```

响应信息:
```
health status index    uuid                   pri rep docs.count docs.deleted store.size pri.store.size
yellow open   world    dRa85ll8SLagjsJaY-wkNw   1   1          0            0       208b           208b
yellow open   test     hcHRqxVFSJKXC1kS_FMWkA   1   1          3            0     12.8kb         12.8kb
yellow open   students B18sNW3mToWhRMAkVFrTHQ   3   2          0            0       624b           624b
yellow open   hello    3fyu9nasSGuRV7nUQw5C0w   1   1          0            0       208b           208b
yellow open   user     zZvrBgbTTROPa2d5eSbM2w   1   1          1            0      3.8kb          3.8kb
yellow open   users    gjBqDrbfRTamNcQf-5eiyQ   1   1          4            4      6.2kb          6.2kb
yellow open   shopping nxDf3j11RemGO5CGeIcbvw   1   1         11            0     22.3kb         22.3kb
```

字段含义:
| 序号 | 字段           | 含义     | 备注 | 示例 |
| ---- | -------------- | -------- | ---- | ---- |
| 1    | health         | 当前服务器健康状态： green(集群完整) yellow(单点正常、集群不完整) red(单点不正常) |      |      |
| 2    | status         | 索引打开、关闭状态 |      |      |
| 3    | index          | 索引名称  |      |      |
| 4    | uuid           | 索引统一编号 |      |      |
| 5    | pri            | 主分片数量 |      |      |
| 6    | rep            | 副本数量 |      |      |
| 7    | docs.count     | 可用文档数量 |      |      |
| 8    | docs.deleted   | 文档删除状态（逻辑删除） |      |      |
| 9    | store.size     | 主分片和副分片整体占空间大小 |      |      |
| 10   | pri.store.size | 主分片占空间大小 |      |      |



## 查看索引设置信息

```
GET /index/_settings
```

## 查看索引映射信息
```
GET /index/_mapping
```



## 修改索引设置

```http
PUT /index/_settings

{
	"index": {"max_result_window": 5000000}
}
```

