## 简介

python http请求库



## 安装依赖

```bash
pip install requests
```



## 基本使用

```python
import requests

resp = requests.get("https://httpbin.org/ip")
print(resp.text)  # {"origin": "183.129.232.234"}
print(resp.status_code)  # 200
print(resp.reason)  # OK
print(resp.url)  # https://httpbin.org/ip
print(resp.content)  # 二进制数据
```





## url参数

```python
params = {
  "name": "xx",
  "age": 11
}
resp = requests.get("https://httpbin.org/ip", params=params)
print(resp.url)
```





## 自定义headers

```python
headers = {
    "User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 \
    (KHTML, like Gecko) Chrome/95.0.4638.69 Safari/537.36"}

resp = requests.get("https://httpbin.org/ip", headers=headers)
```





## 使用Session

```python
from requests import Session

session = Session()
session.verify = False
session.headers

resp = session.get("https://httpbin.org/ip")
```



## post json

```python
```





## post form-data

```python
```







## 使用代理

```python
proxies = {
    'http': 'http://',
    'https': 'https://',
}

r = requests.get('url', proxies=proxies)
```

