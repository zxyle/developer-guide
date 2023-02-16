## 介绍
2000年出现Ant, 2004年出现Maven, 2012年基于Ant和Maven产生Gradle弥补两者不足
它使用一种基于`Groovy`的特定领域语言(DSL)来声明项目设置, 抛弃了XML

## gradle的安装
[下载地址](https://gradle.org/releases/)

### windows安装
配置环境变量

- `GRADLE_HOME`       `D:\developer\software\gradle-6.5`
- `Path`              `%GRADLE_HOME%\bin`
- `GRADLE_USER_HOME`  `D:\developer\mavenrepo`

检查安装是否成功
```
gradle -v 
```

## 配置文件介绍
- `build.gradle`
- `settings.gradle`

## 配置代理
在`build.gradle`文件添加
```groovy
repositories {
    mavenLocal()
    maven { url 'https://maven.aliyun.com/repository/public/' }
    mavenCentral()
}
```

## IDEA 配置
![image](https://note.youdao.com/yws/res/14382/2E40960AE4F147DC89CB1FE448D39474)


## maven 转gradle项目
https://www.toutiao.com/i6899734937990611469/


## 常用代码
```groovy
repositories {
    mavenLocal()
    maven { url 'https://maven.aliyun.com/repository/public/' }
    mavenCentral()
}
```



```
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
//    implementation 'cn.hutool:hutool-all:5.8.10'
    implementation files("/Users/xiangzheng/.m2/repository/cn/hutool/hutool-all/5.8.4/hutool-all-5.8.4.jar")
}
```

### 常用命令

- gradle clean 清空build目录
- gralde classes 编译业务代码和配置文件
- gradle test  编译测试代码，生成测试报告
- gradle build 构建项目
- gradle build -x test 跳过测试构建