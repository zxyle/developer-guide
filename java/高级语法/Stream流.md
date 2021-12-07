## 生成流

- `.stream()`



## 中间操作
- `.filter()` 返回true-留下， 返回false-过滤掉
- `.map()` 
- `.flatMap()`
- `.concat(stream1, stream2)` 合并两个流  
- `.distinct()` 将流中的元素去重之后输出
- `.sorted()` 将流中的元素按照自然排序方式进行排序
- `.peek()`
- `.limit()` 返回指定数量的元素的流
- `.skip()` 将前几个元素跳过（取出）再返回一个流



## 终结操作

- `.forEach()`
- `.forEachOrdered()`
- `.toArray()`
- `.reduce()`
- `.collect()`
- `.min()`
- `.max()`
- `.count()`
- `.anyMatch()`
- `.allMatch()`
- `.noneMatch()`
- `.findFirst()`
- `.findAny()`