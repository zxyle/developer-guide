

## 创建项目

```bash
mkdir myapp && cd myapp

yarn create @umijs/umi-app

# 安装依赖
yarn

# 启动项目
yarn start

# 项目打包发布
yarn build
```


## 目录介绍
- dist 打包编译后文件
- mock 模拟接口
- node_modules 
- src 
  -   .umi 临时文件
  -   page 路由组件
  -   layouts 布局文件
  -   wrappers 
- public 直接copy到输出目录 不会被编译
- package.json 依赖信息
- .editorconfig 编辑器配置
- .gitignore 
- .prettierignore 哪些文件不需要格式化 忽略
- .prettierrc 代码格式化配置
- .umirc.ts umi核心配置文件
- README.md
- tsconfig.json ts配置文件
- typings.d.ts ts类型定义文件
- yarn.lock
- .env 



## 常用配置项(.umirc.ts 文件)

- hash true 生成文件增加哈希后缀 如 umi.6ab158c2.js umi.acf81312.css
- base 路由前缀
- publicPath 静态文件前缀 适用于CDN。 http://cdn.xxx.com
- outputPath 设置yarn build 输入目录名称
- title 设置html title标签里内容， 路由也有一个title
- history:  hash带井号 browser
- targets 配置浏览器最低兼容版本
- proxy 配置后端接口地址
- theme 配置主题
- routes 路由配置
- title 配置页面标题



## 路由配置

## 页面跳转

声明式:

```javascript
import {Link} from 'umi';

<Link to="/user/one">跳转user1</Link>   
```

命令式:

```javascript
function goToPage(){
    history.push("/user/one");
  }

<button onClick={() => {goToPage()}}>点我跳转</button>
```



## html模板

在@umijs/core/lib/Html/document.ejs
在src/pages下 创建document.ejs



## Mock数据

