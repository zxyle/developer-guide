## 介绍
在某些情况下，需要搭建一个git仓库，通常的做法是使用gitlab进行搭建，但并不需要强大的功能，
其实只需要一个简单的git仓库就可以了



## 搭建

```bash
yum install git -y

mkdir repository && cd repository

# 创建项目(每个项目都需要创建)
mkdir hhy-scripts.git
git init --bare hhy-scripts.git/
```



## 拉取代码

```bash
git clone root@10.33.80.96:/root/repository/hhy-scripts.git
```



## 推送代码

```bash
git remote add hhy root@10.33.80.96:/root/repository/hhy-scripts.git
git push hhy
```



## 创建仓库脚本

create.sh
```shell
#!/bin/bash

echo -n "Enter repo name:"
read name

if [ ! -d ${name}.git ]
then
  mkdir ${name}.git
  git init --bare ${name}.git
  echo "Create ${name} success."
else
  echo "${name} existed."
fi
```