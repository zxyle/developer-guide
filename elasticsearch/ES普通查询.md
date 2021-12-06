## 介绍

## 查询方式
- URL形式
- DSL形式

放在url上
```
GET bank/_search/?q=*&sort=account_number:asc
```

放在body里 (Query DSL) Domain Sepcified Language
```
GET /bank/_search
{
  "query": {"match_all": {}},
  "sort": [
    {
      "account_number": {
        "order": "asc"
      }
    }
  ]
}

```


## 查询
- `query`
  - `match_all`  查询所有
  - `match`      会进行分词
  - `match_phrase` 短语匹配，将需要匹配的值当成一个整体单词（不分词）进行检索
  - `match_phrase_prefix` 最左前缀查询  智能搜索--以什么开头
  - `multi_match`  多字段匹配, 多个字段包含 就可以返回 (会分词)
  - `term`  精确匹配，非文本字段使用term来检索
  - `terms` 允许指定多个匹配条件
  - `range`  指定范围查找
  - `exists` 包含字段
  - `missing`  不包含字段 (ES5以上取消)
  - `regexp`  正则
  - `prefix` 前缀开头
  - `must`
  - `filter`
- `from`  从哪里开始
- `size`  取几条数据   
- `sort`  排序

- `highlight`: 高亮查询



## 查询所有文档

```
GET /{index}/_search
```

默认1万条



## 分页查询

```
GET /索引名/_search
```

请求体:
```json
{
    "query": {
        "match_all": {}
    },
    "from": 1,
    "size": 2
}
```

响应体:
```json
{
    "took": 4,
    "timed_out": false,
    "_shards": {
        "total": 1,
        "successful": 1,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": {
            "value": 12,
            "relation": "eq"
        },
        "max_score": 1.0,
        "hits": [
            {
                "_index": "shopping",
                "_type": "_doc",
                "_id": "1002",
                "_score": 1.0,
                "_source": {
                    略
                }
            },
            {
                "_index": "shopping",
                "_type": "_doc",
                "_id": "1003",
                "_score": 1.0,
                "_source": {
                    略
                }
            }
        ]
    }
}
```
- `from`: 开始位置(从0开始)  (页码-1) * pageSize
- `size`: 每页大小


## 范围查询

请求体：
```json
{
    "query": {
        "range" : {
            "score" : {
                "gte" : 90,
                "lte" : 100
            }
        }
    }
}
```

## 时间范围查询


## 查询指定字段
> 类似select id, name, age from person;

- `_source`  返回部分字段 举例: `["firstname", "lastname"]`



## 复合查询
### bool 合并多个查询条件
- `must`      多个查询条件的完全匹配,相当于 and
- `must_not`  多个查询条件的相反匹配，相当于 not
- `shuold`    至少有一个查询条件匹配, 相当于 or
- `filter`