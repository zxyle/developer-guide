



## 输入校验

```javascript
rules = {[
    {required: true, message: '请输入旧密码!'},
]}
```



- 必填项校验: `{required: true}`
- 最小长度校验: `{max: 24, min: 24, message: '设备序列号为24位'}`

更多规则 参考 https://ant.design/components/form-cn/#Rule



## 表格渲染

columns

| 属性名    | 作用       | 示例                 |
| --------- | ---------- | -------------------- |
| title     | 表头       |                      |
| dataIndex | 数据属性名 |                      |
| key       |            |                      |
| render    |            | (text, record) => () |

dataSource



## 栅格

一行 使用Row

Row下面是Col ， 一共24等分