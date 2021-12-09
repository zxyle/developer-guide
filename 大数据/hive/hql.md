## 介绍

HiveQL



## 数据库操作

```sql
-- 显示所有数据库, 默认为default数据库
show databases;

-- 创建数据库
create database mydb1;

-- 创建数据库，指定hdfs存储位置
create database mydb2 location '/user/hive/mydb2'

-- 切换数据库
use dbname

-- 删除数据库
drop database mydb2;
```



## 数据表操作

```sql
-- 显示所有表
show tables;

-- 创建表
create table t1(id int, name string);

-- 显示创建表
show create table t1;

-- 显示表结构
DESC t1;

-- 创建表
create table testa (
  id int,
  name string,
  area string
) partitioned by (create_time string) row format delimited fields terminated by ',' stored as textfile;

-- 表增加字段
alter table t2 add columns(age int);

-- 修改表名
alter table t2 rename to t2_bak;

-- 创建表的时候，指定列分隔符和行分隔符 （默认列分隔符^A \001）
create table t5_new(
  id int comment 'ID',
  stu_name string comment 'name',
  stu_birthday date comment 'birthday',
  online boolean comment 'is online'
) row format delimited 
fields terminated by '\t'
lines terminated by '\n';


```



## 加载数据

```sql
LOAD DATA LOCAL INPATH '/root/test_data.txt' INTO TABLE testA PARTITION(create_time='2020-05-11');
```





## 退出

```sql
quit;
```





## 建表语句

```sql
CREATE TABLE IF NOT EXISTS `year_report_dt` (
  `company_name` STRING COMMENT '企业名称',
  `usci` STRING COMMENT '统一社会信用代码',
  `reg_num` STRING COMMENT '注册号',
  `address` STRING COMMENT '地址',
  `phone_num` STRING COMMENT '联系电话',
  `year` STRING COMMENT '年度',
  `status` STRING COMMENT '企业状态',
  `is_online_shop` STRING COMMENT '是否网站网店',
  `is_equity_transfer` STRING COMMENT '是否股权转让',
  `is_foreign_investment` STRING COMMENT '是否对外投资'
  ) 
COMMENT '年报'
PARTITIONED BY (`ds` string COMMENT 'date used by partition')
lifecycle 365;
```



## 单条插入

```sql
insert into table dws_qdsjzx_ptdsjpt_yqyd_indexes_dt
  partition (ds='20210624')
(establish_day,etps_code,run_except_2y_valid,industry_category,	sxbzx_latest_timedelta,	administrative_penalties_times_2y,abnormal_operations_times_2y,run_except_3y_increse_rate,punish_action_3y_increse_rate,punish_action_2y_fake_rate,sxbzx_count_2y,registered_capital)
VAlues(2712,0,0,0,0,0,0,0,0,0,0,50)
```

