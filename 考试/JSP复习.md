第一章
第二章。不管
三，注释生命，指令，动作
四，
五，会话管理的过程，session 会话周期，cookie，如何判断会话的周期，会话对象，cook
六，javabean的生命周期
七，不管
八，增删改查，如何指定数据源
九，不管
十，servlet，1，3，生命周期
十一，
十二，
十三，不管


# 概述
Web访问可以简单划分为两个过程：客户端请求和服务端响应

超文本传输协议HTTP：
- 无状态的协议
- 允许传输任意类型的数据
- 每次连接只处理一次请求，处理完当次请求就断开连接

---
- ***静态网页***
	- 不灵活，维护成本较高。展示的内容一般固定不变
- ***动态网页***
	- 内容大部分是来自于数据库中的数据。目前流行的动态技术有ASP、PHP、JSP
		- ASP：实际上是1个中间件，将Web上的请求转入到IIS解释器中，IIS将ASP的Script脚本全部解析执行
			- 容易上手且开发效率较高
			- 不能跨平台，只能在Windows平台下
		- PHP：是一种HTML内嵌式的语言
			- 优点是开源、跨平台
			- 安装复杂
		- JSP：采用Java语言作为服务器端脚本，页面由HTML和嵌入Java代码组成。
			- 简单易用，完全面向对象
			- 具有Java的平台无关性和安全可靠性
			- 高效率和高性能

---
Web服务器比较流行的有WebSphere、WebLogic、Tomcat等

---
JSP的执行顺序：
1. 客户端向Web服务器提出请求
2. JSP引擎负载将页面转化为Servlet
3. 经过虚拟机编译生成类文件
4. 再把类文件加载到内存中执行
5. 服务器将处理结果返回给客户端

![700](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240107112003.png)

---
## 企业应用开发架构
- 两层架构
	- 开发简单、部署方便；维护困难、执行效率低、用户容量少
- 三层架构
	- 方便维护，提高执行效率，加大了部署困难的程度
- N层架构
	- 维护方便，进一步加大了部署的困难程度
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240107131928.png)
## C/S，B/S
C/S为客户机服务器架构【***早期***】：
- 用于有固定用户端/少量用户端
- 用于安全性较高的应用【==银行，飞机票售票==】
- 开发成本较高
- 客户端程序设计复杂，跨平台性不强
- 维护困难

B/S为浏览器服务器架构：
- B/S架构的数据提交一般以页面为单位，数据动态交互性不强，不利于在线事务处理应用
# JSP基本语法
- JSP注释
```java
HTML的注释：
   <!--  注释的内容 -->
JSP的注释：
   <%-- 注释的内容 --%>

java注解与JSP注解的混用
<%
	//  这是脚本中的Java注释
	/*
		这也是脚本中的Java注释
	*/
%>
```
- JSP声明：声明部分的变量和方法只在当前的页面中有效
```java
<%! 变量定义/方法定义/类 %>

<%!
	int x,y,z=60;	
	String name="John";
	Date date = new Date();
%>
```
- JSP表达式
```java
<%=变量或者表达式%>

<%=new Date()%>
```

## JSP指令
- Page指令：设置JSP页面的属性和相关功能
	- 在所有的属性中除import可以声明多个外，其他属性都只能出现一次。
	```java
	<%@ page attribute1=”value1” […attribute2=”value n”]%>
	
	<%@ page language="java" import="java.util.*" pageEncoding="UTF-8"%>
	//language是必须设置的
	//import用来声明需要导入的包
	//pageEncoding属性用于设置页面的编码
	```
- Include指令：插入静态的文件内容
	```java
	<%@include file=”URL”%>
	
	<%@include file="copyRight.jsp" %>
	```
- Taglib指令：自定义新的标签在页面中执行
	```java
	//uri属性用来表示自定义标签库的存放位置
	//prefix属性是为了区分不同标签库的标签名
	<%@taglib  uri=”tagliburl” prefix=”tagPre” %>
	
	<%@ taglib uri="http://java.sun.com/jstl/core_rt" prefix="c"%>
	```
## JSP动作
- <jsp:include>动作
	```java
	//引入文件到目标页面
	<jsp:include page=”relative URL” flush=”true”/>
	
	<jsp:include page=”top.html” flush=”true”/>
	```
