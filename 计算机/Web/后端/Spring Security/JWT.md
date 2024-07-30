# JWT

### JWT 令牌

> JWT 令牌【Json Web Token】就是用户标识，对 Json 格式进行了 `Base 64 编码` + 签名算法

* 优点
  * 支持多端【令牌可以存储在除 Cookie 以外的其他存储空间中】
  * 支持服务端集群部署
  * 减轻了服务端存储压力【无需在服务端存储数据】
* 缺点
  * 需要自己实现
  * 需要和前端配合

#### 组成

!\[\[Excalidraw/计算机/JavaWeb Draw.md#^group=MNBxap8H|870]]

#### 实现流程

* 在用户登录成功之后，在服务端生成 JWT 令牌
* 将令牌下发给客户端
* 客户端把令牌存储起来
* 客户端在之后的每一次请求时携带该令牌
* 服务端接收请求之后进行统一拦截，获取到请求中携带的令牌，并校验令牌的真伪
  * 无效，响应错误结果
  * 有效，允许访问对应的业务接口

#### 准备工作

* 引入依赖

```xml
<dependency>  
    <groupId>io.jsonwebtoken</groupId>  
    <artifactId>jjwt</artifactId>  
    <version>0.9.1</version>  
</dependency>
```

#### 具体实现

!\[\[Excalidraw/计算机/JavaWeb Draw.md#^group=t8jOJfVI|790]]

```java
package com.example.utils;

public class CreateJWT {
    public String CreateJWT(Map<String, Object> claims) {
        //链式编程
        String jwt = Jwts.builder()
                .signWith(SignatureAlgorithm.HS256, "greenteck")  //设置签名算法，密钥
                .setClaims(claims)  //设置自定义内容【这里用map集合表示json】
                .setExpiration(new Date(System.currentTimeMillis() + 3600 * 1000))  //设置令牌的有效期
                .compact();  //最后返回令牌

        return jwt;
    }

    public void AnalysisJWT() {
        Claims claims = Jwts.parser()   //调用解析器
                .setSigningKey("greenteck")   //传入密钥
                .parseClaimsJws("eyJhbGciOiJIUzI1NiJ9.eyJraW4iOiJib29nYWxvbyIsImpheWdlZSI6InNjYXJlY3JvdyIsImV4cCI6MTcwMTM5Njc4NH0.Oiv7vVbwJkwEO0sa-4V0sRqgHkWP1sJpXlXppFblRO8")  //声明令牌
                .getBody();  //获取第二部分

        System.out.println(claims);
    }
}
```

```java
package com.example.controller;

@RestController
public class ManagerLoginController {
    @Autowired
    private ManagerLoginService mls;

    @PostMapping("/login")
    public Result login(@RequestBody manager manager) {
        manager m = mls.ManagerLogin(manager);
        System.out.println(m);

        if (m != null) {  //下发令牌
            Map<String, Object> claims = new HashMap<>();
            claims.put("id",m.getId());
            claims.put("account",m.getAccount());
            claims.put("password",m.getPassword());

            CreateJWT createJWT = new CreateJWT();
            String jwt = createJWT.CreateJWT(claims);
            return Result.buildResult(Result.Status.OK, jwt);
        } else {
            return Result.buildResult(Result.Status.PWD_ERROR);
        }
    }
}

---
manager(id=1, account=123, password=abc)
```

```java
package com.example.service;

@Service
public interface ManagerLoginService {
    //根据账号，密码查询用户
    manager ManagerLogin(manager manager);
}
```

```java
package com.example.service.impl;

@Service
public class ManagerLoginService implements com.example.service.ManagerLoginService {
    @Autowired
    private ManagerLoginMapper mlm;

    @Override
    public manager ManagerLogin(manager manager) {
        return mlm.SelectManager(manager);
    }
}
```

```java
package com.example.mapper;

@Mapper
public interface ManagerLoginMapper {
    @Select("SELECT * FROM manager WHERE account=#{account} AND password =#{password}")
    manager SelectManager(manager manager);
}
```

指定的密钥 greenteck 存储在 jwt 的哪个部分

> \[!hint] 当 _**篡改令牌**_ 或 _**令牌过期**_ 解析令牌时就会报错

### 统一拦截

> \[!hint] 目前主流使用 Interceptor

#### 过滤器 Filter

> Filter 是 JavaWeb 的三大组件【Servlet，Filter，Listener】之一，可以把对资源的请求拦截下来，从而_**完成一些通用的操作**_【登录校验，统一编码处理，敏感字符处理……】

**执行流程**

!\[\[Excalidraw/计算机/JavaWeb Draw.md#^group=D\_tAwfzgeAtpLUlBUPLDq|790]] !\[\[Excalidraw/计算机/JavaWeb Draw.md#^group=jcttnSam7dZdpCHQLsr6b|640]]

#### 拦截器 Interceptor

> Spring 框架中提供的用来动态拦截 Controller 方法的执行

!\[\[Excalidraw/计算机/JavaWeb Draw.md#^group=OSBwvT3c5koJtOdxWudzQ|700]]

!\[\[Excalidraw/计算机/JavaWeb Draw.md#^group=gri50A3q|690]]

```xml
<!--阿里巴巴的fastJson--> 
<dependency>  
    <groupId>com.alibaba</groupId>  
    <artifactId>fastjson</artifactId>  
    <version>1.2.75</version>  
</dependency>
```

```java
//拦截器类
package com.example.interceptor;

import org.springframework.util.StringUtils;

@Component  //交给IOC容器
public class LoginCheckInterceptor implements HandlerInterceptor {  //实现HandlerInterceptor接口
    //在Controller方法之前运行【返回true则放行，false则不放行】
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        //获取请求的url
        String url = request.getRequestURL().toString();

        //获取请求头中的令牌
        String jwt = request.getHeader("token");

        //令牌不存在
        if (StringUtils.hasLength(jwt) == false) {
            //手动利用request对象响应错误信息【因为不是Controller，不能自动将Result响应对象转换为json】
            String NoLogin = JSONObject.toJSONString(Result.buildResult(Result.Status.UNAUTHORIZED));
            response.getWriter().write(NoLogin);
            //不放行
            return false;
        }

        //只要解析令牌报错就说明令牌出错了
        JWTUtils jwtUtils = new JWTUtils();
        try {
            jwtUtils.AnalysisJWT(jwt);
        } catch (Exception e) {
	        //将Result对象转换为Json格式
            String NoLogin = JSONObject.toJSONString(Result.buildResult(Result.Status.UNAUTHORIZED));
            response.getWriter().write(NoLogin);
            return false;
        }

        //放行
        return true;
    }

    //在Controller类运行完之后运行
    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
		……
    }

	//视图渲染完毕后运行
    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
		……
    }
}
```

```java
//拦截器的配置类
package com.example.config;

@Configuration  //表示是一个配置类
public class WebConfig implements WebMvcConfigurer {  //实现WebMvcConfigurer接口
    @Autowired
    private LoginCheckInterceptor loginCheckInterceptor;

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(loginCheckInterceptor)  //添加要配置的Interceptor类
                .addPathPatterns("/**")  //拦截所有请求
                .excludePathPatterns("/login");  //不拦截对/login的
    }
}
```

```java
//令牌的工具类
package com.example.utils;

public class JWTUtils {
    public String CreateJWT(Map<String, Object> claims) {
        //链式编程
        String jwt = Jwts.builder()
                .signWith(SignatureAlgorithm.HS256, "greenteck")  //设置签名算法，密钥
                .setClaims(claims)  //设置自定义内容【这里用map集合表示json】
                .setExpiration(new Date(System.currentTimeMillis() + 3600 * 1000))  //设置令牌的有效期
                .compact();  //最后返回令牌

        return jwt;
    }

    public void AnalysisJWT(String jwt) {
        Claims claims = Jwts.parser()   //调用解析器
                .setSigningKey("greenteck")   //传入密钥
                .parseClaimsJws(jwt)  //声明令牌
                .getBody();  //获取第二部分
    }
}
```

> \[!hint] Interceptor 中的路径参数 `/*` 表示所有的一级路径，_**不包括**_ `/user/1` `/**` 表示所有的路径 `/user/*` 表示 `/user` 下的所有一级路径，不包括 `/user/s/1` `/user/**` 表示 `/user` 下的所有路径
