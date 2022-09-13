

### limit 查询

```java
QueryWrapper<T> wrapper = new QueryWrapper<>();
// ...
wrapper.last("limit 1");
```



### 指定查询列

```java
QueryWrapper<T> wrapper = new QueryWrapper<>();

wrapper.select("HOUR(create_time), name, age");
```



### 排序

```java
wrapper.orderByAsc("create_time");
```

### 日期范围查询

```java
QueryWrapper<T> wrapper = new QueryWrapper<>();

wrapper.ge("create_time", "2023-01-01");
wrapper.ge("create_time", "2022-03-06 09:57:55");
wrapper.ge("create_time", LocalDate.parse("2022-09-01"));
wrapper.ge("create_time", LocalDateTime.parse("2022-01-06T08:35:46.695"));

// 使用between
wrapper.between("create_time", "2022-01-01 00:00:00", "2022-01-02 00:00:00");


// error 使用时间戳查询无效
```



### 分页查询

```java
QueryWrapper<T> wrapper = new QueryWrapper<>();
IPage<T> page = new Page<>(1, 10);
// 使用mapper查询
IPage<T> results = ipBlacklistMapper.selectPage(page, wrapper);

// 使用service查询
IPage<T> results2 = ipBlacklistService.page(page, wrapper);
```



### like查询

```java
QueryWrapper<T> wrapper = new QueryWrapper<>();
wrapper.like("name", "to");       // name LIKE '%to%'
wrapper.likeLeft("name", "to");   // name LIKE '%to'
wrapper.likeRight("name", "to");  // name LIKE 'to%'
```



### in 查询

```java
QueryWrapper<T> wrapper = new QueryWrapper<>();
// 方式1（List）：
wrapper.in("ip", Arrays.asList("a", "b", "c"));
// 方式2（vararg）：
wrapper.in("ip", "a", "b", "c");
// 方式3（数组）：
String[] ips = {"a", "b", "c"};
wrapper.in("ip", ips);
```



### 自定义分页

```java
IPage<T> iPage = PageRequestUtil.checkForMp(request);
IPage<T> list = breakerMapper.list(iPage, projectIds);

// IPage<T> list(IPage<T> page, List<Long> projects);
```



