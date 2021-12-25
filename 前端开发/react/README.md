## 介绍

用于构建用户界面的JavaScript库， Facebook开源, https://zh-hans.reactjs.org/, 面向组件编程



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

- `React.createElement('h1', null, 'Hello React!')`
- JSX语法 (本质还是前者)



## 组件

- 函数式组件
- 类组件



### 函数式组件

- 组件名为函数名，需要以大写字母开头
- 需要返回值，返回JSX
- 使用的时候 `<Hello />`

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

export default Welcome;
```

- 传递参数给组件  `<Welcome name="zheng" />`
- 使用传入属性 `props.属性名`



### 类组件

- 需要继承   `React.Component `
- 需要重写render方法，返回JSX

```jsx
import React from 'react';

class Hello extends React.Component {
    render() {
        return <p>Hello</p>
    }
}

export default Hello;
```

- 不是匿名函数 就需要在构造器里绑定 `this.handleChange = this.handleChange.bind(this);`
- 使用传入属性 `this.props.属性名`

## 状态管理

看是否包含状态（state）来确定是否为复杂组件。state是一个o

### 状态初始化

```jsx
// 构造器里
constructor() {
    super();
    this.state = {
    	count: 0
	}    
}
            
// 初始化state语法（ 简化版 ）
state = {
  count: 0
}
```





### 状态读取

```jsx
this.state.count
```



### 状态修改

- 是合并操作，不是更新操作

```jsx
// 错误的
this.state.comment = 'Hello';

// 正确的
this.setState({
    count: this.state.count - 1
})
```



### useState

```jsx
import React, { useState } from 'react'

// 括号里为初始值
const [ count, setCount ] = useState(0)
```





## props

- 传递组件属性
- 传递
- 传递子组件
- props校验
- props是只读的



## ref

React里获取DOM里的信息

- string ref 效率问题，不推荐使用
- 回调形式ref  `<input ref="{c => this.input1 = c}">`



## 事件处理

- onClick
- onSubmit
- onChange

## 生命周期方法

- componentDidMount 组件挂载
- componentWillUnmount 组件卸载



类组件加载顺序： constructor -> render -> componentDidMount -> componentWillUnmount
