

## 当java输出中文为问号

```bash
# Step 1
vim /etc/locale.conf
LANG="zh_CN.UTF-8"

# Step2
vim ~/.bashrc

# 追加
export LANG='UTF-8'
export LC_ALL='zh_CN.UTF-8'
export LC_CTYPE='zh_CN.UTF-8'

source ~/.bashrc

# Step3
重启项目
```

