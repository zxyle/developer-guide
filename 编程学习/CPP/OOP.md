# 面向对象编程



## 类的定义与使用

```cpp
class Student {
public:
    string name;
    int age;

    void learning() {
        cout << name + "is learning.";
    }
};

// 实例化方法1
Student tony = {"Tony", 10};
tony.learning();

// 实例化方法2
Student tony;
tony.name = "Tony";
tony.age = 10;
```

**范围解析运算符** ::



## this

this->Volume()

## 指针

```
// 指针访问成员方法
ptrBox->Volume()
```

## 构造函数和析构函数

```cpp
类名();

~类名();
```



## 友元函数

```c++
class Box
{
   double width;
public:
   friend void printWidth( Box box );
   void setWidth( double wid );
};

// 请注意：printWidth() 不是任何类的成员函数
void printWidth( Box box )
{
   /* 因为 printWidth() 是 Box 的友元，它可以直接访问该类的任何成员 */
   cout << "Width of box : " << box.width <<endl;
}
```



## 内联函数

在编译时，编译器会把该函数的代码副本放置在每个调用该函数的地方。

```c++
inline int Max(int x, int y) {
   return (x > y)? x : y;
}
```



## 虚函数



## 静态成员

我们可以使用 **static** 关键字来把类成员定义为静态的。当我们声明类的成员为静态时，这意味着无论创建多少个类的对象，静态成员都只有一个副本。

静态成员函数即使在类对象不存在的情况下也能被调用，**静态函数**只要使用类名加范围解析运算符 **::** 就可以访问。

## 继承

```c++
class Animal {
    // eat() 函数
    // sleep() 函数
};


// 派生类
class Dog : public Animal {
    // bark() 函数
};


// 多继承
class Rectangle: public Shape, public PaintCost
{
   public:
      int getArea()
      { 
         return (width * height); 
      }
};
```





## 封装



## 多态

