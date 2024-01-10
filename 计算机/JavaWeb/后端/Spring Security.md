# 🌕准备工作
- 引入依赖
```xml
<!--SpringSecurity-->  
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-security</artifactId>  
</dependency>
```


# 🌕过程
## 🌗登录
- 自定义登录Controller接口
	- 调用 ProviderManager 方法进行认证
		- 如果认证通过，生成JWT令牌
		- 再把用户信息存入redis
- 自定义 `UserDetailsService`，在这个类中去查询数据库
## 🌗校验
- 定义JWT认证过滤器
	- 获取token
	- 解析token获取UserId
	- 从redis中获取用户信息
	- 把用户信息存入 `SecurityContextHolder`【为了JWT认证过滤器后续的过滤器可以使用用户信息做某些事情】




























