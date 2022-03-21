## yum安装
```
yum install python3
```



## apt安装

```
```



## Centos源码安装

### step1:  安装包下载
- [淘宝镜像下载](http://npm.taobao.org/mirrors/python/)
- [官网下载](https://www.python.org/downloads/)
- [官网历史版本](https://www.python.org/ftp/python/)

```
wget https://registry.npmmirror.com/-/binary/python/3.7.4/Python-3.7.4.tgz
```



### step2: 依赖库安装
```bash
yum install -y zlib zlib-devel bzip2-devel \
openssl-devel ncurses-devel sqlite-devel \
readline-devel tk-devel gcc libffi-devel
```

### step3: 解压
```
tar -zxvf Python-3.7.4.tgz
```

### step4: 配置
```bash
cd Python-3.7.4
./configure --prefix=/usr/local/python3
```

### step5: 编译及安装
```bash
make && make install
```

### step6: 安装pip
```bash
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
```

### step7: 建立软链接
```bash
ln -s /usr/local/python3/bin/python3 /usr/bin/python3
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
```


### step8: 检查
```bash
python3 -V
pip3 -V
```

### step9: 更换镜像源
放在home目录下的.pip目录内
windows使用pip.ini
Linux使用pip.conf

```ini
[global]
index-url = https://mirrors.aliyun.com/pypi/simple/

[install]
trusted-host=mirrors.aliyun.com
```