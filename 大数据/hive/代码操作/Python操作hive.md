## 安装依赖

```bash
pip install PyHive
```



## 示例代码

```python
from pyhive import hive

conn = hive.Connection(host='127.0.0.1', port=10000, database='dws')

sql = "show tables;"
cur = conn.cursor()
cur.execute(sql)
res = cur.fetchall()

conn.close()
```

