## 介绍

用于构建用户界面的JavaScript库， Facebook开源, https://reactjs.org/, 面向组件编程



## 原生痛点

- 原生JS操作DOM繁琐、效率低（DOM-API 操作UI）
- 使用JS直接操作DOM，浏览器会进行大量**重绘重排**
- 原生JS没有**组件化**编码方案，代码复用率低。



## React特点

- 采用**组件化**模式、**声明式编码**，提高开发效率及组件复用率
- React Native 进行移动端开发
- 使用**虚拟DOM**+优秀的Diffing算法，尽量减少与真实DOM的交互



## 虚拟DOM

- 本质是一个Object
- 虚拟DOM比较轻量化，真实DOM比较重量化



## 创建虚拟DOM方法

- React.createElement()
- JSX





## 组件

- 函数式组件
- 类组件



### 函数式组件

- 组件名为函数名，需要使用大写开头
- 需要返回值，返回JSX
- 使用的时候 `<Hello />`

```jsx
function Hello() {
    return <h1>Hello World</h1>
}
```



### 类组件

- 需要继承   `React.Component `
- 需要重写render方法，返回JSX

```jsx
class Hello extends React.Component {
    render() {
        return <p>Hello</p>
    }
}
```



## 复杂组件

看是否包含状态（state）





## 状态

- 状态初始化
- 状态读取
- 状态修改
