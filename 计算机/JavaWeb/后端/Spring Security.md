```xml
<!--由于是starter版本，所以不用指定版本号-->  
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-security</artifactId>  
</dependency>
```

# 流程
>[!quote] 宏观流程
>
> ```mermaid
> sequenceDiagram
>     participant 客户端
>     participant 服务器
> 
> 	客户端->>服务器: 携带用户名，密码访问登录接口
> 	服务器->>服务器: 与数据库对比，如果正确，则生成一个jwt令牌
> 	服务器->>客户端: 响应jwt给客户端
> 	客户端->>服务器: 请求时携带token
> 	服务器->>服务器: 解析token，获取id
> 	服务器->>服务器: 根据id获取用户的权限信息
> 	服务器->>客户端: 响应资源给客户端
> ```

>[!quote] 微观流程
> - `UsernamePasswordAuthenticationFilter` 判断用户名和密码是否正确
> - `ExceptionTranslationFilter` 处理在认证授权时的所有异常
> - `FilterSecurityInterceptor` 当登录成功后，判断用户是谁，有没有权限
> 
> ```mermaid
> graph LR
> 	subgraph 过滤器链
> 	    A(请求) -->|...| B(UsernamePasswordAuthenticationFilter)
> 	    B -->|...| C(ExceptionTranslationFilter)
> 	    C --> D(FilterSecurityInterceptor)
> 	    D --> E(API)
>     end
> ```

---

>[!quote] Spring Security 默认的流程
> ```mermaid
> sequenceDiagram
>     participant 请求
>     participant U AS UsernamePasswordAuthenticationFilter
>     participant P AS ProviderManager
> 	participant D AS DaoAuthenticationProvider
> 	participant I AS InMemoryUserDetailsManager
> 
> 	Note over U: AbstractAuthenticationProcessingFilter接口
> 	Note over P: AuthenticationManager接口
> 	Note over D: AbstractUserDetailsAuthenticationProvider接口
> 	Note over I: UserDetailsService接口
> 
> 	请求->>U: 提交用户名和密码
> 	U->>U: 封装Authentication对象，这时候还没有权限
> 	U->>P: 调用authenticate方法进行认证
> 	P->>D: 调用DaoAuthenticationProvider的Authenticate方法进行认证
> 	D->>I: 调用LoadUserByUsername方法查询用户
> 	I->>I: 根据用户名去查询对应的用户，及这个用户对应的权限信息【在内存中查找】
> 	I->>I: 把对应的用户信息包括去权限信息封装成UserDetails对象
> 	I->>D: 返回UserDetails对象
> 	D->>D: 通过PasswordEncoder，对比UserDetails中的密码和Authentication的密码
> 	D->>D: 如果正确就把UserDetails中的权限信息设置到Authentication对象中
> 	D->>U: 返回Authentication对象
> 	U->>U: 如果上一步返回了Authentication对象，就使用SecurityContextHolder．getContext().setAuthentication方法存储该对象
> ```

>[!warning] 目前的 Spring Security 的流程是不符合我们的开发要求的，我们要进行修改，要替换不符合要求的实现类

# 登录
```mermaid
sequenceDiagram
    participant 客户端
    participant C AS 自定义Controller登录接口
    participant P AS ProviderManager
    participant D AS DaoAuthenticationProvider
    participant U AS 自定义UserDetailsService
    participant 数据库

	客户端->>C: 提交用户名和密码
	C->>P: 
	P->>D: 
	D->>U: 
	U->>数据库: 
	数据库->>U: 
	Note over U: 封装自定义的UserDetails对象
	U->>D: 返回UserDetails对象
	D->>P: 
    P->>C: 
    Note over C: 认证通过，生成jwt
    Note over C: 并存入信息到redis，方便后续校验
    C->>客户端: 返回 jwt
```

---

- 自定义 UserDetailsService 的实现类
```java
package com.example.spring_security.domain.service.impl.UserDetailsServiceImpl;

@Service
public class UserDetailsServiceImpl implements UserDetailsService {
    @Autowired
    private UserMapper userMapper;

    @Override
    public UserDetails loadUserByUsername(String username) throws UsernameNotFoundException {
        // 查询用户信息
        user user = userMapper.selectByUserName(username);
        if (user == null) {
            throw new UsernameNotFoundException("用户不存在");
        }

        // todo 查询用户对应的权限信息

        // 把用户信息封装成UserDetails对象
        return new LoginUser(user);
    }
}
```

- 自定义 UserDetails 的实现类
```java
@Data  
@NoArgsConstructor  
@AllArgsConstructor
public class LoginUser implements UserDetails {
	private user user;
	
    // 这个方法返回一个权限集合，表示用户具有的角色。Spring Security中的角色通常以ROLE_开头
    @Override
    public Collection<? extends GrantedAuthority> getAuthorities() {
        return null;
    }

    // 返回用户的密码
	@Override  
	public String getPassword() { return user.getUserPassword(); }  
	  
	// 返回用户的用户名  
	@Override  
	public String getUsername() { return user.getUserName(); }

	// 账户是否过期，如果返回false，那么账号就是过期的
    @Override
    public boolean isAccountNonExpired() { return true; }

    // 账户是否锁定，如果返回false，那么账号就是被锁定的
    @Override
    public boolean isAccountNonLocked() { return true; }

    // 凭证是否过期，如果返回false，那么凭证就是过期的
    @Override
    public boolean isCredentialsNonExpired() { return true; }

    // 账户是否可用，如果返回false，那么账号就是不可用的
    @Override
    public boolean isEnabled() { return true; }
}
```

- 自定义 BCryptPasswordEncoder 注入到 IOC 容器中，替换默认的 


# 校验
>[!quote] 校验
>校验 是当用户请求一个受保护的资源时，会检查用户是否已登录，以及用户是否具有访问该资源的权限

```mermaid
sequenceDiagram
	participant K AS 客户端
	participant J AS jwt认证过滤器
	participant R AS redis
	participant S AS SecurityContextHolder

	K->>J: 携带token发起请求
	J->>J: 获取，解析token，获取到userId
	J->>R: 携带userId
	R->>J: 返回用户信息
	J->>S: 把用户信息存入到SecurityContextHolder，便于后续的过滤器可以使用用户信息做某些事情
```






























