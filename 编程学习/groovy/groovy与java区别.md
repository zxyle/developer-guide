## 版本说明
```shell
groovy -version

Groovy Version: 3.0.8 JVM: 1.8.0_202 Vendor: Oracle Corporation OS: Mac OS X
```

## 默认导入
不必显式导入它们, 默认是导入的
- `java.io.*`
- `java.lang.*`
- `java.math.BigDecimal`
- `java.math.BigInteger`
- `java.net.*`
- `java.util.*`
- `groovy.lang.*`
- `groovy.util.*`

## 多方法
## 数组初始化器
```groovy
int[] array = [1, 2, 3]
```

## 包范围可见性



- 如果没有歧义，可以省略调用函数的括号 如: `println "Hello world!"`
- 定义变量，使用def，可以不声明变量类型，如: `def name = "John"`

- 类的使用

  ```groovy
  class Person {
      def name = "John"
      def age = 30
      def address = "123 Main St."
      def city = "New York"
      def state = "NY"
      def zip = "10001"
      def country = "USA"
      def phone = "123-456-7890"
  }
  
  def person = new Person(age: 11)
  person["name"] = "Zhengxiang"
  person.address = "西湖区"
  println person.age
  println person.getAddress()
  ```

  