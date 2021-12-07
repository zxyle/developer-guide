## 前置准备

- Hadoop3.2.0集群
- Mysql 8.0.23
- [MySQL驱动](https://repo1.maven.org/maven2/mysql/mysql-connector-java/8.0.23/mysql-connector-java-8.0.23.jar)
- [hive3.1.2安装包](https://archive.apache.org/dist/hive/hive-3.1.2/apache-hive-3.1.2-bin.tar.gz)



## 解压

```bash
tar -zxvf apache-hive-3.1.2-bin.tar.gz -C /opt/soft
```



## 设置环境变量

```bash
# /etc/profile
# Hive Env
export HIVE_HOME=/opt/soft/apache-hive-3.1.2-bin
export PATH=$HIVE_HOME/bin:$PATH

source /etc/profile
```



## jar包调整

```bash
# 将mysql驱动复制到lib目录下载

# jar包改名，不然会日志冲突
mv log4j-slf4j-impl-2.10.0.jar log4j-slf4j-impl-2.10.0.jar.bak
```



## 在mysql中创建名为hive的数据库

> 编码为 latin1 latin1_general_ci



## 创建配置文件

```bash
cd /opt/soft/apache-hive-3.1.2-bin/conf/

mv hive-env.sh.template hive-env.sh
mv hive-default.xml.template hive-site.xml
```



## 修改hive-env.sh

```
# 文件末尾增加以下配置
export JAVA_HOME=/usr/local/java
export HIVE_HOME=/opt/soft/apache-hive-3.1.2-bin
export HADOOP_HOME=/opt/soft/hadoop-3.2.0
```



## 修改hive-site.xml

```bash
# 将javax.jdo.option.ConnectionURL的值改为
jdbc:mysql://mysqlIp:3306/hive?serverTimezone=Asia/Shanghai

# 将javax.jdo.option.ConnectionDriverName的值改为
com.mysql.cj.jdbc.Driver

# 将javax.jdo.option.ConnectionUserName的值改为
mysql用户名

# 将javax.jdo.option.ConnectionPassword的值改为
mysql的密码

# 将hive.querylog.location的值改为
/data/hive_repo/querylog

# 将hive.exec.local.scratchdir的值改为
/data/hive_repo/scratchdir

# 将hive.downloaded.resources.dir的值改为
/data/hive_repo/resources

# 删除3215行代码 (有一个奇怪字符串会导致启动报错)
```



## 修改hadoop core-site.xml

```xml
<property>
    <name>hadoop.proxyuser.root.hosts</name>
    <value>*</value>
</property>
<property>
    <name>hadoop.proxyuser.root.groups</name>
    <value>*</value>
</property>
```



## 初始化metastore

```bash
bin/schematool -dbType mysql -initSchema
```



## 	启动命令行窗口

```bash
./bin/hive
```



## 启动beeline

```bash
./bin/beeline -u jdbc:hive2://localhost:10000 -n root
```



## 远程服务启动

```bash
./bin/hiveserver2
```

