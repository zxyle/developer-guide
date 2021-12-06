## 介绍
交叉编译就是编译生成不同平台的可执行文件.



## 环境变量设置

* GOOS：目标操作系统
* GOARCH：目标操作系统的架构



## GOOS可选参数

* linux  编译生成Linux下可执行文件
* windows 编译生成Windows下可执行文件
* darwin 编译生成MacOS下可执行文件



## GOARCH可选参数

* 386 
* amd64 
* arm



## 设置环境变量

Windows环境
```
set GOOS=windows
```

MacOS/Linux
```
export GOOS=linux
```



## linux

```shell
#!/usr/bin/env bash
# build-for-linux.sh

export CGO_ENABLED=0
# darwin linux windows
export GOOS=linux
export GOARCH=amd64

go build
```

