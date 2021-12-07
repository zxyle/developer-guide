## 前置条件
```
yum install wget gcc -y
```



## 下载

```
wget https://download.redis.io/releases/redis-6.2.2.tar.gz

wget https://mirrors.huaweicloud.com/redis/redis-6.2.2.tar.gz
```



## 解压 & 编译

```
tar -zxvf redis-6.2.2.tar.gz

cd redis-6.2.2

make

make install

cp redis.conf /etc/redis.conf
```



## 修改配置文件

```
vim /etc/redis.conf
```
- 修改bind: `bind 0.0.0.0` 或者 `bind * -::*`
- 修改daemonize 为yes
- 去掉注释 requirepass foobared
- appendonly 改为yes

## 运行起来
```
redis-server /etc/redis.conf
```

## 测试
```
redis-cli -a foobared
127.0.0.1:6379> ping
PONG
```

## 清理环境
```
rm -rf redis-6.2.2*
```


## 程序目录
- `redis-benchmark`: 性能测试工具
- `redis-check-aof`: 修复有问题的AOF文件
- `redis-check-dump`: 修复有问题的dump.rdb文件
- `redis-sentinel`: redis集群使用
- `redis-server`: redis服务器启动命令