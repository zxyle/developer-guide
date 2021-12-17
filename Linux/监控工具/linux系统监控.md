- sar

- vmstat `vmstat --unit m`

- iostat `iostat -d -k 2` -d磁盘 -k kb 2 2秒/次 yum install sysstat

- pidstat

- htop & top

- ```
  yum install -y sysstat
  ```

```
yum install iotop -y
```



## top

ctrl + E 切换单位



## htop

安装: `yum install htop -y`



## ps

```
ps aux | grep xxx
ps -ef | grep xxx
```

