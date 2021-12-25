## 介绍

JSX (JavaScript XML) 需要babel.js 还有tsx



## 定义虚拟DOM时，不要写引号，直接写HTML



## 引用变量或JS表达式时

使用

```jsx
const name = "zx";
{name}

{1+2}
```



## html的class 需要写className

```jsx
const el (
    <p className="p"></p>

)
```



## 内联样式编写 {{ key: value }}

```jsx
<span styles={{ color: 'red' }}>Hello</span>
```



## 只能有1个根标签

可以使用div作为根标签

```jsx
const el = (
	<div>
        
    </div>
)
```



## 标签必须闭合



## react组件名首字母需要使用大写



## 条件判断

```jsx
```





## 数组遍历

```jsx
const songs = [
        { id: 1, name: "痴心绝对" },
        { id: 2, name: "像我这样的人" },
        { id: 3, name: "南山南" },
      ];

const list = (
    <ul>
        {songs.map((item) => (
            <li key={item.id}>{item.name}</li>
        ))}
    </ul>
);
```



## 特殊属性名

|           |       |      |
| --------- | ----- | ---- |
| className | class |      |
|           |       |      |
|           |       |      |

