## 简介
配置自动化运维工具，使用ssh协议, 不要安装agent



## 安装

```bash
# 安装 EPEL 仓库
yum install -y epel-release

# 安装 ansible
yum install -y ansible

# 或者使用pip安装
pip install ansible
```



## 编辑主机清单

vim /etc/ansible/hosts, 默认使用all代表所有主机

```
[servers] 
host1 ansible_ssh_host=127.0.0.1 
host2 ansible_ssh_host=127.0.0.1
```



## 配置免密

```bash
ssh-keygen -t rsa

ssh-copy-id 127.0.0.1
```



## 命令

命令格式: ansible  主机集合 -m 模块 -a "参数"

参数列表：

| 参数         | 说明                  |
| ------------ | --------------------- |
| -m           | 指定模块, 默认command |
| -i           | 指定主机清单文件      |
| -a           | 指定参数              |
| -u           | 指定用户名            |
| --list-hosts | 查看所有主机          |
| -k           | 使用密码远程          |



## 简单操作

```bash
# ping 所有主机
ansible all -m ping 

# ping test组下的主机
ansible test -m ping

# ping多个组
ansible node1,node2,node3 -m ping

ansible -i hosts all  -a "uptime" -u root

ansible -i hosts all -m ping -u root
```



## ansible-doc

```bash
# 查看模块帮助信息
ansible-doc 模块名称

# 列出所有模块
ansible-doc -l
```



## 错误处理

默认会停止接下来task

```yaml
ignore_errors: true
```



##  复用

