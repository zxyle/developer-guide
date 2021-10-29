
## apt工具使用
- 更新源: `apt-get update`
- 安装包: `apt-get install package -y`
- 卸载: 

## 更换阿里镜像源
### ubuntu
```
sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
sed -i s@/security.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
```

### debian
```
sed -i s@/deb.debian.org/@/mirrors.aliyun.com/@g /etc/apt/sources.list
sed -i s@/security.debian.org/@/mirrors.aliyun.com/@g /etc/apt/sources.list
```