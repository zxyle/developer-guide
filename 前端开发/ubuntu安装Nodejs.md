## 下载安装包

- [淘宝镜像](https://npm.taobao.org/mirrors/node/)

- [官方网站](https://nodejs.org/zh-cn/download/releases/)



### step1: 解压到指定目录
```
tar -zxvf node-v8.14.0-linux-x64.tar.gz -C /opt
```

### step2: 创建软链接
```
ln -s /opt/node-v8.14.0-linux-x64/bin/node /usr/bin/node
ln -s /opt/node-v8.14.0-linux-x64/bin/npm /usr/bin/npm
```

### step3: 验证
```
[root@localhost ~]# node -v
v8.14.0

[root@localhost ~]# npm -v
6.4.1
```

补充配置镜像源





```bash
# 1.  执行以下命令，下载Node.js的安装包。
wget https://npm.taobao.org/mirrors/node/v12.4.0/node-v12.4.0-linux-x64.tar.xz

# 2.  执行以下命令，解压Node.js的安装包。
tar -xvf node-v12.4.0-linux-x64.tar.xz

# 3.  执行以下命令，重命名Node.js安装目录。
mv node-v12.4.0-linux-x64/ /usr/local/node

# 执行以下命令，将Node.js的可执行文件目录加入到系统环境变量中。
echo "export PATH=$PATH:/usr/local/node/bin" >> /etc/profile

# 执行以下命令，使刚配置的Node.js环境变量立即生效。
source /etc/profile

# 执行以下命令，分别查看node和npm版本。
node -v
npm -v
```



## 编写示例

```javascript
vim HelloWorld.js

var http = require('http');
http.createServer(function (request, response) {
    response.writeHead(
        200,
        {
            'Content-Type': 'text/plain'
        });
    response.end('Hello World\n');
}).listen(8080);
console.log('Server started');


// 执行node HelloWorld.js
// 访问 http://127.0.0.1:8080/
```

