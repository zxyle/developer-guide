

## git配置

```bash
# 仓库单独设置用户名和邮箱 --global 为设置全局
git config --local user.name "Xiang Zheng"
git config --local user.email "zxyful@gmail.com"

# git status 中文显示乱码
git config --global core.quotepath false
```



## 删除敏感文件



## 删除大文件

- https://www.cnblogs.com/huipengly/p/8424096.html
- https://git-scm.com/docs/git-filter-branch



## 远程仓库管理

```bash
# 显示仓库信息
git remote -v

# 增加远程仓库（仓库名默认为origin）
git remote add 仓库名 git@gitlab.com:username/repo.git

# 移除远程仓库
git remote remove 仓库名

# 修改仓库地址
git remote set-url origin git@gitlab.com:username/repo.git
```



## 完整克隆代码库(所有分支)

```bash
git clone xxx

git branch -r | grep -v '\->' | while read remote; do git branch --track "${remote#origin/}" "$remote"; done

git fetch --all

git pull --all
```



## stash操作

```bash
```





## 标签操作

```bash
# 查看所有标签
git tag

# 打标签
git tag v0.0.1

# 推送标签到仓库
git push origin v0.0.1

# 推送标签到远程仓库
git push origin --tags

# 删除标签
git tag -d v0.0.1

# 推送到仓库
git push origin :refs/tags/v0.0.1
```

