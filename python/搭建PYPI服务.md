## 介绍

https://github.com/pypiserver/pypiserver



## 安装

```shell
pip install pypiserver==1.3.2
pip install passlib==1.7.2
```



## Dockerfile

```dockerfile
FROM pypiserver/pypiserver:latest

EXPOSE 8080
```



## htpasswd.txt

```
admin:{SHA}fEqNCco3Yq9h5ZUglD3CZJT4lBs=
```



## start.sh

```
pypi-server -p 8080 -P . -a . ./packages
```

