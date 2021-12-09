## window

当前浏览器窗口

```javascript
window.alert("HH")
```



## navigator

浏览器信息

```javascript
// 浏览器UA
navigator.userAgent


```



## screen



## history



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





