## 介绍



## 添加依赖

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-websocket</artifactId>
</dependency>
```



## 配置类

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.socket.server.standard.ServerEndpointExporter;

@Configuration
public class WebSocketConfig {

    /**
     * 注入一个ServerEndpointExporter,该Bean会自动注册使用@ServerEndpoint注解申明的websocket endpoint
     */
    @Bean
    public ServerEndpointExporter serverEndpointExporter() {
        return new ServerEndpointExporter();
    }

}

```



## 测试页面

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>WebSocket</title>
</head>
<body>
<script>
    const socket = new WebSocket("ws://127.0.0.1:8080/websocket")
    socket.onopen = (ws) => {
        console.log("建立连接", ws)
    }

    socket.onmessage = (ws) => {
        console.log("", ws)
    }

    socket.onclose = (ws) => {
        console.log("", ws)
    }

    socket.onerror = (ws) => {
        console.log("", ws)
    }

    setTimeout(() => {
        socket.send("发送一条消息")
    }, 2000)

    setTimeout(() => {
        socket.close()
    }, 5000)


</script>

</body>
</html>
```





```java
package com.example.superpower.modules.ops.websocket;

import org.springframework.stereotype.Component;

import javax.websocket.OnClose;
import javax.websocket.OnError;
import javax.websocket.OnMessage;
import javax.websocket.OnOpen;
import javax.websocket.Session;
import javax.websocket.server.ServerEndpoint;
import java.io.IOException;
import java.util.Map;
import java.util.concurrent.ConcurrentHashMap;

// ws://127.0.0.1:8080/websocket
// wss://
@ServerEndpoint("/websocket")
@Component
public class MyWebSocket {
  
    private static final Map<String, Session> sessionMap = new ConcurrentHashMap<>();

    @OnOpen
    public void onOpen(Session session) throws IOException {
        System.out.println("websocket 已经连接.");
        session.getBasicRemote().sendText("连接已成功, 欢迎您.");
    }

    @OnClose
    public void onClose(Session session) {
        System.out.println("websocket 已关闭");
    }

    // 服务端接收客户端发来的消息
    @OnMessage
    public void onMessage(String message, Session session) throws IOException {
        System.out.println("收到客户端消息: " + message);
        session.getBasicRemote().sendText("消息已收到");

    }

    @OnError
    public void onError(Session session, Throwable error) {
        System.out.println("发生错误");
        error.printStackTrace();
    }
}

```

