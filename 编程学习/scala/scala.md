## 介绍
scale language

原理: scala -> 字节码 -> JVM

https://www.scala-lang.org/




## 环境搭建 & 基本使用
- mac `brew install scala`
- 下载[安装包](https://downloads.lightbend.com/scala/2.11.12/scala-2.11.12.msi)1
- 双击 下一步到底
- 使用命令检查 `scala -version`
- IDEA 安装scala插件
- 启动解释器, 命令行输入: `scala`
- `println("Hello, World")`
- 退出解释器 `:quit`


## 命令行初体验

```scala
scala> val a = 10
val a: Int = 10

scala> val b = 20
val b: Int = 20

scala> val c = a+b
val c: Int = 30

scala> c
val res0: Int = 30

scala>println("helloworld")

scala> :quit
```

## 文件形式
```scala
object HelloScala {
    def main(args: Array[String]): Unit = {
            println("Hello Scala")
    }
}
```

```shell
# 编译
scalac HelloScala.scala
# 执行
scala HelloScala
```


## IDEA配置
- 创建scala目录
- 项目设置源ROOT
- 右键项目添加添加框架支持 -> 选择scala
- 关联源码

```
https://github.com/scala/scala/archive/v2.13.5.tar.gz

tar -zxvf scala-2.13.5.tar.gz

Attach Source
```