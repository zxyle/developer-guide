## 介绍

在windows或mac系统中，执行python文件需要安装对应的编程环境。但是有了pyinstaller，就可以将python源代码转换成可执行文件。



## 安装

```bash
pip3 install -i https://pypi.doubanio.com/simple pyinstaller
```



## 示例

命令格式： pyinstaller 参数 python文件

```bash
pyinstaller -F -i xxx.ico hello.py
```



## 参数

| 参数 | 作用               | 示例           |
| ---- | ------------------ | -------------- |
| -F   | 只生成一个文件     |                |
| -i   | 设置可执行文件图标 | -i favicon.ico |

