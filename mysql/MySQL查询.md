## select

```sql
select * from table_name;
```



## where

```sql
WHERE
```



## 分组查询 group by

```sql
SELECT 
    address, 
    AVG(age) AS "平均年龄", 
    COUNT(*) as "人数" 
FROM students 
GROUP BY students.address;
```

## having

过滤分组信息

```sql
HAVING
```

## 排序 order by

```sql
order by field asc/desc;
```

## left join

左外连接

```sql
SELECT 
    * 
FROM t1
LEFT JOIN t2
ON t1.f1 = t2.f2
```



## right join

右外连接

```sql
```



## join

```sql
```



## limit

```sql
LIMIT 10
```



## IN / NOT IN

```sql
IN ('', '', '')
```



## BETWEEN AND

```sql
create_time BETWEEN '2022-09-01 00:00:00' AND '2022-09-01 23:59:59'
```



## LIKE

```sql
name LIKE '张%'
```





## 窗口函数

```sql
```

