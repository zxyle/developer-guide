## ping模块

作用: 测试主机联通性



## command模块

作用:  不开启shell解释器，直接通过ssh执行命令，不支持bash的一些特性，如重定向等
默认调用command模块



常用命令: 

```bash
ansible test -m command -a "uptime"
ansible test -m command -a "uname -r"
ansible test -m command -a "ip a s ens33"
ansible test -a "ip a s ens33"
ansible all -a "date"
```



## shell模块

作用: 执行shell命令

模块参数:

- chdir: 切换目录
- creates: 文件存在，不执行shell命令
- removes: 文件不存在，不执行shell命令



常用命令: 

```bash
ansible test -m shell -a "ps aux| wc -l"
ansible test -m shell -a "who"
ansible test -m shell -a "touch /tmp/txt.txt"
ansible test -m shell -a "chdir=/tmp touch hello.txt"

ansible test -m shell -a "ssh-keygen -f ~/.ssh/id_rsa -N '' creates=~/.ssh/id_rsa"
ansible test -m shell -a "unzip xx.zip removes=/bin/unzip"
```



## raw模块



## script模块

作用: 执行脚本

创建test.sh

```bash
#!/bin/bash
yum -y install httpd
systemctl start httpd
```



```
ansible test -m script -a "./test.sh"
```



## file模块

作用: 可以创建文件、目录、链接；修改权限与属性等，是幂等性

模块参数:

- path: 创建文件位置
- state: link-创建软链接、absent-删除文件、touch-创建空文件、directory-创建目录、hard-创建硬链接
- src： 创建软链接会使用
- dest： 创建软链接会使用
- owner: 所属用户
- group: 用户组
- mode: 权限
- force: 



常用命令: 

```bash
# 新建文件
ansible test -m file -a "path=/tmp/file.txt state=touch"

# 创建目录
ansible test -m file -a "path=/tmp/mydir state=directory"

# 修改文件和目录权限
ansible test -m file -a "path=/tmp/file.txt owner=sshd group=adm mode=0777"

# 删除文件
ansible test -m file -a "path=/tmp/file.txt state=absent"

# 创建快捷方式
ansible test -m file -a "src=/etc/hosts path=/tmp/host.txt state=link"
```



playbook task 示例:

```yaml
# 创建软链接示例
- name: create links
    file: src=/opt/soft/jdk1.8.0_202 dest=/usr/local/java state=link
```



## copy模块

作用: 将文件拷贝到远程主机

模块参数:

- src: 待上传文件的绝对地址
- dest: 目标文件绝对地址

- backup=yes 如果目标主机有同名文件，则先备份
- content：取代src=，标识直接用此处的信息生成文件内容



常用示例:

```bash
ansible test -m copy -a "src=~/a3.txt dest=/root/"
ansible test -m copy -a "src=~/a3.txt dest=/root/ backup=yes"

# 指定文件名拷贝
ansible test -m copy -a "src=~/a3.txt dest=/root/3a.txt"

# 指定内容
ansible test -m copy -a "content='hello the world\n' dest=/root/new.txt"
```



playbook task示例: 

```yaml
- name: copy jdk remote hosts
  copy: src=~/developer/software/jdk/jdk-8u202-linux-x64.tar.gz dest=/opt/soft
```





## fetch模块

作用: 下载远程主机文件

模块参数:

- src：远程主机文件目录
- dest： 本地主机目录

```bash
ansible test -m fetch -a "src=/etc/hostname dest=~/"
```



## lineinfile模块

作用: 修改文件

模块参数:

- path： 文件位置
- regexp： 
- line： 



## replace模块

作用: 修改文件

模块参数：

- path： 文件路径
- regexp： 被替换的文本
- replace： 替换的文本



## user模块

作用: 创建用户、设置密码

模块参数：

- name： 用户名
- uid： 指定uid
- group： 指定组名
- groups： 指定附加组 root,daemon
- home： 指定家目录 /home/user2
- createhome： 是否创建家目录yes or no
- password： 密码（需要加密） {{'abc' | password_hash('sha512')}}
- system： 是否是系统用户yes or no
- shell
- state： 指定状态 absent-删除用户
- comment： 注释信息
- remove: 连带删除家目录、邮箱



常用命令：

```bash
ansible test -m user -a 'name="user1"'
```



playbook task 示例

```yaml
- name: Add the user James
  user:
    name: james
    uid: 1040
    group: daemon
    password: "{{ '123' | password_hash('sha512') }}"
```



## group模块

作用: 组管理

模块参数：

- gid：gid
- name：组名
- state：状态
- system：是都是系统组yes or no



常用命令：

```bash
ansible test -m group -a 'name=mysql gid=306 system=yes'
```



## yum_repository模块

作用: yum源管理

模块参数：

- name
- description
- baseurl
- gpgcheck



命令示例:

```bash
# 新建yum源配置文件
ansible test -m yum_repository -a "name=myyum description=hello baseurl=ftp://192.168.4.254/centos gpgcheck=no"

# 查看
[root@localhost soft]# cat /etc/yum.repos.d/myyum.repo
[myyum]
async = 1
baseurl = ftp://192.168.4.254/centos
gpgcheck = 0
name = hello
```





## yum模块

作用: yum安装、卸载、升级软件包

