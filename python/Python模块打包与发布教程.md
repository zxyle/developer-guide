想要把自己开发的库分享给别人使用, 使用`pip install` 命令来安装 , 需要学习如何制作一个python 安装包

一、注册pypi账号
----------

https://pypi.org/account/register/



二、创建setup.py和pypirc文件
---------------------

### setup.py模板（该文件放在项目根目录下）
```python
from os.path import abspath, dirname, join

from setuptools import setup, find_packages

# 获取requirements.txt里的依赖信息  
install_reqs = [req.strip() for req in open(abspath(join(dirname(__file__), 'requirements.txt')))]

with open("README.md", 'r', encoding="utf-8") as f:
    long_description = f.read()

setup(
    name='模块名',
    version='0.0.1',
    packages=find_packages(),
    url='网址',
    license='协议',
    author='作者姓名',
    author_email='作者邮箱',
    description='描述信息',
    long_description=long_description,
    long_description_content_type="text/markdown",
    install_requires=install_reqs,
)

```
### pypirc模板 （该文件放在家目录内）

这个文件用来存储刚才注册pypi账号信息
```
[distutils]  
index-servers=pypi  
[pypi]  
repository = https://upload.pypi.org/legacy/  
username = 刚才注册的用户名  
password = 刚才注册的密码
```
三、安装依赖
------
```bash
pip install --upgrade pip twine wheel setuptools 
```

四、打包
----
```bash
python setup.py sdist bdist_wheel
```
打包之后 会在项目的dist目录内生成whl文件

五、将whl文件上传到pypi服务器
------------------
```bash
twine upload dist/*
```



## 常见问题

- 版本号不能是已存在的
