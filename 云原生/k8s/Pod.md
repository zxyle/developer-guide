## 介绍

pod是k8s集群进行管理的最小单元, 程序要运行必须部署在容器中, 而容器必须存在于pod中, pod可以认为是容器的封装, 一个pod中可以存在一个或者多个容器。

> pod 类比为ipod, 里面的音乐、视频软件则为一个个容器



### 命令行操作

- 创建: `kubectl run <pod-name> --image=nginx:1.17.1 --port=80 --namespace=dev`
- 查看: `kubectl get pod -n dev -o wide|yaml|json`
- 描述: `kubectl describe pod <pod-name> -n dev`
- 删除: `kubectl delete pod <pod-name> -n dev`
- 从pod复制文件出来: `kubectl cp <pod-name>:<容器内路径> <本地路径> -n <namespace>`

- 进入pod命令行: `kubectl exec -it <pod-name> -n <namespace> -- /bin/sh`



### 使用配置文件

```yaml
# pod-nginx.yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  namespace: dev
spec:
  containers:
    - image: nginx:1.17.1
      imagePullPolicy: IfNotPresent
      name: pod
      ports:
        - name: nginx-port
          containerPort: 80
          protocol: TCP
```

- 创建资源: `kubectl create -f pod-nginx.yaml`
- 删除资源: `kubectl delete -f pod-nginx.yaml`

