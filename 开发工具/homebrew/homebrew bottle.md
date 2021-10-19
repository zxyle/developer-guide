
## 介绍
二进制安装包、安装快速

- [Bottles](https://docs.brew.sh/Bottles)
- [官方仓库](https://bintray.com/homebrew)

## 制作方法
```
brew install --build-bottle <formula>
brew bottle <formula>
```

## 修改formula文件并上传bottle文件
将生成出来的代码粘贴到<formula>.rb文件中
```ruby
bottle do
    root_url "https://zxyle-bottles.oss-cn-hangzhou.aliyuncs.com"
    sha256 cellar: :any_skip_relocation, big_sur: "63bf80db6b43b410e8c0bd4fe42e4e8899814bafa258d059ba58f8f3adc4f53f"
  end
```

将生成出来的`tar.gz`包 去掉第一个中横线, 并上传至阿里云OSS上


## 补充
计算sha256方法
```
shasum -a 256  builder--0.0.1.big_sur.bottle.tar.gz
```