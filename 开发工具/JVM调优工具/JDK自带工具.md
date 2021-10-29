## jps - 查看进程

- **全称:** JVM Process Status Tool
- **作用:** 显示指定系统内所有的虚拟机进程



## jinfo - 

- **全称:** Configuration Info for Java
- **作用:** 显示虚拟机配置信息

```bash
# 查看jvm参数
jinfo -flags PID
```



## jstack

- **全称:** Stack Trace for Java
- **作用:** 显示虚拟机的线程快照



## jstat

- **全称:** JVM Statistics Monitoring Tool
- **作用:** 用于收集虚拟机各方面的运行数据



## jhat

- **全称:** JVM Heap Dump Browser
- **作用:** 用于分析heapdump文件



## jmap

- **全称:** Memory Map for Java
- **作用:** 生成虚拟机的内存转储快照(heapdump文件)



## javap - 反编译

```
javap <参数> <类>
```

参数
- -c  对代码进行反汇编
- -v  输出附加信息


## 普通的HelloWorld
```
Compiled from "HelloWorld.java"
public class HelloWorld {
  public HelloWorld();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: getstatic     #2                  // Field java/lang/System.out:Ljava/io/PrintStream;
       3: ldc           #3                  // String Hello World!
       5: invokevirtual #4                  // Method java/io/PrintStream.println:(Ljava/lang/String;)V
       8: return
}
```



## jconsole

可视化工具



## jvisualvm

可视化工具

安装Visual GC: 工具 -> 插件 -> Visual GC



```
captcity

- S0C    年轻代中第一个survivor（幸存区）的容量 (kb)
- S1C    年轻代中第二个survivor（幸存区）的容量 (kb)
- S0U    年轻代中第一个survivor（幸存区）目前已使用空间 (kb)
- S1U    年轻代中第二个survivor（幸存区）目前已使用空间 (kb)
- EC     年轻代中Eden（伊甸园）的容量 (kb)
- EU     年轻代中Eden（伊甸园）目前已使用空间 (kb)   
- OC     Old代的容量 (kb)   
- OU     Old代目前已使用空间 (kb)  
- MC     元空间
- MU     元空间
- CCSC   压缩类空间容量
- CCSU   压缩类空间使用状态
- YGC    young gc 次数
- YGCT     young gc 耗费时间
- FGC    full gc 次数
- FGCT   full gc 耗费时间
- GCT    从应用程序启动到采样时gc用的总时间(s)
```





