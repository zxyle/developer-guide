

## tar命令

- 打包  `tar cvf FileName.tar DirName`
- 解包 `tar xvf FileName.tar`



## 打包并压缩

```
tar [压缩格式]cvf FileName.tar.gz DirName
```

压缩格式:

- z: gzip格式
- j: bizp格式



## 解压

```
tar [压缩格式]xvf FileName.tar.gz -C /opt
```





## 其他格式

```
.bz2格式
解压1：[＊＊＊＊＊＊＊]$ bzip2 -d FileName.bz2
解压2：[＊＊＊＊＊＊＊]$ bunzip2 FileName.bz2
压 缩： [＊＊＊＊＊＊＊]$ bzip2 -z FileName

.bz格式
解压1：[＊＊＊＊＊＊＊]$ bzip2 -d FileName.bz
解压2：[＊＊＊＊＊＊＊]$ bunzip2 FileName.bz

.gz格式
解压1：[＊＊＊＊＊＊＊]$ gunzip FileName.gz
解压2：[＊＊＊＊＊＊＊]$ gzip -d FileName.gz
压 缩：[＊＊＊＊＊＊＊]$ gzip FileName

.Z格式
解压：[＊＊＊＊＊＊＊]$ uncompress FileName.Z
压缩：[＊＊＊＊＊＊＊]$ compress FileName

.zip格式
解压：[＊＊＊＊＊＊＊]$ unzip FileName.zip
压缩：[＊＊＊＊＊＊＊]$ zip FileName.zip DirName
```