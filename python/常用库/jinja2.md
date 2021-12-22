## 介绍

模板引擎



## 使用案例

### 变量

```jinja2
{{ bootVersion }}
```



### 循环

```jinja2
{%- for property in properties %}
<{{ property.element }}>{{ property.value }}</{{ property.element }}>
{%- endfor %}
```



### 判断

```jinja2
{%- if packaging != 'jar' %}
    <packaging>{{ packaging }}</packaging>
{%- endif %}
```



