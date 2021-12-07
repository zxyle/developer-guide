
## 结构层次
- Database
- Collection
- Document


## 逻辑操作符
- `$lt`:  小于
- `$gte`: 大于或等于
- `$lte`: 小于或等于
- `$ge`:  大于查询
- `$eq`:  等于

## 时间范围查询
```
db.spider_api.find({"create_time": {"$gt": ISODate("2018-03-01T00:00:00.000+08:00"), "$lt": ISODate("2018-03-31T23:59:59.000+08:00")}})
```

## 修改字段名称
```
db.test.update({}, {$rename : {"abc" : "def"}}, false, true)
```


## 模糊查询

## 建立唯一索引
```
db.collection.ensureIndex({firstname: 1, lastname: 1}, {unique: true});
```

## 统计文档数量
```
db.collection.find().count();
```

## 清空所有文档
```
db.collection.remove({});
```

## 备份和恢复
导出单个表(collection)
```
mongodump --host 主机 -u 账号 -p 密码 --authenticationDatabase 认证数据库 --port 端口 -d 数据库 -c 表名  -o a.bak
```

导入单个表
```
mongorestore --host 主机 -u 账号 -p 密码 --port 端口 --authenticationDatabase 认证数据库 -d 数据库  -c 表名 bson文件位置
```

更多信息参考: https://www.cnblogs.com/xiaotengyi/p/6393972.html



## 索引操作

```
创建唯一索引:
db.COLLECTION_NAME.ensureIndex({"uuid":1},{"unique":true})
db.COLLECTION_NAME.ensureIndex({"hash":1},{"unique":true})

创建索引:
1升序 -1降序
db.COLLECTION_NAME.ensureIndex({"create_time":1}) 
db.COLLECTION_NAME.ensureIndex({"case_no":1}) 
db.COLLECTION_NAME.ensureIndex({"name":1}) 
db.COLLECTION_NAME.ensureIndex({"uen":1}) 


查看索引
db.COLLECTION_NAME.getIndexes()

删除单个索引
db.COLLECTION_NAME.dropIndex("INDEX-NAME")

删除所有索引
db.COLLECTION_NAME.dropIndexes()
```

