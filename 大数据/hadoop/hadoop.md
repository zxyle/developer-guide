## 介绍



## 组件

- Hadoop HDFS (分布式文件系统) 解决海量数据存储

- Hadoop MapReduce(分布式运算编程框架) 解决海量数据计算

- Hadoop yarn （作业调度和集群资源管理的框架） 解决集群资源任务调度



## 节点角色

- NameNode
- DataNode
- Secondary NameNode



## 物理位置

主要包含以下fsimage edits seed_txid VERSION

## NameNode

主节点，支持多个，整个文件系统的管理节点，主要维护着整个文件系统的文件目录树，文件、目录的信息

每个文件对应的数据块列表，并且还负责接收用户操作请求





## SecondaryNameNode

主要负责定期把edits文件内容合并到fsimage中，成为checkpoint, 在合并的时候会对edits中的内容进行转换，生成新的文件内容保存到fsimage文件中



## DataNode

从节点， 支持多个，提供真实文件数据的存储服务， HDFS会按照固定的大小，顺序对文件进行划分并编号，划分好每一个块称为一个block, HDFS默认Block大小是128M



## Replication

多副本机制，HDFS默认副本数量为3，通过dfs.replication属性控制



## 安全模式

刚启动时是安全模式，不能进行操作

- 查看安全模式： `hdfs dfsadmin -safemode get`
- 离开安全模式： `hdfs dfsadmin -safemode leave`
