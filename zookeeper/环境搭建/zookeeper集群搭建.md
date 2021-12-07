## 介绍
介绍如何搭建zookeeper集群搭建



## 1. 前置条件

- CentOS7系统
- JDK环境
- [zk安装包下载](https://mirrors.aliyun.com/apache/zookeeper/zookeeper-3.6.2/apache-zookeeper-3.6.2-bin.tar.gz)
- [zk可视化工具]()



## 2. 网络规划

编写`/etc/hosts`, 增加以下信息
```
192.168.153.128 node1
192.168.153.133 node2
192.168.153.134 node3
```



## 3. 修改配置文件

- 复制配置文件 `cp zoo_sample.cfg zoo.cfg`
- 在解压的zk目录下创建`data`目录
- 在`data`目录下 `touch myid` 输入节点的id (从0开始)
- 修改`zoo.cfg`文件的 `dataDir=/root/apache-zookeeper-3.6.2-bin/data`
- 在`zoo.cfg`文件的最后输入以下:
```
server.0=node1:2888:3888
server.1=node2:2888:3888
server.2=node3:2888:3888
```



## 4. 启动 & 检查

- 每个节点启动zk `bin/zkServer.sh start`
- 查看zk状态 `bin/zkServer.sh status`
- 使用jps命令查看是否有 `QuorumPeerMain` 进程



## 一键安装zk真集群

```bash
#! /bin/bash
# author Xiang Zheng
# 一键安装zk集群

# 前置条件
# ssh-copy-id -i .ssh/id_rsa.pub root@192.168.216.138

cluster=(192.168.216.136 192.168.216.137 192.168.216.138)

# 指定zk版本
version="3.6.2"
# 镜像地址(mirrors.cloud.tencent.com或mirrors.aliyun.com)
mirror=mirrors.aliyun.com
filename=apache-zookeeper-${version}-bin
tarball=${filename}.tar.gz


# 下载安装包
wget https://${mirror}/apache/zookeeper/zookeeper-${version}/${tarball}

# 解压
tar -zxvf ${tarball}

# 复制配置文件
cp ./${filename}/conf/zoo_sample.cfg ./${filename}/conf/zoo.cfg

for k in "${!cluster[@]}";
do
    echo "server.$k=node$k:2888:3888" >> ./${filename}/conf/zoo.cfg
done

mkdir -p ./${filename}/data
touch ./${filename}/data/myid
sed -i 's/\/tmp\/zookeeper/\/root\/zk\/data/g' ./${filename}/conf/zoo.cfg

# 修改hosts文件
for j in "${!cluster[@]}";
do
    echo "${cluster[$j]} node${j}" >> /etc/hosts
done


for i in "${!cluster[@]}";
do
    host=${cluster[$i]}
    scp -r ${filename} root@$host:/root/zk
    scp -r /etc/hosts root@$host:/etc/hosts
    ssh root@$host "
    echo $i >> ./zk/data/myid
    ./zk/bin/zkServer.sh start
    "
done

# 清理安装包
rm -rf ${filename}
rm -rf ${tarball}
```