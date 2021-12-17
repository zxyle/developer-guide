

## mac重置网络

```bash
cd /Library/Preferences/SystemConfiguration

# 删除 除com.apple.Boot.plist 之外所有文件
rm -rf !(com.apple.Boot.plist)
```

