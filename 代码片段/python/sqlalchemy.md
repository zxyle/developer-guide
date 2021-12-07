## 定义Model
```python
from sqlalchemy.ext.declarative import declarative_base

Base = declarative_base()

# ORM test
class User(Base):
    # 表名
    __tablename__ = 'user'

    id = Column(mysql.BIGINT(unsigned=True), primary_key=True, autoincrement=True, nullable=False, comment="主键id")
    create_time = Column(DATETIME, nullable=False, comment="创建时间", server_default=text("NOW()"))
    update_time = Column(DATETIME, nullable=False, comment="更新时间", server_default=text("NOW() ON UPDATE NOW()"))
    name = Column(String(100))
    fullname = Column(String(100))
    nickname = Column(String(100))

    # __table_args__ = (Index('index(zone,status)', 'resource_zone', 'resource_status'), {'comment': "表注释"})
    __table_args__ = ({'comment': "表注释"})  # 添加索引和表注释

    def __repr__(self):
        return "<User(name='%s', fullname='%s', nickname='%s')>" % (
            self.name, self.fullname, self.nickname)
```