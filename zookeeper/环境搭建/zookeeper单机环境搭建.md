## 介绍
分为两种方式
- 使用docker compose
- 搭建伪集群


## 1. docker compose
```yaml
zookeeper:
    image: zookeeper:3.4.11
    restart: always
    ports:
      - 2181:2181
      - 2888:2888
      - 3888:3888
```

## 2. 搭建伪分布式集群

```bash
#! /bin/bash
# author Xiang Zheng
# 一键安装zk集群
# TODO: 1. 新增target指定安装路径

# 指定zk版本
version="3.6.2"
# 指定当前主机的ip地址
ip="192.168.216.128"
# zk节点数量
node=5
# 镜像地址(mirrors.cloud.tencent.com或mirrors.aliyun.com)
mirror=mirrors.aliyun.com

# 创建目录
mkdir cluster
for k in `seq 1 $node`
do
    mkdir cluster/zk$k
    mkdir cluster/zk$k/data
done


# 下载安装包
wget https://${mirror}/apache/zookeeper/zookeeper-${version}/apache-zookeeper-${version}-bin.tar.gz

# 剪切
mv apache-zookeeper-${version}-bin.tar.gz ./cluster/

# 解压
tar -zxvf ./cluster/apache-zookeeper-${version}-bin.tar.gz -C ./cluster/

# 复制配置文件
cp ./cluster/apache-zookeeper-${version}-bin/conf/zoo_sample.cfg ./cluster/apache-zookeeper-${version}-bin/conf/zoo.cfg

# 修改配置文件
for i in `seq 1 $node`
do
    echo "$i" >> ./cluster/zk$i/data/myid
    cp -r ./cluster/apache-zookeeper-${version}-bin/ ./cluster/zk$i/
    sed -i "s/\/tmp\/zookeeper/\/root\/cluster\/zk$i\/data/g" ./cluster/zk$i/apache-zookeeper-${version}-bin/conf/zoo.cfg
    sed -i "s/2181/218$i/g" ./cluster/zk$i/apache-zookeeper-${version}-bin/conf/zoo.cfg
    for j in `seq 1 $node`
    do
        echo "server.$j=${ip}:2881:388$j" >> ./cluster/zk$i/apache-zookeeper-${version}-bin/conf/zoo.cfg
    done

done

# 启动节点
for i in `seq 1 $node`
do
    ./cluster/zk$i/apache-zookeeper-${version}-bin/bin/zkServer.sh start
done

```

批量查看状态/关闭
```bash
#! /bin/bash
for i in {1..3}
do
    ./cluster/zk$i/apache-zookeeper-3.6.2-bin/bin/zkServer.sh status
done
```