## 介绍

Hadoop Distributed File System 



## 特点

- 不适合小文件存储 



## 操作

命令格式: `bin/hdfs dfs -xxx scheme://authority/path`

### -ls 查询指定路径信息

```bash
# 查看根目录内容
bin/hdfs dfs -ls hdfs://hadoop01:9000/

# 也可以简写为
bin/hdfs dfs -ls /

# 递归列出所有
bin/hdfs dfs -ls -R /

# 查看文件数量
bin/hdfs dfs -ls / | grep / | wc -l

# 查看文件大小
bin/hdfs dfs -ls / | grep / | awk '{print $8,$5}'
```



### -put 从本地上传文件

```bash
bin/hdfs dfs -put README.txt /
```



### -cat 查看HDFS文件内容

```bash
 bin/hdfs dfs -cat /README.txt 
```



### -get 下载文件到本地

```bash
bin/hdfs dfs -get /README.txt README.txt.bak
```



###  -mkdir[-p] 创建文件夹

```bash
bin/hdfs dfs -mkdir /test

# 递归创建
bin/hdfs dfs -mkdir -p /abc/xyz
```



### -rm [-r] 删除文件、文件夹 

```bash
bin/hdfs dfs -rm /README.txt

# 忽略回收站，永久删除 
-skipTrash
```