模块参数：

- name： 一个数组或一个字符串，代表软件包名称
- state: 状态 present-安装， latest-升级，absent-卸载



playbook task示例: 

```yaml
- name: Install a list of packages
  yum:
    name:
      - httpd
      - mariadb
      - mariadb-server
```



## apt模块

模块参数：

- pkg
- state: latest

## service模块

作用: 管理服务 （启动、关闭、重启服务）

模块参数：

- name: 服务名称
- state:  started-启动、stopped-关闭 、restarted-重新启动、reloaded-重载 
- enabled:  设置服务开机自动启动，参数为yes|no
- arguments：服务参数



命令示例:

```bash
# 启动httpd
ansible test -m service "name=httpd state=started"
```



playbook task示例: 

```yaml
- name: start firewalld
  service:
    name: firewalld
    state: started
    enable: yes
```



## lvg模块

作用: 创建、删除卷组(VG)，修改卷组大小

模块参数：

- state: present-创建，absent-删除
- vg
- pvs



命令示例

```bash
# 创建名称为myvg的卷组，该卷组由/dev/vdb1组成
ansible test -m lvg -a "vg=myvg pvs=/dev/vdb1"

# 修改卷组大小
ansible test -m lvg -a "vg=myvg pvs=/dev/vdb1,/dev/vdb2"
```



## lvol模块

作用: 

模块参数：





## parted模块

作用: 

模块参数：



## filesystem模块

作用: 

模块参数：



## setup模块

作用:  收集指定服务器的信息（facts）

模块参数：



## debug模块

作用: 

模块参数：



## firewalld模块

作用: 防火墙管理

模块参数：

- port
- permanent
- state



playbook task示例: 

```yaml
- name: set firewalld rule.
  firewalld:
    port: 80/tcp
    permanent: yes
    state: enabled
```



## template模块

作用: 

模块参数：



## cron模块

作用: 设置定时任务

模块参数：

- month：指定月份
- minute: 指定分钟
- job: 指定任务
- day： 指定哪一天
- hour: 指定小时
- weekday：表示周几
- state: 表示是添加还是删除,present：添加，absent：移除



常用命令: 

```shell
 # 每10分钟
 ansible test -m cron -a 'minute="*/10" job="/bin/echo hello"'
```



## synchronize

作用: 使用rsync同步文件

模块参数：

- archive: 归档，相当于同时开启recursive(递归)、links、perms、times、owner、group、-D选项都为yes ，默认该项为开启
- checksum: 跳过检测sum值，默认关闭
- compress:是否开启压缩
- copy_links：复制链接文件，默认为no ，注意后面还有一个links参数
- delete: 删除不存在的文件，默认no
- dest：目录路径
- dest_port：默认目录主机上的端口 ，默认是22，走的ssh协议
- dirs：传速目录不进行递归，默认为no，即进行目录递归
- rsync_opts：rsync参数部分
- set_remote_user：主要用于/etc/ansible/hosts中定义或默认使用的用户与rsync使用的用户不同的情况
- mode: push或pull 模块，push模的话，一般用于从本机向远程主机上传文件，pull 模式用于从远程主机上取文件



## get_url模块

作用: 下载

模块参数：

- url: 文件的下载地址（网址）---必须
- dest: 指定将文件下载的绝对路径---必须
- url_username: 用于http基本认证的用户名
- url_password： 用于http基本认证的密码
- validate_certs： 如果否，SSL证书将不会验证。这只应在使用自签名证书的个人控制站点上使用
- owner： 指定属主
- group： 指定属组
- mode： 指定权限



playbook示例:

```yaml
- name: Download mysql package
  get_url:
    url: https://mirrors.aliyun.com/mysql/MySQL-8.0/mysql-8.0.27-1.el7.x86_64.rpm-bundle.tar.asc
    dest: /opt/soft
```



## mount模块

作用: 磁盘挂载

模块参数：

- name：必选项，挂载点 
- opts：传递给mount命令的参数
- src：必选项，要挂载的文件 state：必选项 present：只处理fstab中的配置  absent：删除挂载点  mounted：自动创建挂载点并挂载之 umounted：卸载





## unarchive模块

作用: 解压文件

模块参数：

- src



## git模块

作用: 

模块参数：

- repo：远程git库的地址，可以是一个git协议，ssh协议或者http协议的git库地址
- dest：必选参数，git库clone到本地服务器以后保存的绝对路径
- version：克隆远程git库的版本，取值可以为HEAD，分支名称，tag的名称，也可以是一个commit的hash值
- foces：默认为no，当该选项为yes时，如果本地git库有修改，将会抛弃本地的修改(强制覆盖)
- accept_hostkey: 当该选项取值为yes时，如果git库服务器不再know_hosts中，则添加到know_hosts中，key_file指定克隆远程git库地址时使用的私钥。





## hostname 模块

作用：

模块参数：



## stat 模块

作用：

模块参数：



## authorized_key模块

作用：分发 ansible 控制端的 ssh 公钥到远程服务器

模块参数：

playbook示例:

```yaml
- name: install sshkey
  authorized_key:
    user: root
    key: "{{ lookup('file', '/root/.ssh/id_rsa.pub')}}"
    state: present
```



## systemd模块

