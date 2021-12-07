## 一、docker compose
```yaml
rabbitmq:
    hostname: my-rabbit
    image: rabbitmq:3.8.9-management
    restart: always
    ports:
      - 15672:15672
      - 4369:4369
      - 5672:5672
      - 25672:25672
    volumes:
      - D:\developer\dockerdata\rabbitmq\data:/var/lib/rabbitmq
      - D:\developer\dockerdata\rabbitmq\log:/var/log/rabbitmq/log
    environment:
      # 默认虚拟主机
      RABBITMQ_DEFAULT_VHOST: "/demo"
      # 管理后台账户密码
      RABBITMQ_DEFAULT_USER: "zheng"
      RABBITMQ_DEFAULT_PASS: "123456"
```



## 二、手动安装

### 安装erlang
### 安装rabbitmq
### 配置管理后台



## 三、Mac安装

```bash
brew install rabbitmq
// 补充启动
```

