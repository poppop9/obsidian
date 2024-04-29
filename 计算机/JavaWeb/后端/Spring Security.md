```xml
<!--SpringSecurity-->  
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-security</artifactId>  
</dependency>
```

# 流程
```mermaid

```

- 宏观流程
![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402271600507.png)
- 微观流程
	- `UsernamePasswordAuthenticationFilter` 判断用户名和密码是否正确
	- `ExceptionTranslationFilter` 处理在认证授权时的所有异常
	- `FilterSecurityInterceptor` 当登录成功后，判断用户是谁，有没有权限

```mermaid
graph LR
	subgraph 过滤器链
	    A(请求) -->|...| B(UsernamePasswordAuthenticationFilter)
	    B -->|...| C(ExceptionTranslationFilter)
	    C --> D(FilterSecurityInterceptor)
	    D --> E(API)
    end
```
## UsernamePasswordAuthenticationFilter
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402281105597.png)

>[!warning] 目前的 Spring Security 的流程是不符合我们的开发要求的，我们要进行修改，要替换不符合要求的实现类

## 登录
- 自定义登录 Controller 接口
	- 调用 ProviderManager 方法进行认证
		- 如果认证通过，生成 JWT 令牌
		- 再把用户信息存入 redis
- 自定义 `UserDetailsService`，在这个类中去查询数据库

## 校验
- 定义 JWT 认证过滤器
	- 获取 token
	- 解析 token 获取 UserId
	- 从 redis 中获取用户信息
	- 把用户信息存入 `SecurityContextHolder`【为了 <u>JWT 认证过滤器</u>后续的过滤器可以使用用户信息做某些事情】




























