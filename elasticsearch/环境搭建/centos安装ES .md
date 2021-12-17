## 安装步骤

```bash
# 下载rpm包
wget https://mirrors.aliyun.com/elasticstack/7.x/yum/7.16.1/elasticsearch-7.16.1-x86_64.rpm

# 安装
rpm -ivh elasticsearch-7.16.1-x86_64.rpm

# 设置自启并立即启动
sudo systemctl daemon-reload
sudo systemctl enable elasticsearch.service --now

# 设置环境变量
echo "export ELASTICSEARCH_HOME=/usr/share/elasticsearch" >> /etc/profile
echo "export PATH=$PATH:$ELASTICSEARCH_HOME/bin" >> /etc/profile

# 测试
curl http://127.0.0.1:9200/
```



## 安装目录

- 安装位置 : `/usr/share/elasticsearch/`
- 配置文件:  `/etc/elasticsearch/`
- 数据目录: `/var/lib/elasticsearch/`
- 日志目录: `/var/log/elasticsearch/`
- service: `/usr/lib/systemd/system/elasticsearch.service`



## 其他设置

```bash
# 设置外网访问
echo "http.host: 0.0.0.0" >> /etc/elasticsearch/elasticsearch.yml

# 重启服务
systemctl restart elasticsearch
```



