```python
# 抢注python软件包

import os

import requests

root_dir = "./temp"


def is_exist(name):
    """
    检查软件包是否不存在
    True代表存在, False代表不存在
    @param name: 软件包名称
    @return:
    """
    url = f"https://pypi.doubanio.com/simple/{name}"
    resp = requests.head(url)
    return resp.status_code == 200


def seize(name):
    if is_exist(name):
        print(f"软件: {name} 已存在.")
        return

    # write to setup.py
    with open(f"{root_dir}/setup.py", "w") as f:
        f.write("from setuptools import setup\n")
        f.write(f"setup(name=\"{name}\", version=\"0.0.1\")")

    os.chdir(root_dir)
    os.system("rm -rf build *.egg-info dist")
    os.system("python setup.py sdist bdist_wheel")
    os.system("twine upload dist/*")
    os.system("rm -rf setup.py")


if __name__ == '__main__':
    seize("sshp")

```

