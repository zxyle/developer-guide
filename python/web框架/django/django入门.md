## 创建项目



## 创建app



## 开启admin后台 需要创建用户

```bash
python manage.py makemigration
python manage.py createsuperuser
```



## 编写model

```python
from django.db import models


class Person(models.Model):
    first_name = models.CharField(max_length=30)
    last_name = models.CharField(max_length=30)
```

