## 介绍



## 引入依赖

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-aop</artifactId>
</dependency>
```



## 创建切面类

```java
@Aspect    // 定义切面
@Component
public class LogAspect {
}
```



## 创建切入点

```java
@Pointcut("execution(* cn.tongdun.gec.securityapi.biz.auth.controller.LoginController.login(..))")
// 定义切入点表达式
public void log() {
}
```



## 使用

```java
// 前置方法
@Before("log()")    // 引用切入点
public void doBefore(JoinPoint joinPoint) {
}

// 后置方法
@After("log()")
public void doAfter() {
  logger.info("------------doAfter------------");
}

// 返回后通知
@AfterReturning(returning = "result", pointcut = "log()")
public void doAfterReturn(Object result) {

  // 打印返回值
  logger.info("AfterReturning Result: {}", result);
}

// 环绕通知
@Around("log()")
public Object Around(ProceedingJoinPoint pjp) throws Throwable {
  Object result = pjp.proceed();
  return result;
}

// 异常后通知
@AfterThrowing(throwing = "e", pointcut = "log()")
public void doAfterThrowing(Throwable e) {
  logger.error("------------doAfterThrowing------------");
  logger.error("Exception: {}", e.getMessage());
}
```

