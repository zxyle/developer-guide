## 介绍
Java软件项目管理及自动构建工具

- [Maven的使用](https://blog.csdn.net/hcmony/article/details/56013655)
- [Mac安装Maven](https://blog.csdn.net/u011886447/article/details/70200922)
- mac安装 `brew install maven`

## 下载及安装
- [官网下载](https://maven.apache.org/download.cgi)
- [阿里云镜像](https://mirrors.aliyun.com/apache/maven/binaries/)

## 配置环境变量
zshrc:
```
export M2_HOME=$HOME/apache-maven-3.6.3
export PATH=$PATH:$M2_HOME/bin
```

windows:
- `M2_HOME`   `D:\developer\software\apache-maven-3.6.3`
- `Path`      `%M2_HOME%\bin`


## 常用命令
- `mvn -v`      查看maven版本信息
- `mvn compile` 编译项目
- `mvn test`    测试
- `mvn package` 打包项目
- `mvn clean`   删除target目录
- `mvn install` 安装jar包到本地仓库中
- `mvn deploy`  部署

## 坐标
- `groupId`     表示项目所属组织信息, 通常是一个公司或者组织的名称 比如 `org.springframework`
- `artifactId`  项目唯一标识, 比如`spring-boot-starter-web`
- `version `    项目的版本
- `scope`

## 版本说明
- **主版本号**   架构变动或者不兼容实现
- **次版本号**   兼容性修改 功能郑钱
- **修订版本**号 bug修复

- **SNAPSHOT** 开发中的版本
- **RELEASE**  正式发布版(M1 M2指里程碑)
- **RC**       Release Candidate 发布候选
- **GA**       General availability 基本可用版

## POM文件说明
POM(project object model)

- modelVersion  pom文件Maven版本
- dependencies  声明依赖
- dependency    单个依赖



### scope

- compile  默认, 表示编译打包都需要此类库
- test   仅仅单元测试中需要
- provided 编译阶段需要此类库但打包不需要 运行时候需要
- build    
- runtime
- system
- import

## 仓库
本地仓库和远程仓库

- [全球中央仓库](http://search.maven.org)
- [Maven仓库](http://mvnrepository.com/)


## 修改镜像仓库

修改settings.xml
```xml
<settings>
    <mirrors>
        <mirror>
            <id>aliyunmaven</id>
            <mirrorOf>*</mirrorOf>
            <name>阿里云公共仓库</name>
            <url>https://maven.aliyun.com/repository/public</url>
        </mirror>
    </mirrors>
</settings>
```


## maven选项
- -P,--activate-profiles
- -D,--define <arg>  Define a system property
- -U, --update-snapshots 在远程仓管更新发布版本或快照版本时，强制更新。
- -T 线程数
- --settings, 指定settings文件


## IDEA 配置

## maven加快打包速度
```
mvn clean install -T 1C -Dmaven.test.skip=true -Dmaven.compile.fork=true
```

- `-T 1C` ：代表每个CPU核心跑一个工程。
- `-Dmaven.test.skip=true` ：代表跳过测试。
- `-Dmaven.compile.fork=true` ：使用多线程编译



## 安装本地jar包到本地仓库

```bash
mvn install:install-file -DgroupId=com.google.code -DartifactId=kaptcha -Dversion=2.3.2 -Dfile=kaptcha-2.3.2.jar -Dpackaging=jar -DgeneratePom=true
```

