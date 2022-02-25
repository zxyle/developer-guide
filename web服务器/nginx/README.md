## 介绍



## 安装

```bash
# 安装nginx
yum install epel-release -y
yum install nginx -y

# 启动并设置开机自启
systemctl enable nginx --now

# 查看安装状态
systemctl status nginx
```



## 配置文件

- 配置文件地址: /etc/nginx
- 默认静态资源: /usr/share/nginx/html



## 常用命令

- nginx -t   检查配置文件是否正确
- nginx -s reload  修改配置文件后，重启