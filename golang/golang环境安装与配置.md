## windows
golang 1.14的windows版本 会自动设置GOPATH环境变量



## centos

- 下载:  https://golang.google.cn/dl/
-  解压: `tar -zxvf go1.15.6.linux-amd64.tar.gz -C /usr/local`
- 设置环境变量 `vim /etc/profile`

```
#golang env config
export GO111MODULE=on
export GOROOT=/usr/local/go 
export GOPATH=/home/gopath
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```
- `source /etc/profile`
- 查看版本 `go version`



## 配置镜像源

```bash
go env -w GOPROXY=https://goproxy.cn,direct
```