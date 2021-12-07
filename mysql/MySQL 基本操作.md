## 登录与退出

```
# 登录
mysql -uroot -p

# 退出
quit;
```

| 参数 | 说明                   |
| ---- | ---------------------- |
| -u   | 用户名                 |
| -p   | 密码                   |
| -h   | 指定主机地址，默认本地 |
| -P   | 指定端口，默认3306     |
| - V  | 显示版本信息           |



## 数据库操作

```sql
-- 创建数据库
CREATE DATABASE db_name DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- 列出所有数据库
SHOW DATABASES;

-- 显示数据库创建信息
SHOW CREATE DATABASE db_name;

-- 切换数据库
USE db_name;

-- 删除数据库
DROP DATABASE db_name;

-- 修改数据库
ALTER DATABASE db_name;
```



## 表操作

```sql
-- 显示库中所有表
USE db_name;
SHOW TABLES;

-- 创建表
CREATE TABLE `USER` (
  `user_id` int(128) NOT NULL AUTO_INCREMENT,
  `name` varchar(64) NOT NULL,
  `age` int(11) DEFAULT NULL,
  PRIMARY KEY (`user_id`)
) ENGINE=InnoDB
DEFAULT CHARACTER SET=utf8 COLLATE=utf8_general_ci;

-- 修改表（新增一列）
ALTER TABLE user ADD COLUMN sex tinyint(1) NOT NULL COMMENT '性别，女：0，男：1' AFTER `age`;

-- 删除表
DROP TABLE tbl_name;

-- 根据已存在表结构，创建新表
CREATE TABLE new_name LIKE old_name;

-- 修改表名
RENAME TABLE table_name_a TO table_name_b;
```



## 索引操作

```sql
-- https://dev.mysql.com/doc/refman/5.7/en/create-index.html

-- 显示表中所有索引
SHOW INDEXES FROM tbl_name;

-- 删除对应表中的索引
DROP INDEX index_name ON tbl_name;

-- 创建单列索引
CREATE INDEX index_name ON tbl_name(col_name);

-- 创建组合索引
CREATE INDEX index_name ON tbl_name(col_name1, col_name2);

-- 创建索引语法格式
CREATE [UNIQUE|FULLTEXT|SPATIAL] INDEX index_name
    [index_type]
    ON tbl_name (index_col_name,...)
    [index_option]
    [algorithm_option | lock_option] ...

index_col_name:
    col_name [(length)] [ASC | DESC]

ASC 升序  DESC 降序

index_option:
    KEY_BLOCK_SIZE [=] value
  | index_type
  | WITH PARSER parser_name
  | COMMENT 'string'

index_type:
    USING {BTREE | HASH}

algorithm_option:
    ALGORITHM [=] {DEFAULT|INPLACE|COPY}

lock_option:
    LOCK [=] {DEFAULT|NONE|SHARED|EXCLUSIVE}

```



## 视图操作

视图是由一系列表组合而成的虚拟表

```sql
-- 创建视图
CREATE VIEW view_name AS SELECT col_name1, col_name2 FROM tbl_name;

CREATE VIEW viem_name(alias_name1, alias_name2) AS SELECT col_name1, col_name2
FROM tbl_name;


-- 多表视图
CREATE VIEW view_name (id, name, glass) AS SELECT tb1.col1, tb1.col2, tb2.col1
FROM tb1, tb2 WHERE tb1.col1=tb2.col1;


-- 删除视图
DROP VIEW IF EXISTS view_name;

SHOW CREATE VIEW view_name;
```



## 账号操作

```sql
-- 创建账号
create user 'username'@'%' identified  by 'password';

-- 删除账号
drop user 'zheng'@'%';

-- 修改密码

```



## 权限有关
--为该用户添加查询、主从复制等权限 grant select,replication slave,replication client,super on *.* to 'canal'@'%';

- 赋予权限: ``
- 刷新权限: `flush privileges;`
- 回收权限: ``

## insert
```sql
insert into table_name(field1, field2) values (v1, v2);
```

## update
```sql
update table_name set field1=new-value1, field2=new-value2
[WHERE Clause]
```



## delete

```sql
DELETE FROM table_name [WHERE Clause]
```



## select

```
select * from table_name;
```



## where

```

```



## 分组查询 group by

```sql
SELECT address, AVG(age) AS "平均年龄", COUNT(*) as "人数" FROM students GROUP BY students.address;
```

## having
```
```

## 排序 order by
```
order by field asc/desc;
```

## left join

## right join

## join

## limit

## IN / NOT IN

## BETWEEN AND

## LIKE



## truncate

