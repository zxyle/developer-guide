### 介绍



### 引入步骤

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```







### 基于权限链 权限判断

@EnableWebSecurity

hasAnyRole

http.formLogin()
.loginProcessingUrl("")
// 自定义登录页面
.loginPage()
// 登陆成功后跳转页面
.successForwardUrl()
// 登陆失败跳转页面
.failureForwardUrl()



用户名字段名

.usernameParameter("username123")

.passwordParameter("password123")



.authorizeRequests()

- .antMatchers("url1", "url2") 放行(ant表达式)

- regexMatchers("") 正则表达式地址

- mvcMatchers("")

- .anyRequest() 剩下请求需要认证



访问控制方法

- .authenticated() 需要认证
- .permitAll() 允许任何人
- .denyAll() 不允许任何
- .anoymous() 匿名访问
- .fullyAuthenticated()
- .remember() 记住我



权限判断

- .hasAuthority("admin")

- .hasAnyAuthority("", "")



角色判断

- hasRole("admin")
- hasAnyRole("", "")
- 或者使用ROLE_开头



IP地址判断

- hasIpAddress("127.0.0.1")



.access()



### access表达式





### 基于注解权限判断

使用前需要开启`@EnableGlobalMethodSecurity(prePostEnabled = true, securedEnabled = true)`

@PreAuthorize 方法级

@PostAuthorize 方法级 很少被用到

@Secured 判断是否有角色 使用ROLE_开头



其他注解

@DenyAll

@PermitAll

@RolesAllowed

### 自定义成功和失败处理器

实现 AuthenticationFailureHandler

实现 AuthenticationSuccessHandler



