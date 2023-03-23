## 介绍



## 使用

### 1. 导入依赖

```xml
<dependency>
  <groupId>org.freemarker</groupId>
  <artifactId>freemarker</artifactId>
  <version>2.3.31</version>
</dependency>
```



### 2. 编写模板

```
Hello ${name}
```



### 3. 渲染模板

```java
import freemarker.template.Configuration;
import freemarker.template.Template;


// 创建freeMarker配置实例
Configuration configuration = new Configuration(Configuration.VERSION_2_3_28);
configuration.setDefaultEncoding("UTF-8");
configuration.setDirectoryForTemplateLoading(new File(TEMPLATE_PATH));

String templateName = "xxx";
String outFile = "";
Map<String, Object> data = new HashMap<>();
data.put("name", "Jack");
Template template = configuration.getTemplate(templateName);

try (Writer out = new BufferedWriter(new OutputStreamWriter(Files.newOutputStream(outFile.toPath())))) {
  template.process(data, out);
} catch (Exception ignored) {
}
```



