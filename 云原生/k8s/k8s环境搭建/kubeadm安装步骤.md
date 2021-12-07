## 介绍
使用centos7搭建一主两从k8s集群

## 1. 主机规划
- master 192.168.216.128
- worker1 192.168.216.130
- worker2 192.168.216.131


## 2. 编辑`/etc/hosts`文件
```
192.168.216.128 master
192.168.216.130 worker1
192.168.216.131 worker2
```

> 使用`ping` 进行服务器之间回声测试

## 3. 时间同步
```bash
systemctl enable chronyd --now
date
```

## 4. 禁用iptables和firewalld防火墙服务
```bash
systemctl disable firewalld --now

systemctl disable iptables --now
```

## 5. 禁用selinux
- 使用 `getenforce` 命令查看, 输出**Enforcing**代表开启
- 编辑 `/etc/selinux/config`, 将`enforcing` 改为`disabled`
- 重启系统，使用`getenforce`再次检查, 输出 **Disabled**代表关闭


## 6. 永久禁用swap分区
- 修改`/etc/fstab`, 使用井号注释掉最后一行swap
- 使用free -h命令， swap一行为空


## 7. 网络设置
```
vim /etc/sysctl.d/kubernetes.conf
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
net.ipv4.ip_forward = 1

#重新加载配置
sysctl -p

# 加载网桥过滤模块
modprobe br_netfilter

# 查看模块
lsmod | grep br_netfilter
```

## 8. 安装ipset和ipvsadmin
```
# 安装
yum install ipset ipvsadmin -y

# 增加配置文件
cat <<EOF > /etc/sysconfig/modules/ipvs.modules
#!/bin/bash
modprobe -- ip_vs
modprobe -- ip_vs_rr
modprobe -- ip_vs_wrr
modprobe -- ip_vs_sh
modprobe -- nf_conntrack_ipv4
EOF

# 增加执行权限
chmod +x /etc/sysconfig/modules/ipvs.modules

# 执行
/bin/bash /etc/sysconfig/modules/ipvs.modules

# 查看
lsmod | grep -e ip_vs -e nf_conntrack_ipv4
```

## 9. 重启系统 & 检查
```
# 重启系统
reboot

# 查看禁用selinux是否成功
getenforce

# 查看禁用swap分区是否成功
free -h
```

## 10. 安装docker
```
# 切换docker镜像源
wget https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo -O /etc/yum.repos.d/docker-ce.repo

# 列出docker版本
yum list docker-ce --showduplicates

# 安装docker
yum install --setopt=obsoletes=0 docker-ce-18.06.3.ce-3.el7 -y
```

## 13. 添加docker配置文件
```
# 创建目录
mkdir /etc/docker

# 添加配置文件
cat <<EOF > /etc/docker/daemon.json
{
    "exec-opts": ["native.cgroupdriver=systemd"],
    "registry-mirrors": ["https://d1zfuwq5.mirror.aliyuncs.com"]
}
EOF
```

## 14. docker 重启 & 设置开机自启
```
systemctl restart docker
systemctl enable docker
```

## 15. 查看docker版本
```
docker version
docker info
```

## 16. 配置k8s镜像源
```
cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://mirrors.aliyun.com/kubernetes/yum/repos/kubernetes-el7-x86_64/
enabled=1
gpgcheck=0
repo_gpgcheck=0
gpgkey=https://mirrors.aliyun.com/kubernetes/yum/doc/yum-key.gpg https://mirrors.aliyun.com/kubernetes/yum/doc/rpm-package-key.gpg
EOF
```

## 安装k8s
```
yum install --setopt=obsoletes=0 kubeadm-1.17.4-0 kubelet-1.17.4-0 kubectl-1.17.4-0 -y
```

## 编辑 `/etc/sysconfig/kubelet`
删除原来存在的一行配置信息
```
KUBELET_CGROUP_ARGS="--cgroup-driver=systemd"
KUBE_PROXY_MODE="ipvs"
```

## 设置k8s开机自启
```
systemctl enable kubelet --now
```

## 列出镜像
```
kubeadm config images list
```

## 安装镜像
```
images=(
kube-apiserver:v1.17.4
kube-controller-manager:v1.17.4
kube-scheduler:v1.17.4
kube-proxy:v1.17.4
pause:3.1
etcd:3.4.3-0
coredns:1.6.5
)
```

## 从国内拉取镜像并修改tag名称
```
for imageName in ${images[@]} ; do
  docker pull registry.cn-hangzhou.aliyuncs.com/google_containers/$imageName
  docker tag registry.cn-hangzhou.aliyuncs.com/google_containers/$imageName k8s.gcr.io/$imageName
  docker rmi registry.cn-hangzhou.aliyuncs.com/google_containers/$imageName
done
```

## 以下命令仅在master节点上执行
```
kubeadm init \
  --kubernetes-version=v1.17.4 \
  --pod-network-cidr=10.244.0.0/16 \
  --service-cidr=10.96.0.0/12 \
  --apiserver-advertise-address=<替换成master-ip>
```

## slave节点执行
```
kubeadm join <替换成master-ip>:6443 --token rg2t2a.f25psi7aechib9ig \
    --discovery-token-ca-cert-hash sha256:7f237b38ec465a73e1247e18d0e1206f4a95da8e174cc700635280a48702608d
```

