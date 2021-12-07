## 安装依赖

```bash
pip install pymongo==3.7.2
```



## 示例代码

```python
import pymongo

# mongo_uri = "mongodb://spider:6Xaohuzof3KLp8BX@10.50.86.170:27017,10.50.86.171:27017,10.50.86.172:27017/spider"
# mongo_uri = "mongodb://127.0.0.1:27017/spider"
client = pymongo.MongoClient(MONGO_URI)
db = client["spider"]
```



补充增删改查 索引等操作

