## 介绍

使用xpath或者css选择器解析html



## 安装

```bash
pip install parsel
```





## 使用

```python
from parsel import Selector

sel = Selector(html)

title = sel.xpath('//div[@class="title"]/text()').get()

sel.css('')
```

