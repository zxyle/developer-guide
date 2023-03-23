
## 介绍
由阿里开源的Java诊断工具
- [官网地址](https://arthas.aliyun.com/doc/)
- [发布历史](https://github.com/alibaba/arthas/releases)



## 基本使用

```bash
# 下载
curl -O https://alibaba.github.io/arthas/arthas-boot.jar

# 启动
java -jar arthas-boot.jar

# 如提示端口被占用
java -jar arthas-boot.jar --telnet-port 9998 --http-port -1
```



## 常见指令

- dashboard - 数据面板
- exit - 退出



## trace

用于跟踪代码每一个步骤耗时

**格式：** trace + 类路径 + 方法名

```bash
trace com.example.demoapi.biz.auth.service.LoginService login
```

