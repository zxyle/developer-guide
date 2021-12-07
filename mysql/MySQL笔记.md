## 创建模板表
```sql
# 模板表
# tinyint:   0 ~ 255
# smallint:  0 ~ 65535
# mediumint: 0 ~ 1677,7215
# int:       0 ~ 42,9496,7295
# bigint:    0 ~ 1844,6744,0737,0955,1615

CREATE TABLE `表名` (
  `id` int unsigned NOT NULL AUTO_INCREMENT COMMENT '主键id',
  `create_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '更新时间',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='表注释';

# 自动更新update_time的触发器(trigger_表名_字段名)
create trigger trigger_表名_update_time before update on 表名 for each row set NEW.update_time=CURRENT_TIMESTAMP;
```



## mysql设置
- 使用`-U` 参数, 当update delete时候 需要指定where条件

## 设计表
- 不能把表主键id 当成业务id, 需要单独创建一个字段 来保存业务id 比如user表 不能用id作为用户id需要创建一个user_id

## 与java区别
在java中`Long`最大值: 9223372036854775807, 选择mysql的`bigint`进行匹配

在java中`Integer`最大值: 2147483647, 选择mysql的`int`进行匹配

## 打印表结构
```sql
SELECT COLUMN_NAME              列名,
       COLUMN_COMMENT           名称,
       COLUMN_TYPE              数据类型,
       DATA_TYPE                字段类型,
       CHARACTER_MAXIMUM_LENGTH 长度,
       IS_NULLABLE              是否必填,
       COLUMN_DEFAULT           描述
FROM INFORMATION_SCHEMA.COLUMNS
where
    table_schema = '数据库名'
  AND
    table_name = '表名'
    
    
SELECT
    a.table_name 表名,
    a.table_comment 表说明,
    b.COLUMN_NAME 字段名,
    b.column_comment 字段说明,
    b.column_type 字段类型,
    b.column_key 约束
FROM
    information_schema.TABLES a
        LEFT JOIN information_schema. COLUMNS b ON a.table_name = b.TABLE_NAME
WHERE
        a.table_schema = 'co_monitor'
ORDER BY
    a.table_name ;
```

## 查看字符集排序规则和修改方法
```sql
show table status like 'hw_event_handle';
alter table hw_plan_station_status collate  utf8mb4_unicode_ci;
```