## 介绍
文档相当于mysql的一条记录


## 1. 插入文档(指定ID)
```
PUT /{index}/_doc/{id}
{
    "first_name" : "John",
    "last_name" :  "Smith",
    "age" :        25,
    "about" :      "I love to go rock climbing",
    "interests": [ "sports", "music" ]
}
```

注意:
- 多次发送就是全量更新操作, ` _version`会递增
- 一定要带id
- url上的`_doc` 可以换成 `_create`


响应信息:
```json
{
    "_index": "索引名",
    "_type": "_doc",
    "_id": "1001",
    "_version": 1,
    "result": "created",
    "_shards": {
        "total": 2,
        "successful": 1,
        "failed": 0
    },
    "_seq_no": 6,
    "_primary_term": 1
}
```

响应含义:
- `_seq_no`
- `_primary_term`



## 2. 插入文档(随机id/不指定ID)

```
POST /{index}/_doc
{
    "name": "zheng",
    "age": 27,
    "gender": "man"
}
```

注意:
- 会自动生成一个id, id 在`_id`属性里
- 如果不带id，多次POST操作, 全是新增操作
- 如果带id，再次POST是更新操作(TODO? 是全量还是局部更新)

响应信息:
```json
{
    "_index": "test",
    "_type": "_doc",
    "_id": "Zvm98HkBIk1ld9uKSDnS",
    "_version": 1,
    "result": "created",
    "_shards": {
        "total": 2,
        "successful": 1,
        "failed": 0
    },
    "_seq_no": 8,
    "_primary_term": 1
}
```



## 更新文档PUT(带ID)

> 全量更新



## 更新文档PUT(不带ID)



## 更新文档POST(带ID)

- 重新PUT(注意_version的变化)
- POST `/{index}/_doc/{id}/_update`  { "doc": {} } 会对比原来的数据, 没更新就不更新
- POST 不带`_update` 不会检查原数据，一直都是更新操作 body 不带doc 属性



## 删除文档(指定ID)

```
DELETE /{index}/_doc/{id}
```

响应信息:
```json
{
    "_index": "索引名",
    "_type": "_doc",
    "_id": "X_l88HkBIk1ld9uK1jlU",
    "_version": 2,
    "result": "deleted",
    "_shards": {
        "total": 2,
        "successful": 1,
        "failed": 0
    },
    "_seq_no": 5,
    "_primary_term": 1
}
```



## 查询并删除

POST /{index}/_delete_by_query

```json
{
    "query": {
        "bool": {
            "must": [
                {
                    "match": {
                        "modelType": "qi_ye_jing_ying_feng_xian"
                    }
                },
                {
                    "range": {
                        "evalDate": {
                            "lt": "2021-10-01"
                        }
                    }
                }
            ]
        }
    }
}
```



## 查询文档是否存在

```
HEAD /{index}/_doc/{id}
```

- 存在返回`200`状态码
- 不存在返回`404`状态码