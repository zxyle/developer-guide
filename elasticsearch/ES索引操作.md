## 介绍
ES的索引可以理解为mysql的数据库

## 1. 创建索引
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
```
GET /索引名
```

响应信息:
```json
{
    "索引名": {
        "aliases": {},
        "mappings": {},
        "settings": {
            "index": {
                "creation_date": "1623239329897",
                "number_of_shards": "1",
                "number_of_replicas": "1",
                "uuid": "-90ySoL4SReG3HV6OsZsCQ",
                "version": {
                    "created": "7080099"
                },
                "provided_name": "goubi"
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
| 1    | health         |          |      |      |
| 2    | status         |          |      |      |
| 3    | index          | 索引名称  |      |      |
| 4    | uuid           |          |      |      |
| 5    | pri            |          |      |      |
| 6    | rep            |          |      |      |
| 7    | docs.count     |          |      |      |
| 8    | docs.deleted   |          |      |      |
| 9    | store.size     |          |      |      |
| 10   | pri.store.size |          |      |      |


## 查看索引设置信息
```
GET /index/_settings
```

## 查看索引映射信息
```
GET /index/_mapping
```