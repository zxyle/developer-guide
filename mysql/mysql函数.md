## 字符串
```sql
-- 字符串拼接
SELECT CONCAT('Hello','World');

-- 转大写
SELECT UCASE('hello');

-- 转小写
SELECT LCASE('HELLO');

-- 字符串长度
SELECT LENGTH('HELLO');

-- 字符串截取（从1开始）
SELECT SUBSTRING( 'helloworld', 2, 4 );  ello

--  去空格
SELECT TRIM(' hello ');
SELECT LTRIM(' hello ');
SELECT RTRIM(' hello ');
```



## 日期时间函数

- CURDATE() 获取当前日期
- SELECT STR_TO_DATE('01,5,2013','%d,%m,%Y');

- NOW()  显示yyyy-mm-dd HH:MM:SS 格式日期
- DATE_FORMAT(NOW(), '%Y-%m-%d %H:%i:%s')
- TIMESTAMPDIFF(SECOND, create_time, update_time)  时间差计算（本例为秒数）

```sql
SELECT YEAR('2022-12-31 11:33:44');
SELECT MONTH('2022-12-31 11:33:44');
SELECT DAY('2022-12-31 11:33:44');
SELECT HOUR('2022-12-31 11:33:44');
SELECT MINUTE('2022-12-31 11:33:44');
SELECT SECOND('2022-12-31 11:33:44');

-- 提取年月
SELECT EXTRACT(YEAR_MONTH FROM '2022-09-28 11:22:33') -- 202209
```



### 日期加减计算

```sql
SELECT DATE_SUB('2022-09-11', INTERVAL 5 DAY); -- 2022-09-06
SELECT DATE_ADD('2022-09-11', INTERVAL 5 DAY); -- 2022-09-16
```



## IP 地址转换

```sql
SELECT INET_ATON("114.114.114.114");

SELECT INET_NTOA(1920103026);
```



## 统计类

- AVG()
- COUNT()
- MAX()
- MIN()
- SUM()



## 保留小数

```sql
ROUND(3.14159, 4) -- 3.1416
CEIL()
FLOOR()
TRUNCATE()
```



## 数据类型转换

```sql
-- 转换成字符串
SELECT CAST( 11 AS CHAR );

-- 转换成数字
SELECT CAST('11' as SIGNED);
```



## 条件表达式

```sql
IF(condition, true, false)

CASE gender
    WHEN 0 THEN "女"
    WHEN 1 THEN "男"
END AS '性别'

-- 如果左边表达式为null，则使用右边表达式的值替换
IFNULL(null, 1);

```


## 窗口函数

| Name                                                         | Description                                                  |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [`CUME_DIST()`](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html#function_cume-dist) | Cumulative distribution value                                |
| [`DENSE_RANK()`](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html#function_dense-rank) | Rank of current row within its partition, without gaps       |
| [`FIRST_VALUE()`](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html#function_first-value) | Value of argument from first row of window frame             |
| [`LAG()`](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html#function_lag) | Value of argument from row lagging current row within partition |
| [`LAST_VALUE()`](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html#function_last-value) | Value of argument from last row of window frame              |
| [`LEAD()`](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html#function_lead) | Value of argument from row leading current row within partition |
| [`NTH_VALUE()`](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html#function_nth-value) | Value of argument from N-th row of window frame              |
| [`NTILE()`](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html#function_ntile) | Bucket number of current row within its partition.           |
| [`PERCENT_RANK()`](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html#function_percent-rank) | Percentage rank value                                        |
| [`RANK()`](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html#function_rank) | Rank of current row within its partition, with gaps          |
| [`ROW_NUMBER()`](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html#function_row-number) | Number of current row within its partition                   |

## 系统类

- VERSION()   查看mysql版本



