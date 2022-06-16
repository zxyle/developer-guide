### 介绍

java中用来处理html的库

https://github.com/jhy/jsoup

https://jsoup.org/



### 引入

```xml
<dependency>
  <groupId>org.jsoup</groupId>
  <artifactId>jsoup</artifactId>
  <version>1.15.1</version>
</dependency>
```



### 网络请求

```java
import org.jsoup.Connection;
import org.jsoup.helper.HttpConnection;

// .connect
// .ignoreContentType
// .execute
// .get
// .post
// .header
// .headers()
// .timeout()
// .userAgent()
// .data()

String url = "https://httpbin.org/ip";
Connection.Response response = HttpConnection.connect(url).ignoreContentType(true).execute();
System.out.println(response.contentType());
System.out.println(response.body());
```





### 网页解析

```java
import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

// 发起网络请求，将网页转换成Document对象
Document doc = Jsoup.connect(url).headers(headers).get();

// css选择器 （此例为类选择器）
Elements elements = doc.select(".well-sm");

// 获取html标签属性
element.attr("id");

// 获取html标签文本
element.text();
```



### 更多示例

```css
// id选择器
#mp-itn

// 层级
ul > li

// 带class="author"的td标签
td.author > cite
```



| 选择器              | 实例              | 选取                                    |
| ------------------- | ----------------- | --------------------------------------- |
| *                   | *                 | 所有元素                                |
| #id                 | #lastname         | id="lastname"的元素                     |
| .class              | .intro            | 所有class="intro"的元素                 |
| element             | p                 | 所有<p>元素                             |
| .class.class        | .intro.demo       | 所有class="intro"且class="demo"的元素   |
| :first              | p:first           | 第一个<p>元素                           |
| :last               | p:last            | 最后一个<p>元素                         |
| :even               | tr:even           | 所有偶数<tr>元素                        |
| :odd                | tr:odd            | 所有奇数<tr>元素                        |
| :eq(index)          | ul li:eq(3)       | 列表中的第4个元素（index从0开始）       |
| :gt(no)             | ul li:gt(3)       | 列出index大于3的元素                    |
| :lt(no)             | ul li:lt(3)       | 列出index小于3的元素                    |
| :not(selector)      | input:not(:empty) | 所有不为空的input元素                   |
| :header             | :header           | 所有标题元素<h1> - <h6>                 |
| :animated           |                   | 所有动画元素                            |
| :contains(text)     | :contains("W3C")  | 包含指定字符串的所有元素                |
| :empty              | empty             | 无子（元素）节点的所有元素              |
| :hidden             | :hidden           | 所有隐藏的<p>元素                       |
| :visible            | table:visible     | 所有可见的表格                          |
| s1,52,53            | th,td,.intro      | 所有带有匹配选择的元素                  |
| [attribute ]        | [href]            | 所有带有href 属性的元素                 |
| [attribute =value]  | [href=#"]         | 所有href 属性的值等于"#"的元素          |
| [attribute !=value] | [href!='#]        | 所有href 属性的值不等于"#"的元素        |
| [attribute $=value] | [href$='jpg'      | 所有href 属性的值包含以"jpg" 结尾的元素 |
| :input              | :input            | 所有 <input>元素                        |
| :text               | :text             | 所有 type="text" 的<input>元素          |
| :password           | :password         | 所有type="password" 的<input>元素       |
| :radio              | :radio            | 所有 type="radio" 的<input>元素         |
| :checkbox           | :checkbox         | 所有 type="'checkbox" 的<input>元素     |
| :submit             | :submit           | 所有type="submit" 的<input>元素         |
| :reset              | :reset            | 所有 type="reset” 的 <input>元素        |
| :button             | :button           | 所有 type="button" 的<input> 元素       |
| :image              | :image            | 所有 type="image" 的 <input>元素        |
| :file               | :file             | 所有 type="file" 的<input>元素          |
| :enabled            | :enabled          | 所有激活的 input 元素                   |
| :disabled           | :disabled         | 所有禁用的 input 元素                   |
| :selected           | :selected         | 所有被选取的input元素                   |
| :checked            | :checked          | 所有被选中的input元素                   |




### 参考文献

- http://t.zoukankan.com/onblog-p-13036308.html
- https://api.jquery.com/category/selectors/
- https://www.runoob.com/jquery/jquery-selectors.html