## 1. 先决条件

- 本文以安装kafka 2.7.0为例

- CentOS系统
- JDK8环境
- zookeeper集群(参考其他文档)
- [kafka安装包下载](https://mirrors.cloud.tencent.com/apache/kafka/)
- [kafka可视化工具下载](https://www.kafkatool.com/download.html)



## 2. 修改`config/server.properties`

- 修改 `log.dirs=/root/kafka_2.13-2.7.0/data`
- 修改 `broker.id` (从0开始)
- 修改 `zookeeper.connect=node1:2181,node2:2181,node3:2181`
- 修改 `listeners=PLAINTEXT://192.168.153.133:9092` (每个节点填写各自的ip)


## 3. 启动并检查
- 启动kafka `nohup bin/kafka-server-start.sh config/server.properties &`
- 使用jps查看进程 是否有``

## 目录介绍
- bin
- config
- libs
- logs
- site-docs


## 一键创建集群
> 先要运行一键创建zk集群
```shell
#! /bin/bash
# author zheng
# 一键搭建kafka集群

mirror=mirrors.aliyun.com
cluster=(192.168.216.136 192.168.216.137 192.168.216.138)
scala_version=2.13
kafka_version=2.7.0
filename=kafka_${scala_version}-${kafka_version}
tarball=${filename}.tgz

# 下载安装包
wget https://${mirror}/apache/kafka/${kafka_version}/${tarball}

# 解压安装包
if [[ -a $tarball ]]; then
	echo "文件存在"
	tar -zxvf ${tarball}
fi

# 创建数据目录
mkdir ${filename}/data

# 修改配置文件
sed -i 's/localhost:2181/node0:2181,node1:2181,node2:2181/g' ./${filename}/config/server.properties
sed -i 's/\/tmp\/kafka-logs/\/root\/kafka\/data/g' ./${filename}/config/server.properties

# 复制安装包并启动节点
for i in "${!cluster[@]}";
do
    host=${cluster[$i]}
    scp -r ${filename} root@$host:/root/kafka
    ssh root@$host "
    source /etc/profile
    sed -i "s/broker.id=0/broker.id=$i/g" ./kafka/config/server.properties
    echo listeners=PLAINTEXT://$host:9092 >> ./kafka/config/server.properties
    nohup ./kafka/bin/kafka-server-start.sh ./kafka/config/server.properties > /dev/null &
    "
done

# 清理安装包
rm -rf ${filename}
rm -rf ${tarball}
```