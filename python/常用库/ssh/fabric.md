### 介绍



### 安装

```bash
pip install fabric==2.7.0
```





### 示例

```python
from fabric import Connection, SerialGroup
from invoke import Exit

SERVER1 = "root@10.33.80.84"
SERVER2 = "root@10.33.80.85"
groups = SerialGroup(SERVER1, SERVER2)


def disk_free(c):
    uname = c.run('uname -s', hide=True)
    if 'Linux' in uname.stdout:
        command = "df -h / | tail -n1 | awk '{print $5}'"
        return c.run(command, hide=True).stdout.strip()
    err = "No idea how to get disk space on {}!".format(uname)
    raise Exit(err)


def memory_free(c):
    c.run("free -h")


def uptime(c):
    c.run("uptime")


for cxn in groups:
    print(f"服务器地址: {cxn.host}")
    print("磁盘占用率: {}".format(disk_free(cxn)))
    print("内存情况: ")
    memory_free(cxn)
    print("负载情况: ")
    uptime(cxn)
```

