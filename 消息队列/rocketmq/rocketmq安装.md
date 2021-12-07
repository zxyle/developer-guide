### 下载
https://mirrors.aliyun.com/apache/rocketmq/

### 启动
- `nohup sh bin/mqnamesrv &`
- 查看日志`tail -f ~/logs/rocketmqlogs/namesrv.log`
- 编辑`runbroker.sh` 和 `runserver.sh -Xms256m -Xmx256m -Xmn128m`
- `nohup sh bin/mqbroker -n localhost:9876 autoCreateTopicEnable=true &`
- 使用`jps`命令

### 小测试
- `export NAMESRV_ADDR=localhost:9876`
- `sh tools.sh org.apache.rocketmq.example.quickstart.Producer`
- `export NAMESRV_ADDR=localhost:9876`
- `sh tools.sh org.apache.rocketmq.example.quickstart.Consumer`

### 关闭RocketMQ
- `sh mqshutdown namesrv`
- `sh mqshutdown broker`

## 概念
- `Producer` 消息发送者
- `Consumer` 消息接收者
- `Broker`  暂存和传输消息
- `Name Server`  管理Broker
- `Topic` 区分消息的种类
- `Message Queue` 
- `Producer -> Name Server -> Broker`
- `Consumer -> Name Server -> Broker`