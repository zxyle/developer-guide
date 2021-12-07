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

## 安装包(相当于npm install)
```bash
yarn 
```

## 启动服务
```bash
yarn start
```

## 添加包
```bash
yarn add xxx
```

## 下载源管理
```bash
// 查看当前源
yarn config get registry
>https://registry.yarnpkg.com

// 设置国内源
yarn config set registry http://registry.npm.taobao.org
```

## 清空缓存
```bash
yarn cache clean
```