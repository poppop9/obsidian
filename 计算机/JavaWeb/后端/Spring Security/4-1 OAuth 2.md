
>[!quote] 宏观流程
>
> ```mermaid
> sequenceDiagram
>     participant D as 第三方应用[例如某个网站]
>     participant S as 授权服务器[例如微信的授权服务器]
> 	participant Y as 用户
> 	participant Z as 资源服务器[例如微信的资源服务器]
> 
> 	D->>S: 给我Token
> 	S->>Y: 你要把权限给第三方用户吗
> 	Y->>S: 同意授权
> 	S->>D: 发放Token
> 	D->>Z: 携带Token进行访问
> 	Z->>D: 返回资源
> ```

# 概述
>[!hint] 使用场景
> - **开放系统间授权**
> 	- 社交登录【~~微信登录各种网页~~】
> 	- 开放 API【~~小白羊网盘获取阿里网盘的资源~~】
> - **现代微服务安全**
> - **企业内部应用认证授权**
> 	- 单点登录
> 	- 身份识别与访问管理

# 授权模式
>[!quote] 四种授权模式
>- **隐藏式**：适用于纯前端网站【浏览器-服务器】
>- **客户端凭证式**：安全，适用于纯后端网站【服务器-服务器】
>- **密码式**：最不安全，适用于公司内部高度信任的两个系统之间使用
>- **授权码式**：<u>最常用</u>，<u>最复杂</u>，<u>最安全</u>，适用于前后端分离网站

## 隐藏式
```mermaid
sequenceDiagram
	participant D as 第三方应用前端
	participant S as 授权服务器
	participant Y as 用户

	D->>S: 给我Token
	S->>Y: 要授权给第三方应用吗
	Y->>S: 同意授权
	S->>D: 返回Token
```

## 客户端凭证式
>[!quote] 凭证
>第三方应用的开发者需要到授权服务器上注册第三方应用，注册成功后会获得 <u>客户端 ID</u> 和 <u>客户端密钥</u>，这两个东西就是凭证。~~例如我要开发一个 A 应用，我需要到微信上注册这个应用，微信会给我凭证~~

```mermaid
sequenceDiagram
	participant F as 服务器端应用程序
	participant S as 授权服务器

	F->>S: 携带凭证，请求token
	S->>S: 验证凭证
	S->>S: 凭证正确
	S->>F: 返回token
```

## 密码式
```mermaid
sequenceDiagram
	participant Y as 用户
	participant D as 第三方应用
	participant S as 授权服务器

	Y->>D: 输入资源服务器的用户名，密码
	D->>S: 携带用户名和密码，请求Token
	S->>S: 校验用户名和密码
	S->>S: 正确
	S->>D: 返回Token
```

## 授权码式
```mermaid
sequenceDiagram
	participant D as 第三方应用
	participant S as 授权服务器
	participant Y as 用户

	D->>S: 携带凭证，重定向URI，请求Token
	S->>S: 跳转到授权页面
	S->>Y: 要授权给第三方应用吗
	Y->>S: 同意授权
	S->>D: 返回授权码
	D->>D: 跳转到指定的重定向URI上
	D->>S: 携带授权码，凭证，重定向URI，请求Token
	S->>S: 验证
	S->>S: 验证通过
	S->>D: 返回token
```

---

>[!quote] 刷新令牌
>第三方应用在获取访问令牌的同时，通常也会收到一个刷新令牌，当访问令牌即将过期时，第三方应用可以使用刷新令牌向授权服务器发起请求，以获取新的访问令牌，刷新令牌是一个长期有效的凭证，<u>用于第三方应用向授权服务器请求新的访问令牌</u>
>- 刷新令牌的使用过程中，用户不需要再次进行授权操作，第三方应用可以自动更新访问令牌

# 第三方登录
Spring Security OAuth2 中，默认整合了 Github，Google，Facebook，Okta 第三方登录功能

```xml
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-oauth2-client</artifactId>
</dependency>
```

## GitHub 登录
- 到开发者设置中的 OAuth 中创建应用 https://github.com/settings/developers
	- 回调地址默认是：`https://localhost:8080/login/oauth2/code/github`
- 获取到 Client ID `Ov23licA0Czh3DzVPvuw`
- 获取到 Client Secrets `b0cbc69b03e269f7961196b6c4b19aaaaa12c7ba`
- 配置 yml 配置文件
```yml
spring:
  security:
    oauth2:
      client:
        registration:	
          github:	
            client-id: ……
            client-secret: ……
```




