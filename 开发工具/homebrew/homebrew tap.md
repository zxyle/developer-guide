

## 介绍
Formule安装脚本所在的仓库

[How-to-Create-and-Maintain-a-Tap](https://github.com/Homebrew/brew/blob/master/docs/How-to-Create-and-Maintain-a-Tap.md)

官方仓库地址: `/usr/local/Homebrew/Library/Taps/homebrew`


## 常用命令
- `brew tap`:  列出所有已安装tap
- `brew untap`: 移除tap仓库

## 创建Tap仓库(Github)
```
brew tap-new user/homebrew-repo
```

- user: github账号
- repo: tap名称

创建位置: `/usr/local/Homebrew/Library/Taps/zxyle`


## 创建基于gitee仓库
```
brew tap zxyle/brew https://gitee.com/zxyle/homebrew-brew.git
```