用以解决命名冲突



## std

标准命名空间



## 定义与使用

```c++
// 定义命名空间
namespace MonkeyCAM {
  
  void fun(){}
  
}
```



```c++
// 使用方法1
std::cout << "C++" << std::endl;
```



```c++
// 使用方法2 引入单个
using std::cout;
```



```c++
// 使用方法3
using namespace std;
```



## 匿名命名空间

编译器会自动生成一个唯一名称

```C++
namespace {
  
}
```

