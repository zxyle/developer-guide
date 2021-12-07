## 查看网络信息

```
docker network ls 
NETWORK ID     NAME      DRIVER    SCOPE
fe3960b17b58   bridge    bridge    local
d20d2e1e4b22   host      host      local
124b3aca4424   none      null      local
```



```
docker network create --subnet=网段 网络名称
```



```
docker network rm 网络名称
```

