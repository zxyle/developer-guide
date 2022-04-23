## 介绍

面向对象和泛型编程的支持

结构化编程 过程化编程
一种强调算法 一种强调数据

从低级组织（如类）到高级组织（如程序）的处理过程叫做自下向上的编程.

- 每条语句占一行
- 每个函数都有一个开始花括号和一个结束花括号，这两个花括号各占一行
- 函数中的语句都相对于花括号进行缩紧
- 与函数名称相关的圆括号周围没有空白
- 

原型只描述函数接口 函数头

char -> short -> int -> long -> long long

\#define INT_MAX 32767
全局搜索并替换 INT_MAX

3.1.8 3.1.9 还需要再看一遍

浮点数 float -> double -> long double





空语句“;”也是一条语句 

复合语句

规定else 与离他最近的尚未匹配的if匹配



## 入门Hello World
```c++
#include <iostream>

int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```


## 变量
```c++
int age = 18;
```


## 常量
```c++
#include <iostream>

using namespace std;

// 定义常量方式1
#define PI 3.14159265358


int main() {
    // 定义常量方式2
    cout << "PI = " << PI << endl;

    const int week = 7;
    cout << "一周有" << week << "天.\n";

    return 0;
}
```

## 整型

| 数据类型    | header 2    |
| ----------- | ----------- |
| row 1 col 1 | row 1 col 2 |
| row 2 col 1 | row 2 col 2 |


- short(短整型) 
- int(整型) 
- long(长整型)
- long long (长长整型)

```c++

```

## sizeof关键字
统计数据类型所占内存大小

## 浮点型
- float
- double

float型需要在末尾加上f

## 字符型
```c++
char ch = 'a';
```

查看字符对应的ASCII编码
`(int)ch`

## 转义字符

## 字符串类型
c风格字符串
```
char str[] = "hello";
string name = "郑翔";
```

## 布尔型
```
bool status = false;
```

## 枚举
```c++
enum color { red, green=5, blue };
cout << green << endl;
```


## 数据从控制台输入
```
#include <iostream>

using namespace std;

int main() {
    string name;
    cout << "input your name:";
    cin >> name;
    cout << "Your nams is " << name << endl;
    return 0;
}
```

## 算术运算符
前加加 后加加
```
```

## 赋值运算符
和python相同

## 比较运算符
和python相同

## 逻辑运算符
- 与: python and; cpp && 
- 或: python or; cpp ||
- 非: python not; cpp !
```
```

## 条件判断
条件有括号
```
if (条件)
    语句
}
```

## 循环

## 数组

## 函数 

## 指针
## 结构体

## 命名空间
namespace


## 关键字
```

```