- <jsp:forward>动作
	- 相对于请求而言，所看到的响应是原先请求的页面给出的，请求者并不会获得转发的页面地址，因此具有隐蔽性
	```java
	//转发请求到另外一个页面中，在请求过程中会连同请求的参数数据一起被转发到目标页面中
	<jsp:forward page=”relative URL”>
	
	<jsp:forward page=”/error.jsp”/>
	```
- <jsp:param>动作
	```java
	//传递参数信息，它经常与其他动作一起使用，例如<jsp:include>和<jsp:forward>，用于传递主页面的参数到目标页面
	<jsp:param name=”参数名称” value=” 参数值”>
	
	<jsp:param name=”username” value=”李四”>
	```

```java
//知识拓展

<%%>脚本片段，如<%System.out.println("HelloWorld");%>
<%!%>声明，如<%! int num = 1;%>
<%=%>jsp表达式，如<%=session.getAttribute("name")%>
<%@%>指令，<%@ page language="java" %>
<%-- --%>隐式注释，则在浏览器源代码中看不到
<!-- --> 显式注释，则在浏览器源代码中看得到
```
# JSP内置对象
>JSP内置对象可以直接在JSP页面中使用，而不需要提前声明

response
session
application
out
page
config

## request对象
用户访问页面，会产生HTTP请求【包含了请求所需的参数值或信息】。可以通过request来获取客户端和服务端的信息【如IP地址、传递的参数名和参数值、应用系统名称、服务器主机名称等】

| **request对象常用方法**    | **方法说明**                                                    |
|:--------------------:|:-----------------------------------------------------------:|
| getParameter()       | 取得请求中指定的参数值,返回String类型                                      |
| getParameterValues() | 将同名称的参数一次性地读入String类型的数组中                                   |
| getParameterNames()  | 获取参数名称,返回枚举类型                                               |
| getMethod()          | 获取客户提交信息的方式,即post或get                                       |
| getServletPath()     | 获取JSP页面文件的目录                                                |
| getHeader()          | 获取HTTP头文件中的指定值,如accept、user-agent、content-type、content-type |
| getRemoteAddr()      | 获取客户端的IP地址                                                  |
| getServerName()      | 获取服务器的名称                                                    |
| getServerPort()      | 获取服务器的端口                                                    |
| getContextPath()     | 获取项目名称,如项目为根目录,则得到空的字符串                                     |
| getHeaders()         | 获取表头信息,返回枚举类型                                               |
### 具体作用
```java
//直接获取网页请求参数
http://localhost:8080/{工程目录地址}/getParameter.jsp?name=John&city=Beijing

页面地址后使用“？”连接请求参数；参数由“=”相连；一个请求携带多个参数时用“&”连接
```

```java
//表单提交获取网页请求参数
表单form中
    action指明表单提交后的数据跳转到指定页面并处理参数
    method有get和post两个值，出于安全考虑，一般选择post提交
```

表单提交获取网页请求参数时中文乱码处理：
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240108004714.png)

## response对象
用户访问一个页面时，会产生一个HTTP请求，服务器做出响应时调用的是response响应包

| addHeader (String name, String value) | 向页面中添加头和对应的值 |
| :--: | :--: |
| addCookie (Cookie cookie) | 添加Cookie信息 |
| sendRedirect (String uri) | 实现页面重定向 |
| setStatus (int code) | 设定页面的响应状态代码 |
| setContentType (String type) | 设定页面的MIME类型和字符集 |
| setCharacterEncoding (String charset) | 设定页面响应的编码类型 |
| setHeader (String name, String value) |  |
```jsp
response.sendRedirect ("index.jsp")
```

头meta信息是指在HTML页面中存在与\</head\>\</head\>之间的信息

## session对象
>session对象可以用来判断是否为同一用户【HTTP协议是一种无状态的协议】，还可以用来记录客户的连接信息等

会话：从用户打开浏览器连接到一个Web应用或者某个界面，直至关闭浏览器这个过程称为一个会话。其实打开一个浏览器就意味着打开了一个会话对象

==session对象生命周期==：从用户访问某个页面到关闭浏览器这段时间称为session对象的生命周期【也就是从会话开始到结束这段时间】

session对象与Cookie对象：session对象与Cookie对象是一一对应关系。JSP引擎会将创建好的session对象存放在对应的Cookie中

