## 介绍



## 下载 & 安装

[镜像下载地址](https://mirrors.cloud.tencent.com/gitlab-ce/yum/el7/)





```bash
# 1.  执行以下命令，使用官方脚本添加Yum源。
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.rpm.sh | bash

# 2.  执行以下命令，安装GitLab。
yum -y install gitlab-ee

# 3.  执行以下命令，初始化已经安装好的GitLab。
gitlab-ctl reconfigure

# 4.  执行以下命令，启动GitLab。
gitlab-ctl start

# 5.  执行以下命令，查看GitLab启动情况。
gitlab-ctl status

```

