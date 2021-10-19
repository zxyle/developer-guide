

## 介绍
HomeBrew是MacOS下的软件包管理工具

- [官网](https://brew.sh/index_zh-cn)

## 配置镜像源
https://developer.aliyun.com/mirror/homebrew

```
# 替换brew.git:
cd "$(brew --repo)"
git remote set-url origin https://mirrors.aliyun.com/homebrew/brew.git

# 替换homebrew-core.git:
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://mirrors.aliyun.com/homebrew/homebrew-core.git

# 替换homebrew-cask.git:
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-cask"
git remote set-url origin https://mirrors.aliyun.com/homebrew/homebrew-cask.git

# 替换homebrew-bottles:
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.aliyun.com/homebrew/homebrew-bottles' >> ~/.zshrc
source ~/.zshrc

# 应用生效
brew update
```

## 基本操作
- 安装: `brew install package`
- 更新: `brew upgrade package`
- 列出: `brew list`
- 重装: `brew reinstall package`
- 更新: `brew update`
- 卸载: `brew uninstall package`