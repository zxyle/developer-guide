## 介绍

Hive是建立在Hadoop上的数据仓库基础构架，它提供一系列的工具，可以进行数据提取、转换、加载(ETL)



## 原理

HiveQL(HQL) 转化成MapReduce 直接查询Hadoop数据 



## Metastore

元数据，存储包括表名、表的列和分区及其属性，表的数据所在目录， 默认使用Derby数据库，可以切换到Mysql.

| 表名       | 作用 |
| ---------- | ---- |
| dbs        |      |
| tbls       |      |
| columns_v2 |      |
|            |      |
|            |      |
|            |      |
|            |      |



## 大数据引擎

- 第一代大数据引擎 MapReduce
- 第二代大数据引擎 Tez
- 第三代大数据引擎 Spark
- 第四代大数据引擎 Flink



## hive命令

参数：

- -e “sql”  直接执行sql



## 设置

- set命令 （仅当前会话有效）
- set hive.cli.print.current.db=true; 显示操作数据库
- set hive.cli.print.header=true;  字段名前面加上表名



## hive历史命令

~/.hivehistory



## 默认数据库为default



## 数据存储在hdfs /user/hive/warehouse



## Hive 与MySQL对比



