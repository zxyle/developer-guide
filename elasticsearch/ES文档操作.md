## 介绍
文档相当于mysql的一条记录



## 1. 插入文档(指定ID)

```
PUT /索引名/_doc/{id}
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
POST /索引名/_doc
{
    "name": "Jack",
    "age": 27,
    "gender": "man"
}
```

注意:
- 会自动生成一个id, id 在`_id`属性里
- 如果不带id，多次POST操作, 全是新增操作
- 如果带id，再次POST是更新操作(全部替换)

响应信息:
```json
{
    "_index": "test",  # 索引
    "_type": "_doc",   # 类型 - 文档
    "_id": "Zvm98HkBIk1ld9uKSDnS",  # 随机生成 唯一标识
    "_version": 1,  # 版本
    "result": "created",  # 结果， 创建成功
    "_shards": {  # 分片
        "total": 2,  # 分片 - 总数
        "successful": 1,  # 分片 - 成功
        "failed": 0   # 分片 - 失败
    },
    "_seq_no": 8,
    "_primary_term": 1
}
```



## 更新文档PUT(带ID)

> 全量更新



## 更新文档PUT(不带ID)



## 更新文档POST(带ID)

- 重新POST(注意_version的变化)
- POST `/{index}/_doc/{id}/_update`  { "doc": {} } 会对比原来的数据, 没更新就不更新
- POST 不带`_update` 不会检查原数据，一直都是更新操作 body 不带doc 属性



## 局部更新

只更新部分字段

```
POST /索引名/_update/ID

{
	"doc": {
		// 文档
	}
}
```





## 删除文档(指定ID)

不会立即被删除，只是标记成逻辑删除

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
    "result": "deleted",  # 标记为删除
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

POST /索引名/_delete_by_query

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



## 查看文档数量

```http
GET /索引名/_count


```

