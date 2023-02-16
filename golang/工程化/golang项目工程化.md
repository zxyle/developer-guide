## 初始化go module项目
```
go mod init [module name 可选]
```



## 设置环境变量

```
go env -w GO111MODULE=on
```

## 使用Goland创建项目
New Project -> Go Modules(vgo) -> Proxy
需要填写 (使用逗号隔开)
- https://goproxy.io
- https://goproxy.cn
- https://goproxy.baidu.com
- https://mirrors.aliyun.com/goproxy/
- https://mirrors.cloud.tencent.com/go/
- direct


## 国内版本校验(不懂用法以及原理)
```
go env -w GOSUMDB="sum.golang.google.cn"
```

## go mod命令
- download    将模块下载到本地缓存
- edit        通过工具或脚本编辑go.mod
- graph       打印模块需求图
- init        在当前目录中初始化新模块
- tidy        添加缺少的内容并删除未使用的模块
- vendor      制作供应商的依赖副本
- verify      验证依赖项具有预期的内容
- why         解释为什么需要软件包或模块



## Goland关闭创建项目的教程
取消 Settings -> Plugins -> IDE Features Trainer
