

## 仓库单独设置用户名
```bash
git config --local user.name "Xiang Zheng"
git config --local user.email "zxyful@gmail.com"
```



## 删除敏感文件



## 删除大文件

- https://www.cnblogs.com/huipengly/p/8424096.html
- https://git-scm.com/docs/git-filter-branch



## git status 显示中文乱码

```bash
git config --global core.quotepath false
```



## 远程仓库管理

```bash
# 显示仓库信息
git remote -v

# 增加远程仓库（仓库名默认为origin）
git remote add 仓库名 git@gitlab.com:xxx/yyy.git

# 移除远程仓库
git remote remove 仓库名
```

