
## 介绍
由阿里开源的Java诊断工具
- [官网地址](https://arthas.aliyun.com/doc/)
- [github release](https://github.com/alibaba/arthas/releases)

## 基本使用

下载:
```
curl -O https://alibaba.github.io/arthas/arthas-boot.jar
```

启动:
```
java -jar arthas-boot.jar
```

端口被占用
```
java -jar arthas-boot.jar --telnet-port 9998 --http-port -1
```

## 常见指令
- dashboard - 数据面板
- exit