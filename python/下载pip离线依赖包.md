## 介绍
在某些环境下 不能使用pip进行在线安装, 需要将依赖包全部离线下载到本地， 再进行安装

参考文档: https://pip.pypa.io/en/stable/cli/pip_download/



## 新方法

将依赖信息写入requirements.txt


```
python -m pip download \
   --only-binary=:all: \
   --platform linux_x86_64 \
   --python-version 39 \
   --implementation cp \
   -i https://mirrors.aliyun.com/pypi/simple \
   -r requirements.txt -d package
```



## 1. 进入对应python版本的docker里

```bash
docker run -it --rm python:3.9.1 /bin/bash
```

## 2. 下载依赖
```
# 先升级pip
pip install --upgrade -i https://mirrors.aliyun.com/pypi/simple/ pip

# 下载依赖
pip download -d package <依赖> -i https://mirrors.aliyun.com/pypi/simple/
```

## 3. 从容器中复制出依赖
打开另外一个窗口:
```
docker cp <容器id>:/package ./package
```

## 4. 编写requirements.txt
```
paramiko-2.7.2-py2.py3-none-any.whl
bcrypt-3.2.0-cp36-abi3-manylinux2010_x86_64.whl
cffi-1.14.4-cp39-cp39-manylinux1_x86_64.whl
cryptography-3.3.1-cp36-abi3-manylinux2010_x86_64.whl
PyNaCl-1.4.0-cp35-abi3-manylinux1_x86_64.whl
six-1.15.0-py2.py3-none-any.whl
pycparser-2.20-py2.py3-none-any.whl
```

## 5. 目标机器安装
```
pip install -r requirements.txt
```
