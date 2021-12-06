## 集群概念



## 搭建集群

config/elasticsearch.yml

```
cluster.name: my-es     # 集群名称
node.name: node-1       # 节点名称
node.master: true       # 当前节点是否可以被选举为master节点，是：true、否：false ---
network.host: 0.0.0.0   # 
http.port: 9200         # 端口号
transport.port: 9300    # ---
# 初始化一个新的集群时需要此配置来选举master
cluster.initial_master_nodes: ["node-1","node-2","node-3"]
#写入候选主节点的设备地址 ---
discovery.seed_hosts: ["127.0.0.1:9300", "127.0.0.1:9301","127.0.0.1:9302"]
http.cors.enabled: true      # 跨域设置
http.cors.allow-origin: "*"  # 跨域设置
```

