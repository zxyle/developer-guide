

## 安装

### macOS
[阿里云镜像站下载](http://mirrors.aliyun.com/docker-toolbox/mac/docker-for-mac/stable/)

### CentOS
[参考文章](https://developer.aliyun.com/mirror/docker-ce)

### Ubuntu
以ubuntu 18.04为例, [参考文章](https://developer.aliyun.com/mirror/docker-ce)

### Windows
[官网下载](https://www.docker.com/products/docker-desktop)

## 配置

### 配置用户
```
# 创建新用户 (在root账户下)
adduser username

# 将新用户添加到sudu组 (在root账户下)
adduser username sudo

# 将当前用户添加到docker组 (在新账户下)
sudo usermod -aG docker ${USER}

# 刷新docker用户组
newgrp docker
```

### 配置开机启动
```
sudo systemctl enable docker
```

### 配置阿里云镜像加速
```bash
sudo mkdir -p /etc/docker

sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://d1zfuwq5.mirror.aliyuncs.com"]
}
EOF

sudo systemctl daemon-reload
sudo systemctl restart docker
```

## 其他
### 安装docker-compose
```
apt install -y python3-pip
pip3 install docker-compose -i https://mirrors.aliyun.com/pypi/simple/
```