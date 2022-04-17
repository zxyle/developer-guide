## useRef

可以存储、查找组件内的标签或任意其他数据

```jsx
// 函数组件中使用
React.useRef()

// 类组件中使用
React.createRef()
```



## useState

函数式组件 内部状态管理

```jsx
import {useState} from "react";

function App () {
  // count初始值为0，通过setCount来修改
  const [ count, setCount ] = useState(0)
  return (
    <div>
      点击次数: { count } 
      <button onClick={() => { setCount(count + 1)}}>点我</button>
    </div>
  )
}

```





## useEffect

函数组件中执行副作用操作(除了状态相关的逻辑，比如网络请求，监听事件，查找 `dom`)

```javascript
import {useEffect} from "react";

// 第一次执行一次， 当数组里的变量状态发生变化，也会调用该函数
// 数组里为监测的状态
// return 相当于willUnmount, 可以用来清除定时器

const [count, setCount] = useState(0);

useEffect(() => {
    setCount(count+1);
    return () => {}
}, [count])

```



## useCallback

```javascript
```





## useMemo

```javascript
```





## useContext

```javascript
```





## useReducer

```javascript
```





## useImperativeHandle

```javascript
```



## Fragment

防止过度div嵌套，还可以使用key属性，  或者使用空标签代替 `<> </>`