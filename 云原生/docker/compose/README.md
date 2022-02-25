## 简介

https://docs.docker.com/compose/

## 安装
```bash
pip install docker-compose
```


## 基本使用

docker-compose up

## 参数
- up 启动服务
  - -d 后台启动
  - --build 构建镜像
- -f 指定compose文件
- restart 重启服务
- logs 查看日志
  - -f 跟踪日志输出。
  - -t 显示时间戳。
  - --tail 100 从每个容器的日志末尾开始显示的行数。
- down
  - -v 删除卷
  - --rmi all 删除镜像