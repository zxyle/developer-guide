
## 介绍


## 引入依赖
```xml
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-validation</artifactId>
</dependency>
```



## 编写异常处理

```java
// 参考builder里模板代码
```



## 使用方式

- 校验对象 （形参最前面加上@Valid注解）
- 校验url上的参数 （controller上加@Validated注解）





## JSR注解

| 注解                               | 适用对象                                                     | 作用                       | 举例                         |
| ---------------------------------- | ------------------------------------------------------------ | -------------------------- | ---------------------------- |
| @Null                              |                                                              | 验证对象是否为null         |                              |
| @NotNull                           |                                                              |                            |                              |
| @Pattern                           | 字符串                                                       | 是否符合正则表达式的规则   | @Pattern(regexp = "0[A\|B]") |
| @NotBlank                          |                                                              |                            |                              |
| @NotEmpty                          | 列表、                                                       |                            |                              |
| @Length                            | 检查字符串、集合、数组等对象的长度是否符合指定的约束条件。   |                            | @Length(min = 1, max = 100） |
| @AssertTrue                        |                                                              | 是否为 true                |                              |
| @AssertFalse                       |                                                              | 是否为 false               |                              |
| @Max                               |                                                              | 是否小等于指定的值         |                              |
| @Min                               |                                                              | 是否大等于指定的值         |                              |
| @DecimalMin                        |                                                              |                            |                              |
| @DecimalMax                        | 检查数字是否小于或等于指定的最大值                           |                            |                              |
| @Size(min=1, max=10)               | list map array string                                        | 长度是否在给定的范围之内   |                              |
| @Digits(integer = 3, fraction = 2) |                                                              | 整数和小数位数             |                              |
| @Email                             |                                                              | 是否是邮件地址             |                              |
| @Range(min = X, max = Y)           | int`、`long`、`double、Integer、Long、Double、BigDecimal、BigInteger |                            |                              |
| @Positive                          | 同上                                                         | 必须为正数                 |                              |
| @Negative                          | 同上                                                         | 必须为负数                 |                              |
| @NegativeOrZero                    | 同上                                                         | 必须为负数或0              |                              |
| @PositiveOrZero                    | 同上                                                         | 必须为正数或0              |                              |
| @Past                              | LocalDateTime、LocalDate                                     | 是否在当前时间之前         |                              |
| @Future                            | 同上                                                         | 是否在当前时间之后         |                              |
| @PastOrPresent                     | 同上                                                         | 当前时间之前或当前时间     |                              |
| @FutureOrPresent                   | 同上                                                         | 当前时间之后或当前时间     |                              |
| @Valid                             |                                                              | javax下 用来标注对象       |                              |
| @Validated                         |                                                              | spring下用来标注Controller |                              |



## Hibernate 注解

- @ScriptAssert
- @URL



## 自定义注解

- 中国身份证
- 统一社会信用代码
- 邮编
- 手机号



## 手动参数校验

```java
ValidatorFactory factory = Validation.buildDefaultValidatorFactory();
Validator validator = factory.getValidator();
Person person = new Person();
person.setSex("Man22");
person.setClassId("82938390");
person.setEmail("SnailClimb");
person.setId("330824199512042426");
Set<ConstraintViolation<Person>> violations = validator.validate(person);
//output:
//email 格式不正确
//name 不能为空
//sex 值不在可选范围
for (ConstraintViolation<Person> constraintViolation : violations) {
    System.out.println(constraintViolation.getMessage());
}
```



## 添加异常处理

```java
// 处理JSON方式 数据校验失败
@ExceptionHandler(MethodArgumentNotValidException.class)
public ResponseEntity<Map<String, String>> handleValidationExceptions(MethodArgumentNotValidException ex) {
	Map<String, String> errors = new HashMap<>();
	ex.getBindingResult().getAllErrors().forEach((error) -> {
		String fieldName = ((FieldError) error).getField();
		String errorMessage = error.getDefaultMessage();
		errors.put(fieldName, errorMessage);
	});
	return ResponseEntity.status(HttpStatus.BAD_REQUEST).body(errors);
}

// 处理表单方式 数据校验失败
@ExceptionHandler(ConstraintViolationException.class)
ResponseEntity<String> handleConstraintViolationException(ConstraintViolationException e) {
	return ResponseEntity.status(HttpStatus.BAD_REQUEST).body(e.getMessage());
}
```



## 参考文档

- [JSR-303 (1.0版本)](https://jcp.org/en/jsr/detail?id=303)
- [JSR-349 (1.1版本)](https://jcp.org/en/jsr/detail?id=349)
- [JSR-380 (2.0版本)](https://jcp.org/en/jsr/detail?id=380)
- [中国数据校验](https://github.com/zxyle/china-data-validator)