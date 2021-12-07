## 安装
```shell
# 安装mysql
brew install mysql

# 查看信息
brew info mysql

# 启动mysql
brew services start mysql 或 mysql.server start

# 关闭mysql
brew services stop mysql

# 重启mysql
brew services restart mysql

# 卸载mysql
brew uninstall mysql
```

> 初始密码呢？



## 外网访问配置

```
vim /usr/local/etc/my.cnf

# 修改bind-addres为
bind-address = 0.0.0.0

# 重启mysql
brew services restart mysql

# 修改root
update user set host = '%' where user = 'root';
```