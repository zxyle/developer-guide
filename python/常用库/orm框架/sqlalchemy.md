## Sqlalchemy ORM示例
```python
# pip install sqlalchemy==1.4.28 mysql-connector-python==8.0.21

from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy import Column, create_engine, text, String, Index

from sqlalchemy.orm import sessionmaker
from sqlalchemy.dialects import mysql
from sqlalchemy.dialects.mysql import TINYINT, INTEGER, FLOAT, BIGINT, VARCHAR, TEXT, DATETIME, LONGTEXT, MEDIUMTEXT

Base = declarative_base()

engine = create_engine('mysql+mysqlconnector://root:12345678@127.0.0.1:3306/spider?charset=utf8', echo=False)

session = sessionmaker(bind=engine)
session = session()


# ORM test
class User(Base):
    # 表名
    __tablename__ = 'user'

    id = Column(mysql.BIGINT(unsigned=True), primary_key=True, autoincrement=True, nullable=False, comment="主键id")
    create_time = Column(DATETIME, nullable=False, comment="创建时间", server_default=text("NOW()"))
    update_time = Column(DATETIME, nullable=False, comment="更新时间", server_default=text("NOW() ON UPDATE NOW()"))
    name = Column(String(100))
    fullname = Column(String(100))
    nickname = Column(String(100), default=None)

    # __table_args__ = (Index('index(zone,status)', 'resource_zone', 'resource_status'), {'comment': "表注释"})
    __table_args__ = ({'comment': "表注释"})  # 添加索引和表注释

    def __repr__(self):
        return "<User(name='%s', fullname='%s', nickname='%s')>" % (
            self.name, self.fullname, self.nickname)


if __name__ == '__main__':
    # Base.metadata.drop_all(engine)
    Base.metadata.create_all(engine)
```



## Sqlalchemy Core示例

```python
# 文档地址: https://docs.sqlalchemy.org/en/13/core/tutorial.html
# pip install sqlalchemy

import sqlalchemy.dialects.mysql as mysql
from sqlalchemy import Table, Column, MetaData, text, DATETIME, String
from sqlalchemy import create_engine

engine = create_engine("mysql+pymysql://root:12345678@127.0.0.1:3306/car?charset=utf8mb4", echo=False)

# 定义表语句
metadata = MetaData()

template = Table("template", metadata,
                 Column("id", mysql.BIGINT(unsigned=True), primary_key=True, autoincrement=True, nullable=False,
                        comment="主键id"),
                 Column("create_time", DATETIME, nullable=False, comment="创建时间",
                        server_default=text("NOW()")),
                 Column("update_time", DATETIME, nullable=False, comment="更新时间",
                        server_default=text("NOW() ON UPDATE NOW()")),
                 Column("name", String(32), comment="姓名"),
                 comment="模板表",
                 )

# 删除表语句
metadata.drop_all(engine)

# 创建表语句
metadata.create_all(engine)

with engine.connect() as conn:
    # 插入记录语句
    ins = template.insert().values(name='Zheng')
    result = conn.execute(ins)
    print(result)
    result2 = conn.execute(template.insert(), [
        {'name': 'jack@yahoo.com'},
        {'name': 'jack@msn.com'},
        {'name': 'www@www.org'},
        {'name': 'wendy@aol.com'},
    ])

    print(result2)

    # 查询语句
    # 选择全部字段
    # s = select([users])
    # 选择字段
    # s = select([users.c.name, users.c.fullname])
    # result = conn.execute(s)
    # print(result.fetchall())
    # # for row in result:
    # #     print(row)
```



## 连接池设置

| 参数         | 含义 |
| ------------ | ---- |
| pool_recycle |      |
| pool_size    |      |
| pool_timeout |      |
| max_overflow |      |

## MySQL

```python
from sqlalchemy.dialects.mysql import TINYINT, INTEGER, FLOAT, BIGINT, VARCHAR, TEXT, DATETIME, LONGTEXT, MEDIUMTEXT
```



## 提交 & 回滚

```python
session.commit()

session.rollback()

session.close()

session.remove()
```





## 新增单条

```python
# insert into user(name, fullname, nickname) values('ed', 'Ed Jones', 'edsnickname')
ed_user = User(name='ed', fullname='Ed Jones', nickname='edsnickname')
session.add(ed_user)
session.commit()
```





## 批量新增

```python
# 添加多个对象
session.add_all([
     User(name='wendy', fullname='Wendy Williams', nickname='windy'),
     User(name='mary', fullname='Mary Contrary', nickname='mary'),
     User(name='fred', fullname='Fred Flintstone', nickname='freddy')])
 
# commit() 刷新对数据库的其余更改，并提交事务
session.commit()  
```



## 查询单条

```python
# select * from user where username='ed' limit 1
session.query(models.User).filter(models.User.username == 'ed').first()
```



## 查询全部

```python
# select * from user where username='xxx'
session.query(models.User).filter(models.User.username == username).all()
```



## 删除

```python
# DELETE FROM user WHERE user.username = 'ed'
session.query(Users).filter(Users.name == "ed").delete()
session.commit()
```



## 排序

```python
# SELECT *  FROM user ORDER BY user.create_time DESC
session.query(User).order_by(User.create_time.desc()).all()　
```



## 更新

```python
# 
session.query(Users).filter_by(id=1).update({'name': "Jack"})
```



## count

```python
session.query(models.User).count()
```



## 执行原生SQL

```python
cursor = session.execute('select count(*) from user')
result = cursor.fetchall()
```

