## 介绍
是一个匿名函数(没有函数名的函数)

## 格式
```
(parameters) - > {
    statement;
}
```


## 应用场景

### 列表迭代
```
numbers.forEach(x -> System.out.println(x));
```

### Map 映射
```

```

### 代替 Runnable
```java
Thread t = new Thread(() -> {
    //to do something
});
t.start;
```