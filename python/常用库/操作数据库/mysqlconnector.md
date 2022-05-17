



### 介绍

MySQL官方出的连接工具



### 安装

```bash
pip install mysql-connector-python==8.0.29
```



### 示例

```python
import mysql.connector
from mysql.connector import errorcode


class MySQL:
    def __init__(self, **kwargs):
        self.cursor = None
        self.cnx = None
        self.status = False
        self.user = kwargs.get("user", "root")
        self.password = kwargs.get("password", "123456")
        self.host = kwargs.get("host", "127.0.0.1")
        self.port = kwargs.get("port", "3306")
        self.database = kwargs.get("database", "test")
        self.raise_on_warnings = kwargs.get("raise_on_warnings", True)
        self.connection_timeout = kwargs.get("connection_timeout", 5)
        self.pool_size = kwargs.get("pool_size", 1)

        if not self.cursor or not self.cnx:
            self._connect()

    def _connect(self):
        config = {
            'user': self.user,
            'password': self.password,
            'host': self.host,
            'database': self.database,
            'port': self.port,
            'raise_on_warnings': self.raise_on_warnings,
            'connection_timeout': self.connection_timeout,
            'pool_size': self.pool_size,
        }

        try:
            self.cnx = mysql.connector.connect(**config)
        except mysql.connector.Error as err:
            if err.errno == errorcode.ER_ACCESS_DENIED_ERROR:
                print("用户名或密码有问题")
            elif err.errno == errorcode.ER_BAD_DB_ERROR:
                print("数据库不存在")
            else:
                print(err.errno)
        else:
            self.cursor = self.cnx.cursor()
            self.status = True
            return self.cursor

    def _close(self):
        if not self.status:
            print(f"数据库: {self.host}未连接.")
            return
        if self.cursor:
            self.cursor.close()

        if self.cnx:
            self.cnx.close()

    def __enter__(self):
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        self._close()


if __name__ == '__main__':
    connection = {'host': '120.78.219.230', 'user': 'kaihai', 'password': '!Q9s05XnbiTfR3Uu', 'database': 'energy'}
    with MySQL(**connection) as my:
        print(my.status)
        sql = "select count(*) from sys_area"
        my.cursor.execute(sql, )
        print(my.cursor.fetchone())

        insert_sql = ("INSERT INTO person "
                      "(`name`,`age`) "
                      "VALUES (%s, %s)")
        my.cursor.execute(insert_sql, ('zx', 11))
        my.cnx.commit()

```

