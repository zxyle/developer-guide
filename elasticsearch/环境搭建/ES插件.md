## head插件
head是ES集群的Web客户端

https://github.com/mobz/elasticsearch-head



## 中文分词插件

## 安装ik分词器
- 先下载 https://github.com/medcl/elasticsearch-analysis-ik
- 在plugins目录下创建ik 解压将内容放进去
- 使用`./bin/elasticsearch-plugin list`
- 重启ES
- `ik_smart` 和 `ik_max_word`


## 测试分词
```
POST /_analyze
{
    "analyzer": "ik_smart",
    "text": "我是中国人"
}
```

## 自定义词库

### 网络词库

- 创建`fenci.txt` 文件， 每一个词一行
- 放入nginx目录
- 修改`ik/config/IKAnalyzer.cfg.xml`文件
- `<entry key="remote_ext_dict">http://192.168.56.10/es/feci.txt</entry>`
- 重启es



### 本地词库

