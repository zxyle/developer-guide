## 介绍

模拟浏览器操作



## 使用步骤

- 查看chrome浏览器版本
- 下载对应版本的驱动

## 驱动下载
- [chromdriver](https://chromedriver.chromium.org/)
- [chromedriver镜像](https://registry.npmmirror.com/binary.html?path=chromedriver/)



## 示例代码

```python
# pip install selenium

from selenium import webdriver
from selenium.webdriver.chrome.options import Options


def get_driver():
    # selenium + chromium
    chromedriver_path = r"D:\developer\software\chromedriver\86\chromedriver.exe"
    pc_ua = "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 \
    (KHTML, like Gecko) Chrome/86.0.4183.83 Safari/537.36"
    chrome_options = Options()
    # chrome_options.add_argument(f'--user-agent={pc_ua}')
    # 设置无头模式
    chrome_options.add_argument('--headless')
    # 禁止发送通知
    chrome_options.add_argument('--disable-notifications')
    return webdriver.Chrome(chromedriver_path, options=chrome_options)


if __name__ == '__main__':
    driver = get_driver()
    driver.get("http://127.0.0.1:8080/hello")
    print(driver.page_source)

```

