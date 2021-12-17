

## ref

```jsx
```



## useState

函数组件 内部状态管理

```jsx
// count初始值为0， 通过setCount来修改
const [count, setCount] = useState(0);
```





## useEffect

```javascript
// 当count状态发生变化，就会调用该函数
useEffect(() => {
    setEffect(effect+1);
}, [count])

```

