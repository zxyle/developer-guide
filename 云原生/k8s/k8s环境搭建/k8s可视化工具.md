## 一、kubesphere

https://kubesphere.com.cn/


## 二、kubernetes dashboard
查看https://github.com/kubernetes/dashboard

1. 部署
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml
```

2. 开启代理
```
kubectl proxy
```

3. 访问:
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/login

创建用户