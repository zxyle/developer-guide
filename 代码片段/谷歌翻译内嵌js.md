```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>网页嵌入谷歌翻译</title>
</head>
<body>

这是一个简单的小测试

<!-- 把button放在右下角，这个是可以随意修改的，你可以改成一个链接一个图片之类的 -->
<div id="google_translate_element" style="position:absolute;bottom:10px;right:10px;z-index:2000;opacity:0.7"></div>

<script>
    function googleTranslateElementInit() {
        var x = new google.translate.TranslateElement(
            {
                // pageLanguage: 'zh-CN',
                // 需要翻译的语言，比如你只需要翻译成越南和英语，这里就只写en,vi
                includedLanguages: 'en,zh-CN,hr,cs,da,nl,fr,de,el,iw,hu,ga,it,ja,ko,pt,ro,ru,sr,es,th,vi',
                layout: google.translate.TranslateElement.InlineLayout.SIMPLE,
                // 自动显示翻译横幅，就是翻译后顶部出现的那个
                autoDisplay: true,
                // 还有些其他参数，由于原插件不再维护，找不到详细api了，将就了，实在不行直接上dom操作
            },
            'google_translate_element' // 触发元素的id
        );
        console.log(x)
    }
</script>

<script src="https://translate.google.cn/translate_a/element.js?cb=googleTranslateElementInit"></script>
</body>
</html>
```

