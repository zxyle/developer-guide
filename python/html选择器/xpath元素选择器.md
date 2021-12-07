## 介绍
- 测试工具: 
- 测试页面

>>入口节点使用红色标注， 目标节点使用绿色标注
- 获取标签之间的文本 `text()`
- 获取标签的属性 `@属性名` 比如 `@href` 和 `@src`


```html
<div>
<a id="1" href="www.baidu.com">我是第1个a标签</a>
<p>我是p标签</p>
<a id="2" href="www.baidu.com">我是第2个a标签</a>
<a id="3" href="www.baidu.com">我是第3个a标签</a>
<a id="4" href="www.baidu.com">我是第4个a标签</a>
<p>我是p标签</p>
<a id="5" href="www.baidu.com">我是第5个a标签</a>
</div>
```

```
获取第三个a标签的下一个a标签："//a[@id='3']/following-sibling::a[1]"

获取第三个a标签后面的第N个标签："//a[@id='3']/following-sibling::*[N]"

获取第三个a标签的上一个a标签："//a[@id='3']/preceding-sibling::a[1]"

获取第三个a标签的前面的第N个标签："//a[@id='3']/preceding-sibling::*[N]"

获取第三个a标签的父标签："//a[@id=='3']/.."

```


## 包含文本
```
p[contains(text(),'剩余时间')]
```

## string(.)