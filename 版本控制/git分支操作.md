```bash
# 创建新分支
git branch 分支名

# 切换分支
git checkout 分支名

# 创建新分支并切换新分支
git checkout -b 分支名

# 切换到上一个分支
git checkout -

# 删除分支
git branch -d 分支名

```



## 查看操作

```bash
# 查看本地所有分支
git branch

# 查看本地和远程所有分支
git branch -a

# 查看远程分支
git branch -r


```



## 切换操作





## 合并操作

```bash
git merge --no-ff branch-name
```







## 切换远程分支

```bash
git checkout -b 本地分支名 origin/远程分支名
```



## 删除远程仓库分支

```bash
git tag -d v0.0.1
git push origin :refs/tags/v0.0.1
```



## 分支

- `git fetch` 将本地分支与远程保持同步
- `git fetch --all` 将本地所有分支与远程保持同步
- `git pull --all` 拉取所有分支代码