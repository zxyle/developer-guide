

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

// count初始值为0，通过setCount来修改
const [count, setCount] = useState(0);

// 修改状态
setCount(100);
```





## useEffect

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



## useMemo



## useContext



## useReducer







## Fragment

防止过度div嵌套，还可以使用key属性，  或者使用空标签代替 `<> </>`