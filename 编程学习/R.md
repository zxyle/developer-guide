## 介绍

https://www.r-project.org/



## 安装

https://mirrors.tuna.tsinghua.edu.cn/CRAN/

## 安装三方包

```R
install.packages("plyr")
```



## Http请求

```R
# 加载包
library('rvest')
# 指定要爬取的url
url <- 'http://httpbin.org/ip'

# 从网页读取html代码
webpage <- read_html(url)
print (webpage);
```

