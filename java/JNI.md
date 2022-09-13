# Java调用C++ 



## 1.  编写native方法

```java
public class Hello {

    public native void helloFromCPP();

}
```





## 2. 生成头文件

```bash
javac Hello.java -h .
```



## 3. 编写实现源文件

```c++
#include <jni.h>
#include <stdio.h>
#include "org_example_Hello.h"

JNIEXPORT void JNICALL Java_org_example_Hello_helloFromCPP
  (JNIEnv *, jobject){
    printf("Hello from C++\n");
  }

```



## 4. 编译生成动态链接库

```bash
gcc -I "/Users/xiangzheng/Library/Java/JavaVirtualMachines/azul-1.8.0_342/Contents/Home/include" -I "/Users/xiangzheng/Library/Java/JavaVirtualMachines/azul-1.8.0_342/Contents/Home/include/darwin" -shared -o libHello.dylib org_example_Hello.cpp
```



include 路径



## 5. 加载并使用

```java
public class Hello {

    public native void helloFromCPP();

    static {
        // 加载上一步生成的动态链接库
        System.load(System.getProperty("user.dir") + "/libHello.dylib");
    }

}
```



## 6. 调用

```java
public class Demo {
    public static void main(String[] args) {
        Hello hello = new Hello();
        hello.helloFromCPP();
    }
}
```

