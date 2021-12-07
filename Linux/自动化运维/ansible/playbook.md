## 介绍

playbook 是将一系列任务编排成一个文件，用于重复执行



playbook -> play -> task



## 命令

 命令格式: ansible-playbook install_jdk.yml

参数: 

| 参数         | 含义                     |
| ------------ | ------------------------ |
| -e           | 指定变量 -e iname="beth" |
| -i           | 指定主机清单             |
| --list-hosts | 查看所有主机             |
| -f           | 代表并发数               |



## 提示输入示例

```yaml
- hosts: test
  vars_prompt:
    - name: iname
      prompt: "请输入用户名"
      private: no
    - name: iname
      prompt: "请输入密码"
      private: yes
```



## 定义变量

```yaml
- hosts: hadoop
  vars:
    target: /opt/soft
    unzip_dir: hadoop-3.2.0
    tarball: hadoop-3.2.0.tar.gz
	
	tasks:
	 	- name: copy hadoop remote hosts
      copy: src=/root/{{ tarball }} dest={{ target }}
```





## 变量文件

```yaml
# variable.yml
---
iname: cloud
ipass: '123456'
```



使用:

```yaml
---
- hosts: test
  vars_files: variables.yml
  tasks:
    - name: create user.
      user:
        name: "{{ iname }}"
        password: "{{ ipass | password_hash('sha512') }}"
```

