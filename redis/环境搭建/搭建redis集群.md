## 下载redis
```
wget http://download.redis.io/releases/redis-4.0.11.tar.gz
```

## 传输文件到目标服务器
```
scp redis-4.0.11.tar.gz get-pip.py root@10.50.103.103:/opt/soft
```

## 更换镜像源
```
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
mv /etc/yum.repos.d/CentOS-Base.repo.backup /etc/yum.repos.d/CentOS-Base.repo
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
```

## 更新软件
```
yum makecache
sudo yum -y install epel-release
yum -y update

yum -y install python2-pip vim gcc gcc-c++
```

## 修改pypi镜像源
```
vim ~/.pip/pip.conf
[global]
index-url = https://pypi.doubanio.com/simple/
trusted-host = pypi.doubanio.com
```

## 安装软件
```
pip install --upgrade pip
pip install supervisor==3.3.4
```

## supervisord设置
```
echo_supervisord_conf > /etc/supervisord.conf
mkdir -p /etc/supervisor/conf.d


vim /etc/supervisord.conf
[include]
files = /etc/supervisor/conf.d/*.conf

supervisord -c /etc/supervisord.conf
```

## 安装redis
```
tar xzf redis-4.0.11.tar.gz
cd redis-4.0.11

make MALLOC=libc
make hiredis jemalloc linenoise lua
```

## ruby设置
```
yum -y install ruby
查找默认源
gem sources
移除默认源
gem sources --remove https://rubygems.org/
添加新源
gem sources -a https://mirrors.aliyun.com/rubygems/
```

## 启动集群
```
./redis-trib.rb create --replicas 1 10.50.103.103:6379 10.50.103.104:6379 10.50.103.105:6379 10.50.103.106:6379 10.50.103.107:6379 10.50.103.108:6379
```