## 简单查询(带ID)
```
GET /索引名/_doc/{id}
```

返回含义:
- `_index`        在那个索引(库)
- `_type`         在那个类型(表)
- `_id`           记录id
- `_version`      版本号
- `_seq_no`       并发控制字段， 每次更新就会+1， 用来做乐观锁
- `_primary_term` 同上，主分片重新分配，如重启就会变化
- `_found`         布尔值 查询是否成功
- `_source`  查询结果



## 乐观锁操作

更新携带`?if_seq_no=0&if_primary_term=1`

如果`if_seq_no`不一致则不更新


## 批量操作
两行作为一个整体
```
POST /{index}/{type}/_bulk

{"index": {"_id": "1"}}
{"name": "John Doe"}
{"index": {"_id": "2"}}
{"name": "Jane Doe"}
```

## 导入测试数据
```
POST /bank/account/_bulk
```
https://raw.githubusercontent.com/elastic/elasticsearch/master/docs/src/test/resources/accounts.json


## 高级查询


### 带参数查询
```
GET /{index}/_search?q=last_name:Smith
```

### 查询表达式
```
GET /{index}/_search
{
    "query" : {
        "match" : {
            "last_name" : "Smith"
        }
    }
}
```


### 带过滤器查询
```
GET /{index}/_search
{
    "query" : {
        "bool": {
            "must": {
                "match" : {
                    "last_name" : "smith" 
                }
            },
            "filter": {
                "range" : {
                    "age" : { "gt" : 30 } 
                }
            }
        }
    }
}
```

### 模糊查询
```
GET /{index}/_search
{
    "query" : {
        "match" : {
            "about" : "rock climbing"
        }
    }
}
```

## 多字段匹配
查询title或者sourceWebPageTitle包含honda 都满足要求
```json
{
    "query":{
        "multi_match":{
            "query": "honda",
            "fields": ["title", "sourceWebPageTitle"]
        }
    }
}
```

## bool 复合查询



## 文档
https://www.elastic.co/guide/cn/elasticsearch/guide/current/index.html