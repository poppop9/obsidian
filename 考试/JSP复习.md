第一章
~~第二章~~
三，注释生命，指令，动作
四，
五，√√√
六，javabean的生命周期
~~七~~
八，增删改查，如何指定数据源
九，不管
十，servlet，1，3，生命周期
十一，
十二，
~~十三~~
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
### C/S，B/S
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
// 设置重定向
response.sendRedirect ("index.jsp")
```

头meta信息是指在HTML页面中存在与\</head\>\</head\>之间的信息

## session对象
>session对象可以用来判断是否为同一用户【HTTP协议是一种无状态的协议】，还可以用来记录客户的连接信息等

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
# 会话
## 会话管理的过程
1. 识别意图：当用户与系统开始交互时，系统首先要识别用户的意图。这可以通过自然语言处理（NLP）技术来实现，系统会分析用户的输入并尝试确定用户想要达到的目标或请求。
2. 状态跟踪：系统会跟踪对话的状态。这包括记录用户的先前输入、系统的先前响应以及任何其他相关信息。通过跟踪对话状态，系统可以根据先前的上下文提供更准确和连贯的响应。
3. 生成回应：基于用户输入和对话状态，系统会生成合适的回应。这可能涉及调用后端服务、查询数据库或执行其他必要的操作以满足用户的请求。生成回应的过程通常基于预定义的规则、模板或机器学习算法。
4. 输出回应：系统将生成的回应返回给用户。这可以通过文本、语音或其他合适的方式进行。
5. 用户反馈：系统可能接收用户对输出回应的反馈。这可以包括用户的确认、修正或进一步的请求。系统可以利用这些反馈来进一步改进对话过程和响应质量。
6. 上下文管理：在对话的不同轮次之间，系统需要管理上下文信息，以确保对话的连贯性。这可以通过在对话状态中跟踪关键信息、使用上下文向量或利用其他技术来实现。
7. 终止会话：当用户结束对话或系统检测到会话已完成时，会话可以被终止。这可能涉及保存会话历史记录、清除对话状态或采取其他适当的操作。
## 如何判断会话周期
- 建立和终止连接：在网络通信中，会话可以从建立连接开始，到终止连接结束。建立连接可以是客户端与服务器之间的连接，如通过TCP/IP协议建立套接字连接。终止连接可以是任一端主动关闭连接，或者在一定时间间隔或不活动时间后自动关闭连接。
- 用户登录和注销：在许多应用程序中，会话的周期可以与用户的登录和注销过程相关联。当用户成功登录时，会话开始。当用户注销或会话超时时，会话结束。这通常需要在服务器端维护会话状态和对用户进行身份验证。
- 时间限制：会话周期可以根据时间限制来判断。例如，可以设置一个固定的会话时长，超过该时长则认为会话已结束。这可以通过使用定时器或在服务器端进行计时来实现。
- 活动状态：会话周期可以根据用户的活动状态来确定。如果用户在一段时间内没有任何活动（如发送请求或交互），则可以认为会话已结束。这可以通过在服务器端记录用户的最后活动时间，并根据一定的规则判断会话是否已结束。
- 应用程序逻辑：具体的应用程序逻辑也可以定义会话周期。例如，在电子商务应用中，可以根据用户完成购物流程或结账过程来确定会话的周期。
## 会话对象
会话对象是指在计算机程序中用于跟踪和管理会话状态的数据结构或对象。它通常用于存储与特定用户或客户端相关的会话信息，以便在会话期间跟踪和访问这些信息。会话对象通常包含以下几个方面的信息：
- 会话标识符（Session ID）：会话对象通常包含一个唯一的会话标识符，用于识别和关联特定的会话。这个标识符可以是一个字符串、整数或其他可以唯一标识会话的值
- 会话数据（Session Data）：会话对象可以包含与会话相关的数据。这些数据可以是用户的身份信息、用户的偏好设置、购物车内容、临时存储的状态等。会话数据可以是键值对、对象、数组或其他适当的数据结构
- 会话状态（Session State）：会话对象可以用于跟踪和管理会话的状态信息。这可能包括用户的登录状态、权限和访问控制、会话的活动时间等。会话状态可以在会话期间不断更新和修改
- 生命周期管理（Lifecycle Management）：会话对象通常提供方法或接口来管理会话的生命周期，例如开始会话、结束会话、检查会话是否过期等。这使得应用程序可以根据需要创建、销毁和管理会话对象
## session会话周期，cookie
会话：从用户打开浏览器连接到一个Web应用或者某个界面，直至关闭浏览器这个过程称为一个会话。其实打开一个浏览器就意味着打开了一个会话对象

==session对象生命周期==：从用户访问某个页面到关闭浏览器这段时间称为session对象的生命周期【也就是从会话开始到结束这段时间】

==session对象与Cookie对象==：session对象与Cookie对象是一一对应关系。JSP引擎会将创建好的session对象存放在对应的Cookie中

Cookie对象：将只需在客户端处理的数据存放在本地计算机上，不需要通过网络传输，提高处理效率，如记住密码
# Servlet
>Servlet【Server Applet】，是利用Java类编写的服务端程序，可以被看作是位于客户端和服务端的一个中间层，负责接收和请求客户端用户的响应

Servlet使用了很多Web服务器都支持的API，可调用和扩展Java中提供的大量程序设计接口、类、方法等功能

JSP的实质就是Servlet，所有JSP页面传回服务端都要转为Servlet进行编译、运行
## 功能
 - 对客户端发送的数据进行读取和拦截
>客户端在发送一个请求时，一般会携带一些数据，当一个servlet接收到这些请求时，Java Servlet中的类通过所提供的方法就能得到这些参数，也正为这个原因，Servlet可以对发送请求起到拦截作用，它在某些请求前先做一个预处理分析，从而判断客户端是否可以做某些请求，当Servlet具有如上功能时，一般称之为拦截器。

- 读取客户端请求的隐含数据
>客户端请求的数据可以分为隐含数据和显式数据：隐含数据一般不直接跟随于URL中，它存在于请求的来源、缓存数据(cookie)、客户端类型中；显式数据显然是用户可以直观看到的，例如表单数据和URL参数。

 - 运行结果或者生成结果
>当一个Web应用程序对客户端发送的请求做出响应时，一般需要很多中间过程才能得到结果。Servlet起到这个中间角色的功能，协调各组件、各部分完成相应的功能，根据不同的请求做出相应的响应并显示结果。

- 发送响应的数据
>Servlet在对客户端做出响应并处理得出结果后，会对客户端发送响应的数据，以便让客户端获取请求的结果数据。在Web应用程序中，Servlet的这个作用相当突出，无论现有的技术多么突出，都是基于这个作用点出发的。



















