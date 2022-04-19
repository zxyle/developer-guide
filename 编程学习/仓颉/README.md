

## 环境搭建

```bash
apt-get install binutils libgcc-7-dev

ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6 /usr/lib/libstdc++.so

scp Cangjie_0.27.4-ubuntu_18.04-x86_64.tar.gz root@121.43.182.208:/root

tar -xvf Cangjie_0.27.4-ubuntu_18.04-x86_64.tar.gz
```



## docker环境使用

```bash
docker pull registry.cn-hangzhou.aliyuncs.com/zxyle/cangjie:0.27.4

docker tag registry.cn-hangzhou.aliyuncs.com/zxyle/cangjie:0.27.4 cangjie:0.27.4 

docker run -it --rm cangjie:0.27.4 /bin/bash
```

