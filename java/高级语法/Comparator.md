## Comparator.comparingInt

类型转换之后进行排序

```java
Comparator.comparingInt(new ToIntFunction<CompanyLabel>() {
                                @Override
                                public int applyAsInt(CompanyLabel value) {
                                    return Integer.parseInt(value.getSpare2());
                                }
                            })
```

