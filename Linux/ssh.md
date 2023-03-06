## 介绍



## 文件列表

- known_hosts
- id_rsa   私钥
- id_rsa.pub 公钥
- config   配置主机别名
- authorized_keys 免密访问主机的公钥



## 生成key

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

```
静默生成密钥对
ssh-keygen -t rsa -f /root/.ssh/id_rsa -N ''
```

参数:

| 参数 | 说明       |
| ---- | ---------- |
| -t   | 类型 如rst |
| - N  | 密码       |
| -f   | 指定文件名 |
| -q   | 静默       |
| -C   | 注释信息   |
|      |            |
|      |            |



## 配置免密登陆

```bash
ssh-copy-id -i .ssh/id_rsa.pub root@hostname
```



## 编辑 .ssh/config

```
Host hostname
    HostName 149.129.246.83
    Port 22
    User root
    IdentityFile ~/.ssh/id_rsa
```



## 修改权限

```bash
chmod  600  ~/.ssh/*
```