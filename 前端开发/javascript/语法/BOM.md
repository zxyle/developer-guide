## 介绍

浏览器对象模型(Browser Object Model)

## window

当前浏览器窗口

|         | 作用               | 示例                            |
| ------- | ------------------ | ------------------------------- |
| alert   | 弹框               | `alert("Hello World");`         |
| confirm | 对话框，返回布尔值 | `confirm("是否开始？");`        |
| prompt  | 输入框             | `prompt("请输入性别: ", "男");` |



- setInterval
- clearInterval
- console

## navigator

浏览器信息

```javascript
// 浏览器UA
navigator.userAgent


```



## screen

```javascript
screen
```





## history

```javascript
```





## location



## localStorage

本地存储空间, 用于长久保存整个网站的数据，保存的数据没有过期时间，直到手动去除。

```javascript
// 设置
localStorage.setItem("key", "value");

// 获取
localStorage.getItem("key");

// 删除
localStorage.removeItem("key");
```





## sessionStorage

会话存储空间, 用于临时保存同一窗口(或标签页)的数据，在关闭窗口或标签页之后将会删除这些数据。

```javascript
// 设置
sessionStorage.setItem("key", "value");

// 获取
sessionStorage.getItem("key");

// 删除指定key
sessionStorage.removeItem("key");

// 清空
sessionStorage.clear()
```





