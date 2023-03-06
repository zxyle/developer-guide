## 介绍

Spring Expression Language, 是一种强大的表达式语言， 更多参考https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#expressions



## 示例1

```java
ExpressionParser parser = new SpelExpressionParser();
Integer score = 4;
EvaluationContext context = new StandardEvaluationContext();
context.setVariable("score", score);

// 三元表达式
String expression = "#score >= 8 ? 10: (#score >= 6 ? 6: (#score >= 4 ? 4 : 0))";
Integer name = parser.parseExpression(expression).getValue(context, Integer.class);
System.out.println(name);
```



## 示例2

```java
List<String> options = new ArrayList<>();
options.add("A");
ExpressionParser parser = new SpelExpressionParser();
EvaluationContext context = new StandardEvaluationContext();
context.setVariable("options", options);
// 判断数组是否包含某个元素
String expression = "#options.contains('A')";
Boolean b1 = parser.parseExpression(expression).getValue(context, Boolean.class);
System.out.println("include : " + b1);
```



## 示例3

```java
SpelParserConfiguration config = new SpelParserConfiguration(SpelCompilerMode.IMMEDIATE,
                this.getClass().getClassLoader());
ExpressionParser parser = new SpelExpressionParser(config);
EvaluationContext context = new StandardEvaluationContext();
context.setVariable("score", 10);
String expression = "#score <= 2";
Boolean b1 = parser.parseExpression(expression).getValue(context, Boolean.class);
System.out.println(b1);
```

