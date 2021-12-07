## 介绍
abd(Android Debug Bridge)



## 常用命令

- 安装adb : `brew install --cask android-platform-tools`
- 查看设备: `adb devices`
- 连接设备: `adb connect 127.0.0.1:5555`
- 进入设备: `adb shell`
- 安装apk: `adb install`
- 卸载apk: `adb uninstall`
- 发送文件: `adb push <本地路径> <远程路径>`
- 下载文件: `adb pull <远程路径> <本地路径>`


[安卓模拟器端口](https://www.cnblogs.com/Nick1994/p/8342046.html)