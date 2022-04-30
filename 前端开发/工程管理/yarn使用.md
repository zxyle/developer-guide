## 介绍
facebook出品的包管理工具， https://yarnpkg.com/



## 安装

```bash
npm install -g yarn
```



## 初始化项目(相当于npm init)

```bash
yarn init
```



## 安装依赖(相当于npm install)

```bash
yarn 或 yarn install
```



## 启动服务

```bash
yarn start
```



## 添加依赖

```bash
yarn add 包名
```



## 编译打包

```bash
yarn build
```



## 测试

```bash
yarn test
```



## 下载源管理

```bash
// 查看当前源
yarn config get registry
>https://registry.yarnpkg.com

// 设置国内源
yarn config set registry http://registry.npmmirror.com
```



## 清空缓存

```bash
yarn cache clean
```