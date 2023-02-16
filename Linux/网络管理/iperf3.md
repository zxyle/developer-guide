## 介绍

TCP、UDP 和 SCTP 速度测试工具



## 安装

```bash
yum install iperf3 -y
```



## 开启服务端

```bash
iperf3 -s
```



## 客户端测试

```bash
iperf3 -c 服务端IP
```



-R 下载

-P 10 



## 输出解析

```bash
Connecting to host 127.0.0.1, port 5201
[  4] local 127.0.0.1 port 35530 connected to 127.0.0.1 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  3.03 GBytes  26.0 Gbits/sec    0   2.00 MBytes
[  4]   1.00-2.00   sec  2.50 GBytes  21.5 Gbits/sec    0   2.00 MBytes
[  4]   2.00-3.00   sec  2.57 GBytes  22.1 Gbits/sec    0   2.00 MBytes
[  4]   3.00-4.00   sec  2.47 GBytes  21.3 Gbits/sec    0   2.00 MBytes
[  4]   4.00-5.00   sec  3.04 GBytes  26.1 Gbits/sec    0   2.00 MBytes
[  4]   5.00-6.00   sec  3.24 GBytes  27.8 Gbits/sec    0   2.00 MBytes
[  4]   6.00-7.00   sec  3.20 GBytes  27.5 Gbits/sec    0   2.00 MBytes
[  4]   7.00-8.00   sec  2.99 GBytes  25.7 Gbits/sec    0   2.00 MBytes
[  4]   8.00-9.00   sec  3.03 GBytes  26.1 Gbits/sec    0   2.00 MBytes
[  4]   9.00-10.00  sec  3.05 GBytes  26.2 Gbits/sec    0   2.00 MBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  29.1 GBytes  25.0 Gbits/sec    0             sender
[  4]   0.00-10.00  sec  29.1 GBytes  25.0 Gbits/sec                  receiver

iperf Done.
```

