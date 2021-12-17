## 介绍

映射Mapping , 类似于定义表结构，为每个字段添加数据类型、长度、约束



## 创建mapping

```
PUT /索引名/_mapping

{
    "properties": {
        "name": {
            "type": "text",
            "index": true
        },
        "sex": {
            "type": "text",
            "index": false
        },
        "age": {
            "type": "long",
            "index": false
        }
    }
}
```

- type: 索引类型 参考下表
- index: 是否会被索引, true-会被索引,可以用来搜索， false-字段不会被索引，不能用来搜索
- format: 如果type类型为date， 则可以指定日期格式 如`yyyy-MM-dd HH:mm:ss||yyyy-MM-dd||epoch_millis`
- store: 是否将数据进行独立存储，默认为 false， 原始文本存储在_source里, 这个会解析得快，但也占用更多空间
- analyzer： 分词器  如 `ik_max_word`

## 查询索引

```
# 两种方法
GET /索引名/_mapping
GET /索引名
```





## 索引类型

| 类型         | 说明                         |      |
| ------------ | ---------------------------- | ---- |
| text         | 可分词(默认类型)             |      |
| keyword      | 不可分词，当成整体进行匹配   |      |
| long         |                              |      |
| integer      |                              |      |
| short        |                              |      |
| byte         |                              |      |
| double       |                              |      |
| float        |                              |      |
| half_float   |                              |      |
| scaled_float | 高精度浮点数                 |      |
| date         | 日期类型 formate可以指定格式 |      |
| array        | 数组                         |      |
| object       | 对象                         |      |
| nested       |                              |      |
|              |                              |      |
|              |                              |      |

