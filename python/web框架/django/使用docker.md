```dockerfile
FROM python:3.7.6
ENV PYTHONUNBUFFERED 1
RUN mkdir /code
WORKDIR /code
COPY requirements.txt /code/
COPY ./pip.conf /etc/pip.conf
RUN pip install --no-cache-dir --upgrade pip \
     && pip install --no-cache-dir -r requirements.txt
COPY . /code/
```

