```sequence
Notability -> 订阅者: 我打算更改为年费订阅制。
Note right of 订阅者: 订阅者开始抗议
订阅者 --> Notability: 老子以后不更新
```

```flow
st=>start: Notability更改为年费订阅制
op=>operation: 订阅者开始抗议
cond=>condition: 抗议成功?
e=>end: 取消更改

st->op->cond
cond(yes)->e
cond(no)->op
```

