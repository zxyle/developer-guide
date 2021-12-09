```shell
#!/bin/bash
# crontab
# 0 1 * * * root sh /data/shell/uploadLogData/sh >> /data/shell/uploadLogData.log

# 获取昨天日期字符串
yesterday=$1
if [[ "$yesterday" = "" ]] 
then
	yesterday=`date +%Y_%m_%d --date="1 days ago"`
fi

# 拼接日志文件路径信息
logPath=/data/log/access_${yesterday}.log

# 将日期字符串中的_去掉，并且拼接成hdfs的路径
hdfsPath=/log/${yesterday//_/}

# 在hdfs上面创建目录
hdfs dfs -mkdir -p ${hdfsPath}

# 将数据上传到hdfs的指定目录中
hdfs dfs -put ${logPath} ${hdfsPath}
```

