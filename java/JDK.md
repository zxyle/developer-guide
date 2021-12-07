## JDK 下载
- [Oracle JDK官网](https://www.oracle.com/hk/java/technologies/oracle-java-archive-downloads.html)
- [OpenJDK](https://developers.redhat.com/products/openjdk/download?sc_cid=701f2000000RWTnAAO)
- [AdoptOpenJDK](https://adoptopenjdk.net/)
- [华为JDK镜像](https://repo.huaweicloud.com/java/jdk/)
- [清华大学JDK镜像](https://mirrors.tuna.tsinghua.edu.cn/AdoptOpenJDK/)



## windows 安装jdk

- 一路点击下一步
- 新建环境变量名: `JAVA_HOME` 变量值: `C:\Program Files\Java\jdk1.8.0_131`
- `Path`添加 `%JAVA_HOME%\bin` 和 `%JAVA_HOME%\jre\bin`
- 新建环境变量名: `CLASSPATH` 变量值: `.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar`



## linux 安装jdk

### step1: 解压到指定目录
```shell
[root@localhost ~]# tar -zxvf jdk-8u202-linux-x64.tar.gz -C /opt
```

### step2: 创建软连接
```shell
[root@localhost ~]# ln -snf /opt/jdk1.8.0_202 /opt/jdk
```

### step3: 配置环境变量
```shell
局部环境变量：~/.bashrc
全局环境变量：/etc/profile

# Java 环境变量
export JAVA_HOME=/opt/jdk
export JRE_HOME=$JAVA_HOME/jre
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:.
export PATH=$PATH:$JAVA_HOME/bin

# 激活
source 相关文件（更新配置文件）
```

### step4: 验证
```shell
[root@localhost ~]# java
用法: java [-options] class [args...]
           (执行类)
   或  java [-options] -jar jarfile [args...]
           (执行 jar 文件)
                  
[root@localhost ~]# javac -version
javac 1.8.0_191

[root@localhost ~]# java -version
java version "1.8.0_202"
Java(TM) SE Runtime Environment (build 1.8.0_202-b12)
Java HotSpot(TM) 64-Bit Server VM (build 25.191-b12, mixed mode)
```



## rpm安装

```shell
rpm -ivh jdk-8u202-linux-x64.rpm
```



设置环境变量

```shell
export JAVA_HOME=$(dirname $(dirname $(readlink $(readlink $(which javac)))))
```

