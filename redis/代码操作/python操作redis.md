## 安装依赖

`pip install redis==3.2.1`



## 示例代码

```python
import redis

pool = redis.ConnectionPool().from_url("redis://localhost:6379/0")
# pool = redis.ConnectionPool(host="127.0.0.1", port=6379, db=0, password=None)
r = redis.Redis(connection_pool=pool)

print(r.ping())
```

