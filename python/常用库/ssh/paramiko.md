### 安装

```bash
pip install paramiko==2.11.0
```



### 示例

```python
import paramiko

# 登录到服务器
ssh_client = paramiko.SSHClient()
ssh_client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
ssh_client.connect("10.33.80.44", username="root", password="123456")
sftp = ssh_client.open_sftp()

# 执行命令
cmd = f"kubectl get pod -n canal | grep {pod_name_keyword}"
stdin, stdout, stderr = ssh_client.exec_command(cmd)
pod_name = stdout.read().decode('utf-8').split(" ")[0].strip()
print(f"PodName: {pod_name}")

# 文件下载到本地
sftp.get("/root/logs.tar.gz", "logs.tar.gz")

# 文件上传到远程
sftp.put("./README.txt", "/root/README.txt")

# 关闭SSHClient
ssh_client.close()

```

