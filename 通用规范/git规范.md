# git规范

## 仓库命名规范
- 禁止取名一些稀奇古怪的名字，不要创造英文单词 (bifrost、kraken、baldur)
- 设计以xxx-ui命名
- 后端服务以xxx-api命名
- 前端项目以xxx-web命名
- 苹果以xxx-ios命名
- 安卓以xxx-android命名
- 仓库必须写明用途
- 仓库禁止创建在个人名下

## 仓库初始化
- README.md .gitignore

## 分支规范
- 记得清理已经合并的分支
- 分支作用记录
- 前后端分支名称保持一致 dev prod release / 版本号
- git rebase git merge的使用

## 代码提交规范
- git提交信息配置
- 提交粒度以一个功能完成或功能修复为最小单位 `feat`, 禁止一次性提交大量代码
- 提交信息格式
- 修复bug格式为 `fix#TeamWork编号 内容` 举例 `fix#40593 修复XXX功能`
- https://blog.csdn.net/ligang2585116/article/details/80284819
- 提交前需要对代码格式化， 不必要的代码需要进行清理
- 原则上完成一个完整功能并自测无异常后，方可checkin代码，必须保证无编译报错
- 提交代码必须写注释，能够完整描述本次提交变更的内容

## 分支合并


## 小技巧
- 代码暂存
- 删除大文件