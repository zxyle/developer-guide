## 安装

```bash
pip install yaml
```



## 使用

```python
import yaml

with open('config.yaml', encoding='utf-8') as file:
    res = yaml.load(file, yaml.BaseLoader)
```

