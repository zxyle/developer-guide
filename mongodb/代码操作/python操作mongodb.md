## 安装依赖

```bash
pip install pymongo==3.7.2
```



## 示例代码

```python
import pymongo

# MONGO_URI = "mongodb://spider:6Xaohuzof3KLp8BX@10.50.86.170:27017,10.50.86.171:27017,10.50.86.172:27017/spider"
# MONGO_URI = "mongodb://127.0.0.1:27017/spider"
client = pymongo.MongoClient(MONGO_URI)
db = client["spider"] # 数据库
post = db["wenshu"]   # 表
```



## 查询

```python
# 第一个代表条件(where), 第二个为select 指定字段
post.find({}, {"_id": 0})
```



## 新增

```python
from pymongo.errors import DuplicateKeyError

doc = {"name": "zx", "age": 10}
try:
    post.insert_one()
except DuplicateKeyError:
    print("数据重复！")
```



补充增删改查 索引等操作

