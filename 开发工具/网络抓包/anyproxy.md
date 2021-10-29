## 介绍
anyproxy是阿里开源的一个抓包工具 [官网地址](https://anyproxy.io/cn/)

## 使用步骤

- 安装: `npm install -g anyproxy`

- 启动: `anyproxy -i`

  > -i : 监听https

- 访问: http://127.0.0.1:8002

## rule的使用
```
// file: sample.js
// anyproxy -i --rule sample.js

const redis = require('redis');

const client = redis.createClient('6379', '127.0.0.1');

module.exports = {
    summary: 'a rule to get shop id',
    * beforeSendRequest(requestDetail) {
        let buf;
        if (requestDetail.url.indexOf('shopId') !== -1 || requestDetail.url.indexOf('ccapp.cib.com.cn/o2o-api/share/shareShop') !== -1) {
            buf = requestDetail.requestData;
            const value = buf.toString('utf8');
            if (value.trim() !== "") {
                client.lpush("credit:cib", value.replace("shopId=",""));
            }
            console.log(requestDetail.url);
            console.log(value);
            return null;
        }

    },

};
```