## master节点执行
```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

## 安装网络插件
```
wget https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
```

## 创建kube-flannel.yml
> 需要复制到本地的文件, 然后通过ftp传输过去

```
---
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: psp.flannel.unprivileged
  annotations:
    seccomp.security.alpha.kubernetes.io/allowedProfileNames: docker/default
    seccomp.security.alpha.kubernetes.io/defaultProfileName: docker/default
    apparmor.security.beta.kubernetes.io/allowedProfileNames: runtime/default
    apparmor.security.beta.kubernetes.io/defaultProfileName: runtime/default
spec:
  privileged: false
  volumes:
  - configMap
  - secret
  - emptyDir
  - hostPath
  allowedHostPaths:
  - pathPrefix: "/etc/cni/net.d"
  - pathPrefix: "/etc/kube-flannel"
  - pathPrefix: "/run/flannel"
  readOnlyRootFilesystem: false
  # Users and groups
  runAsUser:
    rule: RunAsAny
  supplementalGroups:
    rule: RunAsAny
  fsGroup:
    rule: RunAsAny
  # Privilege Escalation
  allowPrivilegeEscalation: false
  defaultAllowPrivilegeEscalation: false
  # Capabilities
  allowedCapabilities: ['NET_ADMIN', 'NET_RAW']
  defaultAddCapabilities: []
  requiredDropCapabilities: []
  # Host namespaces
  hostPID: false
  hostIPC: false
  hostNetwork: true
  hostPorts:
  - min: 0
    max: 65535
  # SELinux
  seLinux:
    # SELinux is unused in CaaSP
    rule: 'RunAsAny'
---
kind: ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: flannel
rules:
- apiGroups: ['extensions']
  resources: ['podsecuritypolicies']
  verbs: ['use']
  resourceNames: ['psp.flannel.unprivileged']
- apiGroups:
  - ""
  resources:
  - pods
  verbs:
  - get
- apiGroups:
  - ""
  resources:
  - nodes
  verbs:
  - list
  - watch
- apiGroups:
  - ""
  resources:
  - nodes/status
  verbs:
  - patch
---
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: flannel
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: flannel
subjects:
- kind: ServiceAccount
  name: flannel
  namespace: kube-system
---
apiVersion: v1
kind: ServiceAccount
metadata:
  name: flannel
  namespace: kube-system
---
kind: ConfigMap
apiVersion: v1
metadata:
  name: kube-flannel-cfg
  namespace: kube-system
  labels:
    tier: node
    app: flannel
data:
  cni-conf.json: |
    {
      "name": "cbr0",
      "cniVersion": "0.3.1",
      "plugins": [
        {
          "type": "flannel",
          "delegate": {
            "hairpinMode": true,
            "isDefaultGateway": true
          }
        },
        {
          "type": "portmap",
          "capabilities": {
            "portMappings": true
          }
        }
      ]
    }
  net-conf.json: |
    {
      "Network": "10.244.0.0/16",
      "Backend": {
        "Type": "vxlan"
      }
    }
---
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: kube-flannel-ds
  namespace: kube-system
  labels:
    tier: node
    app: flannel
spec:
  selector:
    matchLabels:
      app: flannel
  template:
    metadata:
      labels:
        tier: node
        app: flannel
    spec:
      affinity:
        nodeAffinity:
          requiredDuringSchedulingIgnoredDuringExecution:
            nodeSelectorTerms:
            - matchExpressions:
              - key: kubernetes.io/os
                operator: In
                values:
                - linux
      hostNetwork: true
      priorityClassName: system-node-critical
      tolerations:
      - operator: Exists
        effect: NoSchedule
      serviceAccountName: flannel
      initContainers:
      - name: install-cni
        image: registry.cn-hangzhou.aliyuncs.com/zxyle/flannel:v0.13.1-rc1
        command:
        - cp
        args:
        - -f
        - /etc/kube-flannel/cni-conf.json
        - /etc/cni/net.d/10-flannel.conflist
        volumeMounts:
        - name: cni
          mountPath: /etc/cni/net.d
        - name: flannel-cfg
          mountPath: /etc/kube-flannel/
      containers:
      - name: kube-flannel
        image: registry.cn-hangzhou.aliyuncs.com/zxyle/flannel:v0.13.1-rc1
        command:
        - /opt/bin/flanneld
        args:
        - --ip-masq
        - --kube-subnet-mgr
        resources:
          requests:
            cpu: "100m"
            memory: "50Mi"
          limits:
            cpu: "100m"
            memory: "50Mi"
        securityContext:
          privileged: false
          capabilities:
            add: ["NET_ADMIN", "NET_RAW"]
        env:
        - name: POD_NAME
          valueFrom:
            fieldRef:
              fieldPath: metadata.name
        - name: POD_NAMESPACE
          valueFrom:
            fieldRef:
              fieldPath: metadata.namespace
        volumeMounts:
        - name: run
          mountPath: /run/flannel
        - name: flannel-cfg
          mountPath: /etc/kube-flannel/
      volumes:
      - name: run
        hostPath:
          path: /run/flannel
      - name: cni
        hostPath:
          path: /etc/cni/net.d
      - name: flannel-cfg
        configMap:
          name: kube-flannel-cfg
```

## 安装flannel
```
kubectl apply -f kube-flannel.yaml
```

## 测试节点状态
```
kubectl get nodes
```

## 查看pod
```
kubectl get pods -n kube-system
```

## 测试是否正常
```
kubectl create deployment nginx --image=nginx:1.14-alpine
kubectl expose deployment nginx --port=80 --type=NodePort
```