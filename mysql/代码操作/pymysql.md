

## 安装依赖

```bash
pip install pymysql
```



## 示例代码

```python
import pymysql

db = pymysql.connect(host="IP", port=3306, user="账号名", passwd="密码",
                     charset='utf8mb4', db="库名",cursorclass=pymysql.cursors.DictCursor)

# 游标
cursor = db.cursor()

# SQL 插入语句
sql = 'INSERT INTO `person`(name, age) VALUES (%s, %s)'
try:
    # 执行sql语句
    cursor.execute(sql, ('zheng', 20))
    # 提交到数据库执行
    db.commit()
except:
    # 如果发生错误则回滚
    db.rollback()

# 关闭数据库连接
db.close()
```

