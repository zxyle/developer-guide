



### 1. 合并多个txt文件

```bash
cat hello.txt world.txt > merge.txt

cat *.txt > merge.txt
```





### 2.对txt按行去重

```
vim example.txt

输入:sort u
然后保存并推出
```





### 3. 查看文件行数

```bash
wc -l example.txt
```



### 4. 查看文件头尾

```bash
head -n 行数 example.txt
tail -n 行数 example.txt
```



### 5. 全局替换字符串

```
vim example.txt

:%s/old/new/
```

