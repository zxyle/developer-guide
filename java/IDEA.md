## 常用快捷键

- Ctrl + J:           插入快速代码
- Alt + insert:       插入构造方法、getter/setter等
- Ctrl + Alt + V:     生成对象的类信息(生成左边代码)
- Ctrl + D:           复制光标所在行到下一行
- Ctrl + Shift + / :  多行注释快捷键
- Alt + 7             打开结构窗口
- Ctrl + Alt + T      快速生成try...catch代码 , 选中需要包裹的代码



## 设置篇

- 提示不区分大小写，   编辑器 -> 常规 -> 代码完成 -> 取消匹配大小写的勾
- 隐藏不想看到的文件   编辑器 -> 文件类型 -> 切换忽略的文件和文件夹 填写 *.iml HELP.md mvnw mvnw.cmd
- 关闭顶行注释         编辑器 -> 代码样式 -> Java -> 代码生成 -> 取消行注释在第一列勾
- 禁用掉不常用的插件
- 修改编码: 编辑器 -> 文件编码 -> 把GBK全部设置为UTF-8, 并将属性文件默认编码设置为UTF-8并勾选Ascii
- 修改文件模板:  Preferences | 编辑器 | 文件和代码模板|Class

```java
#if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end
#parse("File Header.java")

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class ${NAME} {

    Logger log = LoggerFactory.getLogger(${NAME}.class);
}

```



## 插件篇

[插件中心](https://plugins.jetbrains.com/)

- [JRebel 热部署工具](https://www.cnblogs.com/linliquan/p/12426065.html)
- ignore
- [chinese]()
- MyBatisX
- Translation
- jclasslib
- kubernetes
- SonarLint



## 文件模板

- mybatis mapper.xml
- mybatis-config.xml
- hibernate.cfg.xml
- hibernate mapping xml
- beans.xml
- log4j.xml
- logback.xml loback-spring.xml
- log4j2.xml log4j2-spring.xml



## 如何调试?