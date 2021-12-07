## 介绍

Tornado 是一个 Python 网络框架和异步网络库, https://www.tornadoweb.org/en/stable/



## 入门

```python
# pip install tornado==6.0.4
import tornado.ioloop
import tornado.web


class MainHandler(tornado.web.RequestHandler):
    def get(self):
        self.write("Hello, world")


def make_app():
    return tornado.web.Application([
        (r"/", MainHandler),
    ])


if __name__ == "__main__":
    app = make_app()
    app.listen(8888)
    tornado.ioloop.IOLoop.current().start()
```



