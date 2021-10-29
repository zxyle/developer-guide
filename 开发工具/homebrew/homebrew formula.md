
## 介绍
配方 也就是安装脚本

- [Python-for-Formula-Authors](https://docs.brew.sh/Python-for-Formula-Authors)
- [Node-for-Formula-Authors](https://github.com/Homebrew/brew/blob/master/docs/Node-for-Formula-Authors.md)
- [Formula-Cookbook](https://docs.brew.sh/Formula-Cookbook)

## 创建Formula
```
brew create --python https://zxyle-homebrew.oss-cn-hangzhou.aliyuncs.com/tarballs/builder-0.0.1.tar.gz
```
> 以上使用了python模板, 还可以使用go node rust ruby等模板


## 编写rb文件
参考 https://github.com/zxyle/homebrew-taps/tree/main/Formula


## 安装Formula
```
brew install name
```

## 从在线地址安装Formula
```
brew install --build-from-source  http://example.org/name.rb
```

