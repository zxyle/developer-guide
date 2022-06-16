

### mac重置网络

```bash
cd /Library/Preferences/SystemConfiguration

# 删除 除com.apple.Boot.plist 之外所有文件
rm -rf !(com.apple.Boot.plist)
```



### 删除残留图标

方法1： 进入启动台 -> control+option+command -> 进行删除

方法2: 进入访达 前往 `/private/var/folders`  搜索com.apple.dock.launchpad， 找到db，使用navicat打开这个文件 , 在apps表里删除对应图标，然后命令行执行`killall Dock`

参考文章https://blog.csdn.net/wang11yangyang/article/details/118963412
