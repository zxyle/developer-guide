## 介绍

Hadoop分布式文件系统（Hadoop Distributed File System ）



## 特点

- 不适合小文件存储 （每个文件128M）



## 操作

命令格式: `hdfs dfs -命令 scheme://authority/path`

### -ls 查询指定路径信息

```bash
# 查看根目录内容
hdfs dfs -ls hdfs://hadoop01:9000/

# 也可以简写为
hdfs dfs -ls /

# 递归列出所有
hdfs dfs -ls -R /

# 查看文件数量
hdfs dfs -ls / | grep / | wc -l

# 查看文件大小
hdfs dfs -ls / | grep / | awk '{print $8,$5}'
```



### -put 从本地上传文件

```bash
hdfs dfs -put README.txt /
```



### -cat 查看HDFS文件内容

```bash
hdfs dfs -cat /README.txt 
```



### -get 下载文件到本地

```bash
hdfs dfs -get /README.txt README.txt.bak
```



###  -mkdir[-p] 创建文件夹

```bash
# 创建一级目录
hdfs dfs -mkdir /test

# 递归创建
hdfs dfs -mkdir -p /abc/xyz
```



### -rm [-r] 删除文件、文件夹 

```bash
hdfs dfs -rm /README.txt

# 忽略回收站，永久删除 
-skipTrash
```