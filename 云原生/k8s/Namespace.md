## 介绍

名称空间是资源的边界, 用来实现资源隔离



## 命令操作

- 查看所有: `kubectl get namespace` 或 `kubectl get ns`
- 查看详情: `kubectl describe ns <namespace-name>`
- 创建空间: `kubectl create ns <namespace-name>`
- 删除空间: `kubectl delete ns <namespace-name>`



## 使用配置文件形式

```yaml
# dev-ns.yml
apiVersion: v1
kind: Namespace
metadata:
  name: dev
```

- 创建资源: `kubectl create -f ns-dev.yaml` 或 `kubectl apply -f ns-dev.yaml `
- 删除资源: `kubectl delete -f ns-dev.yaml`