Cookie对象：将只需在客户端处理的数据存放在本地计算机上，不需要通过网络传输，提高处理效率，如记住密码

| sessioin对象常用方法 | 方法说明 |
| :--: | :--: |
| void setAttribute (String name, Object value) | 将参数名和参数值存放在session对象中 |
| Object getAttribute (String name) | 返回session中与指定参数绑定的对象,不存在则返回null |
| Enumeration GetAttributeName () | 一个用户一个线程,从而保证多个用户单击同一个页面时，session对象唯一性 |
| String getIld() | 获取session对象的ID值 |
| void removeAtrribute (String name) | 移除session中指定名称的参数 |
| long getCreationTime() | 获取对象创建的时间,返回结果是long型的毫秒数 |
| int getMaxInactiveInterval() | 获取session对象的有效时间 |
| void setMaxInactiveInterval() | 设置session对象的有效时间 |
| boolean isNew() | 用于判断是否为一个新的客户端 |
| void invalidate()  | 使session对象不合法,即失效 |

```java
// 获取session id值
String sessionID = session.getId();
session.setAttribute("name","John");
String author ＝ （String）session.getAttribute（＂author＂）；／／强制转为String类型 long time = session.getCreationTime();
Date date = new Date(time); 

```

## application对象
>application对象实现接口为javax.servlet.ServletContext，它的生命周期是从application对象创建到应用服务器关闭，可以视application对象为Web应用的全局变量

| application常用方法 | 方法说明 |
| :--: | :--: |
| getAttribute (String name) | 获得存放在application中的含有关键字为name的对象 |
| setAttribute (String name, 0bject obj)  | 将关键字name的指定对象ob j放进appl ication对象中 |
| Enumeration getAttributeNames () | 获取application中所有参数的名字,返回值是枚举类型 |
| removeAttribute (String name)  | 移除application对象中name指定的参数值 |
| getServletInfo() | 获取Servlet的当前版本信息 |
| getContext (String uripath)  | 获取uripath指定路径的context内容 |
| getRealPath (String path) | 获取指定文件的实际路径 |
| getMimeType (String file)  | 获取指定的文件格式 |
```java
// 网站计数器【刷新一次表示登录一次】
Integer count = (Integer) application.getAttribute("count");
if (count == null) {
    count = 1;
} else {
    count++;
}

application.setAttribute("count", count);
```

## out对象
out对象是继承javax.servlet.jsp.JspWriter类的一个输出流对象。包含很多IO流中的方法和特性，常用的方法就是输出内容到HTML中

| out常用方法 | 方法说明 |
| :--: | :--: |
| append (char c) | 将字符添加到输出流中 |
| clear() | 清空页面缓存中的内容 |
| close() | 关闭网页的输出 |
| flush() | 网页流的刷新 |
| println() | 将内容直接打印在HTML标记中 |
| write() | 与println()方法相似,区别在于println()方法可以输出各种类型的数据，而write方法只能输出与字符相关的数据,例如字符、字符数组、字符串等 |

## page对象
page对象的实质是java.lang.Object对象，它代表转译后的Servlet。page对象是指当前的JSP页面本身，在实际开发中并不常用

| page常用方法            | 方法说明                  |
|:-------------------:|:---------------------:|
| getClass ()         | 返回当时被转译的Servlet类      |
| hashCode()          | 返回此时被转译的Servlet类的哈希代码 |
| toString ()         | 将此时被转译的Servlet类转换成字符串 |
| equals (0bject obj) | 比较此时的对象是否与指定的对象相等     |
| clone()             | 将此时的对象复制到指定的对象中       |
| copy (0bject obj)   | 对指定对象进行克隆             |

## config对象
config对象一般用于在页面初始化时传递参数。

| config常用方法                      | 方法说明              |
|:-------------------------------:|:-----------------:|
| getInitParameter (String arg0) | 获得指定的初始化值         |
| getServletName ()               | 获得Servlet名字       |
| getServletContext()             | 获得ServletContext值 |
| equals (0bject obj)             | 比较此时的对象是否与指定的对象相等 |
| getIni tParameterNames ()       | 获得初始化值得枚举值        |
| toString()                      | 获得此对象的值           |

一般而言很少在页面中使用config对象，因为JSP页面的实质是Servlet

![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240110005040.png)































