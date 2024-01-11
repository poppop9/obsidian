[TOC]
第一章
~~第二章~~
三，注释生命，指令，动作
四，
五，√√√
六，√√√
~~七~~
八，增删改查，如何指定数据源
~~九~~
十，1，3
十一，
十二，
~~十三~~

```java
dddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddd
```
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
## 介绍
### 功能
 - 对客户端发送的数据进行读取和拦截
>客户端在发送一个请求时，一般会携带一些数据，当一个servlet接收到这些请求时，Java Servlet中的类通过所提供的方法就能得到这些参数，也正为这个原因，Servlet可以对发送请求起到拦截作用，它在某些请求前先做一个预处理分析，从而判断客户端是否可以做某些请求，当Servlet具有如上功能时，一般称之为拦截器。

- 读取客户端请求的隐含数据
>客户端请求的数据可以分为隐含数据和显式数据：隐含数据一般不直接跟随于URL中，它存在于请求的来源、缓存数据(cookie)、客户端类型中；显式数据显然是用户可以直观看到的，例如表单数据和URL参数。

 - 运行结果或者生成结果
>当一个Web应用程序对客户端发送的请求做出响应时，一般需要很多中间过程才能得到结果。Servlet起到这个中间角色的功能，协调各组件、各部分完成相应的功能，根据不同的请求做出相应的响应并显示结果。

- 发送响应的数据
>Servlet在对客户端做出响应并处理得出结果后，会对客户端发送响应的数据，以便让客户端获取请求的结果数据。在Web应用程序中，Servlet的这个作用相当突出，无论现有的技术多么突出，都是基于这个作用点出发的。

### 特点
- 高效率，Servlet本身就是一个Java类，在运行的时候位于同一个Java虚拟机中，可以快速地响应客户端的请求并生成结果。在Web服务器中处理一个请求使用的都是线程而非进程，也就是说在性能开销方面就小很多，无须大量的启动进程时间，在高并发量访问时，一个进程可以有多个线程，并发是线程在CPU使用的开销代价要远小于进程的开销
- 简单方便，开发一个Web程序时，从开发顺序上说比较简单，首先定义一个Servlet类，然后在系统（web.xml）中配置程序，继而发布程序，这样一个Web程序就完成了。在开发的过程中，系统提供了大量的实用工具方法，可以处理复杂的HTML表单数据、处理cookie、跟踪网页会话等
- 持久性，Servlet只需Web服务器加载一次，可以在不同请求之间保持服务
- 可扩展性，Servlet是java编写的，具备java的所有特点
- 安全性，从外界调用一个servlet的唯一方法就是通过Web服务器，提供了高水平的安全保障。
### JSP与Servlet
Servlet是服务器端运行的一种Java应用程序。当浏览器端有请求则将其结果传递给浏览器。
在JSP中使用到的所有对象都将被转换为Servlet或者非Servlet的Java对象，然后被执行，所以执行JSP实际上与执行Servlet是一样的。
由于JSP编写HTML页面直观且易调试，因此JSP逐步取代Servlet在开发页面中的作用
#### 区别
- 编程方式不同：JSP是为了解决Servlet中相对困难的编程技术而开发的技术，JSP比servlet编写起来简单
- Servlet必须在编译以后才能执行：JSP并不需要另外进行编译，JSP容器会自动完成这一工作，而Servlet在每次修改代码之后都需要编译完才能执行，JSP页面部署到WEB应用时只需将JSP页面复制到指定的目录下，当它第一次被访问时，WEB服务器自动将JSP代码转换为Java代码并自动编译
- 运行速度不同：由于JSP容器将JSP程序编译成Servlet的时候需要一些时间，所以JSP的运行速度比Servlet要慢一些，不过，如果JSP文件能毫无变化的重复使用，它在第一次以后的调用中运行速度就会和Servlet一样了，这是因为JSP 容器接到请求以后会确认传递过来的JSP是否有改动，如果没有改动的话，将直接调用JSP编译过的Servlet类，并提供给客户端解释执行，如果JSP文件有所改变，JSP 容器将重新将它编译成Servlet，然后再提交给客户端
- Servlet用来写业务逻辑层是很强大的，但是对于写表示层就很不方便。JSP则主要是为了方便写表示层而设计的。
### 工作原理
Servlet是javax.Servlet包中HttpServlet类的子类，运行在Web服务器的Servlet容器里。
Servlet容器，从属于Java虚拟机，根据Servlet的生命周期的规范，负责执行Servlet对象的初始化、运行和卸载等动作。
Servlet的生命周期：Servlet在容器中从创建到删除的过程。
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240110223019.png)
### 运行顺序
![[Excalidraw/杂/草稿纸 Draw.md#^group=E9go_c9fX7nkr7ocSUrYL]]
## 基本流程
1. 客户端通过HTTP提出请求
2. Web服务器接收该请求交给Servlet容器，然后再调用Servlet中的方法来处理。如果这个Servlet尚未被加载，Servlet容器将把它加载到Java虚拟机并且执行它
3. Servlet将接收该HTTP请求并用特定的方法进行处理：可能会访问数据库、调用Web服务、EJB调用或直接给出结果，并生成一个响应
4. 这个响应由Servlet容器返回给Web服务器
5. Web服务器包装这个响应，以HTTP响应的方式发送给Web浏览器。
## 生命周期阶段
1. 初始化阶段
	1. 装载：由servlet容器装载1个servlet类，把它装载到java内存中，servlet容器可创建1个servlet对象并与web.xml中的配置对应起来
	2. 初始化子阶段：调用servlet中的init()方法
2. 运行阶段【这个阶段中是实际响应客户端的请求】
>当有请求时，Servlet会创建HttpServletRequest和HttpServletResponse对象，然后调用service(HttpServletRequest request, HttpServletResponse response)方法。service()方法通过request对象获得请求对象的信息并加以处理，再由response对象 对客户端做出响应。
3. 消亡阶段
>当Servlet应用被终止后，Servlet容器会调用destory()方法对Servlet对象进行销毁动作。在消亡的过程中，Servlet容器将释放它所占的资源。

![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240110223522.png)
## 生命周期过程
①装载Servlet，装载情形：Servlet容器启动时自动加载某些Servlet；在Servlet容器启动后,客户首次向Servlet发出请求；Servlet的类文件被更新后，重新加载Servlet。
②实例化一个Servlet实例对象。
③调用Servlet的init( )方法进行初始化。
④服务。容器收到对该Servlet的请求，则调用该Servlet对象的service（）方法处理请求。
⑤卸载。
当服务器端不再需要该Servlet的时候，服务器调用destroy（）方法卸载该Servlet，释放Servlet运行时占用的资源。

![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240110223634.png)
## 编写和部署Servlet
1. 创建Java工程
2. 添加web框架
3. 加载lib包
4. 创建servlet类
5. 编写servlet类
	1. FirstServlet：定义了init()方法、doGet()方法、doPost()方法和destory()方法
		1. 多次刷新，init方法只会执行一次，doGet方法会执行多次

![700](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240110223959.png)

6. 配置xml
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240110224046.png)

7. 运行：访问路径`localhost:8080/HelloServlet_war_exploded/firstServlet `
## 请求与响应
> - Web访问最基本的两个过程
> - JSP最基本的两个内置对象
> - 是一个Web应用系统构建一个完整程序的必要条件
> - 是前端人员开发所要了解的原理与方法

JSP内置对象和Servlet的Java对象是有对应关系：【==JSP与Servlet是依靠Web容器结合起来使用的==】
- request对象---HttpServletRequest
- response对象---HttpServletResponse
- session对象---HttpSession
- out对象---PrintWriter
- application对象---ServletContext

### Web容器
>Web容器是一种服务程序，在服务器一个端口就有一个提供相应服务的程序，而这个程序就是处理从客户端发出的请求，如JAVA中的Tomcat容器。一个服务器可以有多个容器，常见的Web容器有：IIS(asp容器)、Tomcat(servlet容器)、Jboss(EJB容器)

#### 作用
- 创建一个servlet实例
- 并完成servlet注册
- 根据web.xml中的URL进行响应
- 当请求来到容器时，Web容器会转发给对应的Servlet来处理请求

![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240110230843.png)
Web服务器：提供web服务的软件或主机【Web服务器软件或装有Web服务器软件的计算机】，可以处理 HTTP 协议。常见的Web服务器有：Apache、IIS、Tomcat、Jetty、JBoss、webLogic等

Servlet容器：是与Servlet交互的Web服务器的一部分，它可以从Web页面接收请求后再将这些请求重定向到Servlet对象中，然后将动态生成的结果返回到正确的位置中
#### 响应过程
当客户端请求Web服务器时，会使用HTTP来传递请求、标头、参数等信息
1. 当Web服务器将请求转给Web容器时
2. Web容器会创建一个HttpServletRequest和HttpServletResponse对象，将请求中的信息传递给HttpServletRequest对象
3. 而HttpServletResponse对象则作为对客户端响应的Java对象

### 请求到响应的流程
Web容器会根据配置信息（例如web.xml），查找相对应的Servlet并调用它的service()方法。service()方法会根据HTTP请求的方式，决定是调用doPost()方法或者是doGet()方法。

如示意图中，doPost()方法中，可以使用HttpServletRequest对象和HttpServletResponse对象。使用getParameter()取得请求参数值，使用getWriter()取得输出流对象并进行响应处理，后由Web容器转换为HTTP响应，由HTTP服务器对浏览器做出响应。随后Web容器将HttpServletRequest对象和HttpServletResponse对象
销毁回收，请求响应结束。
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240110231223.png)
### doXXX()方法
Servlet中的service()方法包括多种：doGet()、doPost()、doHead()等：
- 当Method是POST时，请求会调用doPost()方法
- 当Method是GET时，请求会调用doGet()方法

在定义Servlet时，一般是继承HttpServlet类，然后定义doPost()或者doGet()方法

在自定义Servlet时不实现doGet()或者doPost()方法，那么程序会调用默认的doGet()或doPost()方法，而默认的doGet()或doPost()方法会将页面重定向到错误页面
### HttpServletRequest对象
>HttpServletRequest对象是请求封装对象，***由Web容器生成***，使用该对象可以取得HTTP请求中的信息

在Servlet中，也是使用该对象进行请求处理的。如果要==共享==request中的属性，可以将请求对象设置到该对象中，那么Servlet在同一请求中就可以共享其对象

JSP内置对象request实质就是HttpServletRequest。可实现读取body内容、取得上传文件和调派请求等功能
#### 方法
- 读取body内容：运用getReader()方法获取Body内容
- 获取上传文件的内容：使用getInputStream()方法 / getPart()和getParts()方法
- 实现调派请求：使用getRequestDispatcher()方法实现多个Servlet之间的调整
	- include()
	- forward()
	![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111002320.png)
	在web程序中，经常是由多个Servlet来完成请求。RequestDispatcher接口【该接口可以由HttpServletRequest的getRequestDispatcher()方法取得】就是为了多个Servlet之间的调整而实现的。调用时指定跳转的URL地址即可完成跳转动作。RequestDispatcher接口有两种方法实现跳转Servlet：include()和forward()。
	![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111002641.png)
### HttpServletResponse对象
>HttpServletResponse是用于浏览器做出响应的操作对象，可以设置响应类型，也可以直接输出HTML内容

- setContentType()设置JSP响应类型
- getWriter()取得PrintWriter对象，可用于输出字符
```java
response.setContentType（＂ text／ html； charset＝ UTF - 8＂）；／／ 设置响应的类型和编码
PrintWriter out＝ response.getWriter（）；／／ 取得PrintWriter（） 对象
out.println("<!DOCTYPE HTML>");
out.println("<HTML>");
out.println(" <HEAD><TITLE>A Servlet</TITLE></HEAD>");
out.println(" < BODY > ");
out.print(body);
out.println(" </BODY>");
out.println("</HTML>");
out.flush();
out.close();
```

在Servlet开发中，须告诉浏览器以何种方式处理响应，所以要设置标头，在设置context-type中，指定MIME类型后，浏览器就能知道标头类型。
MIME类型有text/html、application/pdf、application/jar、application/x-zip、image/jpeg等。在应用程序中，可以在web.xml中设置MIME类型。

- getOutputStream()取得ServletOutputStream流对象，可用于下载文件
>![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111003602.png)
- serHeader()和addHeader()设置标头
- sendRedirect(),用于对页面进行重定向
>sendRedirect()方法会在响应中设置HTTP状态码和Location标头，当客户端接收到这个标头时，会重新请求指定的URL，所以地址栏上的地址会发生改变
>![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111003753.png)

- sendError()发送错误消息
>如果在处理请求的时候发生错误，就可以用sendError()方法传递服务器的状态和错误消息【例如，请求的页面地址不存在，则可发送如下错误信息：`response.sendError(HttpServletResponse.SC_NOT_FOUND);`
> `SC_NOT_FOUND`表示资源文件不存在，服务器会响应404错误代码，错误代码统一定义在httpServletResponse接口上】
> 
> 还可以***自定义错误信息***，如下：
> `response.sendError(HttpServletResponse.SC_NOT_FOUND，”页面错误”);`
## 会话管理
>在人机交互过程中，会话管理是指保持用户的整个会话活动的交互与计算机系统跟踪的过程
>
>会话管理分为：
>- 桌面会话管理
>- 浏览器会话管理
>- Web会话管理【Web会话管理（通常指的是session以及Cookie），也称为==会话跟踪==】
### 会话管理解决方案
#### 使用隐藏域
> 隐藏域是指将表单中的内容在显示页面时隐藏，即不显示数据

- 方法：在JSP中将input标签的type属性设定为hidden,即生成一个隐藏表单域。再将会话的唯一标识记录到隐藏域中的value属性中，并设定name属性值。当表单提交时，会话标识也被提交到服务端，服务端根据它找到对应的会话对象。
- 特点：使用隐藏域时，需要在每个页面中都包含会话标识表单，这样才能在许多页面跳转之间保存会话，并对它进行管理。

>[!hint] 此方法实现起来比较烦琐，安全性较差，不适合隐秘性的数据，在目前的开发中较少使用
#### 使用URL重写
>URL重写：在URL地址的末尾添加会话标识，改写了原先的URL地址

- 本质：用于唯一标识会话的信息，以参数的形式添加到URL中，服务端接收到请求时，解析出会话标识，然后利用会话标识查找出与当前请求对应的会话对象。
- 优点：是用在浏览器中Cookie被禁用的情况下，利用该方法可以很好地实现会话跟踪而不会受到浏览器参数设定的影响。
- 特点及缺陷：在URL后面添加会话标识，整个Web应用中的超链接或者脚本中用到的URL都需要添加会话标识，Web应用中的每一个页面都需要动态生成，页面中的每一个链接或者有客户生成的跳转指令都必须加上会话标识，才能确保是当前会话。当客户端访问静态页面时，会话标识将会丢失，当重回动态页面时将不能继续此前的会话。
- 安全性：当用户在浏览网页时，可能会将URL复制下来分享给朋友，因为URL中会包含会话标识，那么其他人可能与当前浏览者使用同一会话对象，这样当前浏览者的个人隐私就暴露了，信息不再安全。
#### 使用Cookie
>[!hint] 利用Cookie实现会话管理是最容易的实现方式，也是使用较多的方法

- 原理：在服务端保存的会话对象中设定会话的唯一标识，客户端将会话标识保存在Cookie中，当浏览器发起请求时，从Cookie中取得会话标识并发送给服务端，服务端在收到请求后，根据发送过来的会话标识查找到对应的会话对象，这样服务端就清楚当前是哪个客户端在连接，并且可以从会话中获得信息。
- 特点：利用Cookie实现会话管理是目前开发中采用的主流方法，大多数的动态页面开发技术都实现了这一功能，并且其管理流程是自动完成的，在实现上并不需要多大的开发工作量。

![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111010905.png)
### HttpSession会话管理
服务端不能主动连接客户端，只能等待并答复客户端请求。HTTP协议本身并不支持服务端保存客户端的状态等信息。于是，Web服务器中引入了session的概念，用来保存客户端的信息

在java中，使用`javax.servlet.http.HttpSession类`来实现session会话。每个请求者对应一个session对象，客户的所有状态信息都保存在该对象里。当用户第一次请求服务器时，就创建了session对象。它以`key-value`的形式进行保存，通过相对应的读写方法来保存客户的状态信息。

```java
 //获取Session对象
 HttpSession session = request.getSession();	 
//设置Session中的属性
 Session.setAttribute(“username”,”John”);	
```

- 利用session来保存登录信息
![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111181435.png)
#### HttpSession管理会话的原理
HttpSession会话管理是利用服务器来管理会话的机制，当程序为某个客户端的请求创建了一个session的时候，服务器会检查客户端的请求是否已经包含了一个session标识，如果已经有了session标识，服务器就把该session检索出来使用；如果请求不包含session标识，就为客户端创建一个该请求的唯一session标识。
![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111181557.png)
#### HttpSession中禁用Cookie
可以通过配置的方式在Web项目中禁用Cookie，禁用方法如下：
- 在Web项目中的web目录中的META-INF文件夹下，打开或者创建context.xml文件，并编辑内容如图【仅对单个项目的Cookie禁止】
- 打开Tomcat的配置文件context.xml，将cookies禁用掉【禁止部署在Tomcat服务器里的Web项目使用Cookie】
#### HttpSession的生命周期
1. 创建：当客户端第一次访问服务器时，服务器为每个浏览器创建不同Session的ID值。在服务器端使用request.getSession()方法来获得HttpSession对象
2. 使用：创建HttpSession对象后，使用Session对象进行数据的存取和传输。
	1. 将产生的sessionID存入Cookie
	2. 当客户端再次发送请求时，会将sessionID与request一起传送给服务端。
	3. 服务端根据请求过来的sessionID与保存在服务器端的session对应起来，判断是否为同一session。
3. 消亡：有3种方式可以结束session对象
	1. 将浏览器关闭
	2. 调用HttpSession的invalidate()方法
	3. session超时

关闭浏览器，这样会使浏览器端的session失效，服务器端session并不会失效。如果服务器进程终止了，那么session会被结束。在session结束时，服务器会清空当前浏览器的相关数据信息。
#### HttpSession的有效期
>当某用户访问的session超过这个有效期时，那么session就失效了，服务器会将它从内存中清除

设定session的有效期有以下三种方法：、
- 在对应的Web服务器配置中设置所有session的有效期
- 调用session的setMaxInactiveInterval(long interval)进行设定
- 在web.xml中修改，例如：
	```xml
	<session-config>
	<!--会话超时时长为30分钟-->
	<session-timeout>30</session-timeout>
	</session-config>
	```
# Servlet过滤器，监听器
>过滤器和监听器是Servlet规范里的两个高级特性

- 过滤器的作用是通过对request、response的修改实现特定的功能【例如请求数据字符编码、IP地址过滤、异常过滤、用户身份认证等】
- 监听器的作用是用于监听Web程序中正在执行的程序，根据发生的时间做出特定的响应
## Servlet进阶API
在编写完一个Servlet类后，通常需要在`web.xml`中或者`通过注解`进行相关配置，这样Web容器才能读取Servlet设置的信息【包括其类地址、初始化等】

对于每个Servlet的配置，Web都会生成与之相对应的ServletConfig对象，从ServletConfig对象中可以得到Servlet的初始化参数
### ServletConfig
在Web容器启动后，通过加载web.xml文件读取Servlet的配置信息，实例化Servlet类，并且为每个Servlet配置信息产生唯一一个ServletConfig对象。在运行Servlet时，调用Servlet接口的init()方法，将产生的ServletConfig作为参数传入Servlet中
![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111183502.png)
初始化方法只会被调用一次，即容器在启动时实例化Servlet和创建ServletConfig对象，且Servlet与ServletConfig是一一对应关系，之后就直接执行service()方法。
#### 使用ServletConfig
当容器初始化Servlet时，会为Servlet创建唯一的ServletConfig对象。利用web容器读取web.xml文件，将初始化参数传给ServletConfig，而servletConfig作为对象参数传递给init()方法中。
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111184327.png)
### GenericServlet
GenericServlet类同时实现Servlet和ServletConfig两个接口

GenericServlet类使得编写Servlet更加方便，提供了一个简单的方法，这个方法用来执行有关servlet生命周期的方法以及在初始化时对ServletConfig对象和ServletContext对象进行说明。
### ServletContext
ServletContext对象是Servlet中的全局存储信息，当服务器启动时，Web容器为Web应用创建唯一的ServletContext对象，应用内的Servlet共享同一个ServletContext。

在ServletContext中存放着共享数据，应用内的Servlet可以通过ServletContext对象提供的方法获取共享数据。ServletContext接口中定义了运行Servlet应用程序的环境信息，可以用来获取请求资源的URL、设置与存储全局属性、Web应用程序初始化参数。
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111185031.png)
## 注解
### @WebServlet主要属性列表
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111184618.png)

利用初始化信息设定跳转信息
![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111184757.png)

### @WebInitParam主要属性列表
![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111184642.png)
## 监听器
>监听器就是应用监听事件来监听请求中的行为而创建的一组类

HttpServletRequest、HttpSession、ServletContext对象在Web容器中遵循生成、运行、销毁这样的生命周期。当进行相关的监听配置后，Web容器就会调用监听器上的方法，进行对应的事件处理，从而了解运行的情况或者运行其他的程序。

使用监听器需要实现相应的监听接口。在触发监听事件时，应用服务器会自动调用监听方法。
### ServletContext事件监听器
ServletContextListener被称为“ServletContext生命周期监听器”，可以用来监听Web程序初始化或者结束时响应的动作事件，提供两个监听方法：
- contextInitialized()：该方法用于通知监听器，已经加载Web应用和初始化参数。
- contextDestroyed()：该方法用于通知监听器， Web应用即将关闭。
---
- Web应用程序启动时，自动开始监听，调用contextInitialized()方法，传入ServletContextEvent参数，它封装了ServletContext对象，可以通过ServletContextEvent的getServletContext()方法取得ServletContext对象，通过getInitParameter()方法取得初始化参数。
- Web应用关闭时，自动调用contextDestroyed()方法，同样会传入ServletContextEvent参数。在contextInitialized()中可以实现应用程序资源的准备事件， 在contextDestroyed()中可以实现对资源的释放。例如，可以在contextInitialized()方法中实现Web应用的数据库连接、读取应用程序设置等，在contextDestroyed()中设置数据库资源的释放。
#### 实现ServletContextListener的步骤
1. 编写一个监听类并实现ServletContextListener接口
2. 用web.xml进行相关的配置
	```xml
	<listener>
	  <listener-class>com.test.MyServletContextListener</listener-class>
	</listener>
	```

3. 或者利用注入的方式注入监听类
	```java
	@WebListener
	public class MyServletContextListener implements ServletContextListener{
	}
	```

4. 若需要初始化参数， 则需要在web.xml中进行配置
	```xml
	<context-param>
	  <param-name>user_name</param-name>
	  <param-value>test</param-value>
	</context-param>
	```
### ServletContextAttributeListener - 属性监听器
>用来监听Application属性的添加、移除或者替换时响应的动作事件，提供3个监听方法：
> - attributeAdded()方法:该方法用于通知监听器，有对象或者属性被添加到Application中。
> - attributeRemoved()方法:该方法用于通知监听器，有对象或者属性被移除到Application中。
> - attributeReplaced()方法:该方法用于通知监听器，有对象或者属性被更改到Application中。

在ServletContext中添加属性、移除属性或者更改属性时，与其相对应的方法就会被调用。同样，在Web应用程序中，实现ServletContextAttributeListener的方法也有两种：
- 利用注入的方式注入监听类：
	```java
	@WebListener
	public class MyServletContextAttributeListener implements ServletContextAttributeListener{
	}
	```
- 在web.xml中配置
	```xml
	<listener>
		<listener-class>
		com.test.MyServletContextAttributeListener
		</listener-class>
	</listener>
	```
### HttpSession事件监听器
![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111190906.png)
- HttpSessionIdListener用来监听session ID的变化。
- HttpSessionListener是“HttpSession生命周期监听器”，用来监听HttpSession对象初始化或者结束时响应的动作事件。
- HttpSessionActivationListener是“HttpSession对象转移监听器”，用来实现它对同一会话在不同的JVM中转移。
- HttpSessionAttributeListener是“HttpSession属性改变监听器”，用来监听HttpSession对象加入属性、移除属性或者替换属性时响应的动作事件。
- HttpSessionBindingListener是“HttpSession对象绑定监听器”，用来监听HttpSession中设置成HttpSession属性或者从HttpSession中移除时得到session的通知。
### HttpSessionIdListener
请求的session ID发生变化时（场景：在失效瞬间生成新Session，SessionID会改变），会触发sessionIDChanged()方法，并传入HttpSessionEvent和oldSessionId参数，使用HttpSessionEvent中的getSession().getId()获取新的session ID,oldSessionId代表改变之前的session ID。

实现方式有2种：
- 注入方式
	```
	@WebListener
	public class MyHttpSessionIdListener implements HttpSessionIdListener{
	}
	```
- web.xml配置
	```
	<listener>
		<listener-class>
		com.wujialiang.MyHttpSessionIdListener
		</listener-class>
	</listener>
	```
### HttpSessionListener
在HttpSession对象初始化或者结束前，会自动调用sessionCreated()方法和sessionDestroyed()方法，并传入HttpSessionEvent参数，它封装了HttpSession对象，通过HttpSessionEvent的getSession()方法取得HttpSession对象。

在Web应用程序中，实现HttpSessionListener的方法同样有两种，形式如下。
- 注入方法
	```
	@WebListener
	public class MyHttpSessionListener implements HttpSessionListener{
	}
	```
- web.xml方法
	```
	<listener>
		<listener-class>
		com.test.MyHttpSessionListener
		</listener-class>
	</listener>
	```

利用HttpSessionListener记录在线人数：
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111192231.png)
### HttpServletRequest事件监听器
![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111192330.png)
- ServletRequestListener是“Request生命周期监听器”，用来监听Reuqest对象初始化或者结束时响应的动作事件
- ServletRequestAttributeListener是“Request属性改变监听器”，用来监听Request对象加入属性、移除属性或者替换属性时响应的动作事件
### ServletRequestListener
ServletRequestListener提供2个监听接口：
- requestInitialized():该方法用于通知监听器，产生了新的request对象。
- requestDestroyed():该方法用于通知监听器，已经消除一个request对象。

在request对象初始化或者结束前，会自动调用requestInitialized()方法和requestDestroyed()方法，并传入ServletRequestEvent参数，它封装了ServletRequest对象，可以通过ServletRequestEvent的getServletContext()方法取得Servlet上下文对象，通过getServletRequest()方法得到请求对象，有2种实现方式：
- 注入方式监听
	```
	@WebListener
	public class MyServletRequestListener implements ServletRequestListener{
	}
	```

- web.xml配置
	```
	<listener>
		<listener-class>
		com.wujialiang.MyServletRequestListener
		</listener-class>
	</listener>
	```
### ServletRequestAttributeListener
该接口提供3个监听方法：
- attributeAdded():该方法用于通知监听器，已经在Request中添加一个对象或者变量。
- attributeRemoved():该方法用于通知监听器，已经在Request中移除一个对象或者变量。
- attributeReplaced():该方法用于通知监听器，已经在Request中替换一个对象或者变量。

当对request范围的对象或者变量进行操作时，Web容器会自动调用与实现接口类相对应的方法。ServletRequestAttributeEvent是一个对象，可以利用其getName()方法得到操作对象或者变量的名称，利用getValue()方法得到操作对象或者变量的值，有2种实现方式：
注入方式
```
@WebListener
public class MyServletRequestAttributeListener implements HttpSessionAttributeListener{
}
```
## 过滤器
阻挡某些事件的发生。在Web应用程序中，过滤器在Servlet之前，既可以拦截、过滤浏览器的请求，也可以改变对浏览器的响应。它在服务器端与客户端起到了一个中间组件的作用，对二者之间的数据信息进行过滤。
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111194314.png)
1个Web应用程序，可以有多个过滤器，组成一个过滤器链，如经常使用过滤器完成字符编码的设定和验证用户的合法性。过滤器链中的每个过滤器都各司其职地处理并转发数据。
### 实现与设置过滤器
在Servlet中要实现过滤器，必须实现Filter接口，并用注入的方式或者在web.xml中定义过滤器，让Web容器知道应该加载哪些过滤器。主要分以下5个步骤：
- 实现Filter接口
	- init()方法:用来初始化过滤器，利用该对象可以得到过滤器中初始化的配置参数信息。
	- doFilter()方法:过滤器中主要实现过滤的方法。当客户端请求目标资源时，Wb应用程序会调用与此目标资源相关的doFilter()方法，在该方法中，实现对请求和响应的数据处理。
	- destroy()方法:用于释放过滤器中使用的资源。
- 实现FilterConfig接口
	- getFilterName():用于得到过滤器的名字。
	- getlnitParameter():得到过滤器中初始化的参数值。
	- getInitParameterNames():得到过滤器配置中的所有初始化参数名字的枚举类型。
	- getServletContext():得到Servlet上下文文件对象。
- 设置过滤器
	- 注入
	- web.xml中配置
- 请求封装器
>请求封装器是指利用HttpServletRequestWrapper类将请求中的内容进行统一修改，例如修改请求字符编码、替换字符、权限验证等
- 响应封装器
>响应封装器是指利用HttpServletResponseWrapper类将响应中的内容进行统一修改，例如压缩输出内容、替换输出内容等。有些时候需要对网站的输出内容进行控制，一般有两种方法：一是在保存数据库前对不合法的内容进行替换：二是在输出端进行替换。若是对每一个Servlet都进行输出控制，则任务量将非常大而且烦琐。可利用过滤器对Servlet进行统一处理，但是因为HttpServletResponse不能缓存输出内容，所以需要自定义一个具备缓存功能的response。
## 异步处理
一个普通的Servlet工作流程大致是：
- 首先，Servlet接收请求，对数据进行处理
- 然后，调用业务接口方法，完成业务处理【在Servlet中最耗时，因为它会执行一些数据库操作或者其他的跨网络调用等，在处理业务的过程中，该线程占用的资源不会被释放，这有可能造成性能的瓶颈。】
- 最后，将结果返回到客户端


异步处理可以先释放容器被占用的资源，将请求交给另一个异步线程来执行，业务方法执行完成后再生成响应数据。可以通过异步处理接口AsyncContext实现，ServletRequest提供了两个方法来启动AsyncContext：
- AsyncContext startAsync()
- AsyncContext startAsync(ServletRequest servletRequest,ServletResponse servletResponse)

上述两个方法都能得到AsyncContext接口的实现对象。当一个Servlet调用了startAsync()方法之后，该Servlet的响应就会被延迟，并释放容器分配的线程。AsyncContext接口的主要方法如下表所示。
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111203425.png)
# JavaBean
>软件设计分层的概念主要就是将软件各个部分进行解耦合设计，对于JSP动态开发技术而言，JavaBean是最基础的分层技术。

在JSP中，经常利用Java Bean实现核心的业务逻辑，而JSP页面用于表现层

Java Bean完全符合Java语言编码规范的要求和特性，形式上就是纯Java代码，它是可以重复使用的一个组件。在这种设计模式下，JSP页面只用于接收用户的输入以及显示处理之后的结果，因此不需要在JSP页面中嵌入大量的Java代码，不但提高了系统的可维护性，而且方便工作的分工。
## 特性
- 支持反射机制：利用反射机制可以分析出Java Bean是如何运行的
- 支持事件：事件是一种简单的通信机制，利用它可以将相应的信息通知给Java Bean
- 支持属性：可以自定义属性，利用标准标签与JSP页面交互数据
- 支持持久性：可以将Java Bean进行保存，在需要的时候又可以重新载入

![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111211539.png)
## 创建规范
- Java Bean类必须是public类
- 提供给JSP页面调用的方法，必须赋予public访问权限。
- Java Bean类中的属性，提供给JSP页面调用时必须提供public的get和set方法。
- 必须拥有不带参数的构造方法

使用Bean注意3个问题：
- 按规范定义Bean类【常见有2种部署方法】，并给出类属性的相应get和set方法
	- 将Bean的Class文件部署在Web服务器的公共目录中
	- 将Bean的Class文件部署在Web服务器的特定项目的目录中，即将Bean类的Class文件部署在Web项目的指定文件夹下。例如\ch09\src\com\eshore\pojo\User.class
- 在页面中要导入相应的Bean类
>![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111211758.png)

- 在JSP页面中利用<jsp:useBean>标签使用Bean类
## 设置Bean属性
- 使用<jsp:setProperty>
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111212040.png)
```jsp
// 在使用该标签时， 注意必须使用<jsp:useBean>标签创建一个Bean

<jsp:setProperty name="beanInstanceName"
                 property="*|propertyName [param='parameterName']|propertyName value='{String|<%=expression%>}'">
</jsp:setProperty>
```

使用<jsp:setProperty>标签有3种方式：
- 使用字符串或者表达式给Bean属性赋值， 其要求是表达式的值与Bean属性的值类型相同。
- 使用表单参数形式给Bean属性赋值， 其要求是表单中提供的参数名字与Bean属性的名字相同。
- 使用表单参数值给Bean属性赋值， 其要求是表单中提供的参数名字与<jsp:setProperty>标签中的param属性值名字相同。

表单参数是指在HTML表单中定义的输入字段的名称，而表单参数值是用户在该字段中输入的实际值
## 取得Bean属性
<jsp:getProperty>标签用来获得Bean属性值，并可以显示在浏览器中。该标签必须和<jsp:useBean>标签一起使用
## 🌗Bean的作用域
<jsp:useBean>标签中Bean的作用域有4个：page、request、session、application。JSP引擎会根据作用域给用户分配不同的Bean，运行多个用户拥有相同的Bean，每个客户的Bean是相互独立的。

- 当指定的范围为request时，针对同一用户的不同请求，JSP引擎都会给用户分配不同的Bean对象。当响应结束时，取消分配的Bean。==Bean的生命周期就是从客户请求开始到响应结束这段时间==
- 当指定的范围为page时，针对同一用户访问不同的页面，JSP引擎都会给用户分配不同的Bea对象。当客户进入当前页时，JSP引擎给用户分配一个Bean对象，当用户离开当前页时，取消分配的Bean对象。==因此，该Bean的生命周期就位于当前页==
- 当指定的范围为session时，针对同一用户访问同一Web项目下的不同页面时，JSP引擎都会给用户分配不同的Bean对象。当客户访问Web项目中某一目录下的页面时，JSP引擎给用户分配一个Bean对象，当用户离开Web目录时，取消分配的Bean对象，==因此，该Bean的生命周期是Web项目的一个Session时间==
- 当指定的范围为application时，JSP引擎为访问用户分配同一个Bean对象。==它的生命周期就是该Web应用的存在时间，即Web应用在服务器中存在的时间==

Bean的作用范围是由标签中的scope属性指定的，默认是page范围，即该Bean在当前页有效。scope属性决定了在使用<jsp:useBean>标签时是否要重新创建新的对象。如果某个Bean在其有效的范围内又出现一个id和scope都相同的Bean,那么就可以重用已经被实例化的Bean,而不是重新新建。
# JDBC
>JDBC【Java DataBase Connectivity】就是用Java语言操作关系型数据库的一套API
>
>数据库（Database）是指存储数据的容器，也被称为数据存储库（Data Store）。数据库能够存储大量结构化和非结构化的数据，包括文本、数字、图像、音频等各种类型的数据。它们是计算机系统中最重要的组件之一，被广泛用于各种应用程序和业务领域

常见的数据库软件有MySQL、Oracle、SQL Server、PostgreSQL等。这些软件具有管理、查询、更新、删除数据的功能，可以通过编写SQL语句来操作数据库中的数据

在Java中主要是使用JDBC来访问数据库。JDBC API是Java语言访问数据库的一种规范，是Java数据库的编程接口，是一组标准的Java接口和类
## Dao设计模式
DAO【Data Access Object】设计模式可以提高开发效率、实现模块化开发，在数据操作过程中，主要是以面向接口编程为主。

- 客户层：实际上就是客户端浏览器。
- 显示层：利用JSP和Servlet进行页面显示。
- 业务层：对数据层的原子性DAO操作进行整合。
- 数据层：对数据库进行原子操作，例如增加、删除、修改等。
- 数据库：保存数据的信息库。
### Dao划分
- VO(Value Object)：一个用于存放网页的数据，比如网页要显示一条用户的信息，则这个类就是用户类，主要由属性以及属性的setter和getter方法组成，VO类中的成员变量与表中的字段是相对应的。
- DatabaseConnection：用于打开和关闭数据库操作的类。
- DAO接口：用于声明数据库的操作，定义对数据库的原子性操作，例如增加、修改、删除等。
- DAOImpl：实现DAO接口的类，但是不负责数据库的打开和关闭。
- DAOProxy：也是实现DAO接口，主要完成数据库的打开和关闭。
- DAOFactory：工厂类，通过getInstance()取得DAO的实例化对象。
### DAO命名规则
- DAO命名为XxxDao，有的开发人员喜欢在其前加一个Ⅰ表示是接口类，例如UserDao或者IUserDao
- DAOImpl命名为XxxDaoImpl，表示是接口实现类，例如UserDaoImpl
- DAOProxy命名为XxxDaoProxy或者XxxService，例如UserDaoProxy或者UserService
- DAOFactory命名为XxxFactory，例如UserDaoFactory
- VO的命名与表名一致，VO中的属性与表字段一致
## JDBC建立过程
- 创建数据库
- 导入JDBC驱动包
>![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111213507.png)

- 建立数据库的一个连接
- 执行SQL语言
>![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111213650.png)
> ```
> MySQL注册方式为com.mysql.jdbc.Driver
> 连接方式为jdbc:mysql://IP:3306/database
> IP为连接的IP地址(示例中是localhost)，默认端口是3306
> database是连接的数据库(示例中是test)
> “root”和“123456”是数据库的用户名和密码
> rs = st.executeQuery("select * from person");执行SQL查询并返回结果
> ```

- 处理数据库返回结果
>![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111213738.png)

- 关闭数据库的连接
>![400](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111213750.png)
## 增删改查
### 增
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214006.png)
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214012.png)
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214016.png)
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214212.png)
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214229.png)
### 删
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214312.png)
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214418.png)
### 改
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214328.png)
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214448.png)
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214502.png)
### 查
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214536.png)
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214540.png)
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214604.png)
![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240111214615.png)
# XML
>XML是一种可扩展的标记语言，被设计用来传输和存储数据，是由万维网协会推出的一套数据交换标准。可以用于定义网页上的文档元素，以及复杂的表述和传输。
   
在目前的开发系统中，会有很多XML文件，如strus.xml、spring.xml、web.xml、server.xml以及自定义的XML文件

- XML与HTML类似，设计的宗旨是传输数据，它没有固定的标签体，需要自定义标签，也是一种自我描述的语言，可以储存数据和共享数据
- XML与HTML的主要差异在于：HTML用来显示数据，XML用来传输和存储数据；HTML用来显示信息，XML用来传输信息
- XML的最大特点是它的自我描述和任意扩展，当用其描述数据时，用户可以根据需要，组织符合- XML规范形式的任意内容，并且标签的名称也可以由用户指定
## XML用途
- 传输数据
> 通过XML可以在不同的系统之间传输数据，在开发过程中难免会遇到多个系统之间相互通信，且各系统的存储数据又是多种多样的情况，对于开发者而言，这些工作量是巨大的，通过转换为XML格式来传输数据可以减少传输数据时的复杂性，并且还可以具备通用性。
> 例如，目前流行的SOA协议、Web Service服务、json、Ajax等，其实都是利用XML数据格式在不同的系统之间交互数据
- 存储数据
> 利用XML来存储数据是其最基本的用途，因为它可以作为数据文件，所以当需要持久化保存数据时，可以利用XML数据格式进行存储，例如web.xml、struts.xml、spring.xml等
## XML的技术架构
- 数据定义Schema、DTD：XML数据文件按照一定的协议进行定义，有两种可遵循的定义规则，即DTD和Schema。
- 数据风格样式XSLT：XSLT是可扩展样式转换，使用XSLT可以将XML中存放的内容按照指定的样式转换为HTML页面。
- 解析XML文件工具：目前比较盛行的工具是使用dom、dom4j、SAX。
- 操作XML数据：目前将XML数据作为具体操作，其功能是由额外的程序实现的，一般采用Java比较多，也可以使用JavaScript。
## XML基本语法
- XML文档的基本结构
>XML文档首先必须要有XML文档的声明，如`<?xml version="1.0" encoding="UTF-8"?>`
- 标记必须闭合：在XML文档中，除XML声明外，所有元素都必须有结束标识，如果XML元素没有文本节点时，就采用自闭合的方式关闭节点，例如使用`</name>`的形式进行自闭合
- 必须合理嵌套
	```xml
	不合理嵌套
	<age>30<sex>
	</age>女</sex>
	
	合理嵌套
	<age>30</age>
	<sex>女</sex>
	```

- XML元素：XML元素是指成对标签出现的内容，且每个元素之间有层级关系。`<age>`元素是`<user>`元素的子元素，`<user>`元素是`<age>`元素的父元素，`<name>`元素与`<age>`元素是并联关系
	- 元素命名规则
		- 可以包含字母、数字和其他字符
		- 不能以xml开头
		- 不能以数字或者标点符号开头、不能包含空格
		- 除xml外，没有保留字，但应尽量使元素名字具有可读性
		- 尽量避免使用‘-’和‘.’，可能引起混乱
		- xml元素命名不要使用‘:’
- XML属性：XML元素可以在开始标签中包含属性，属性提供关于元素的额外信息，被定义在XML元素的标签中，且自身有对应的值。例如`<user language="java"></user>`
- 只有一个根元素：所有的XML文档有且只有一个根元素来定义整个文档。在web.xml代码中，可以看到`<web-app>`是它的根元素，不能出现2个
- 大小写敏感：XML文档是大小写敏感的，包括标签名称、属性名和属性值等。例如`<age>`与`<Age>`是不同的
- 空白被保留：空白被保留是指在XML文档中，空白部分并不会被解释器删除，而是被当作数据一样完整的保留
- 注释的写法
```
<!--注释单行-->
<!--
注释多行
-->
```
## 其他
- JDK中的XML API
	- The Java API For XML Processing：负责解析XML
	- Java Architecture for XML Binding：负责XML映射为Java对象
---
- 最常见的XML解析模型：
	- DOM（文档对象模型）是W3C组织推荐的处理XML的一种方式。它是一种基于对象的API，把XML内容加载到内存中，生成一个XML文档相对应的对象模型，根据对象模型，以树节点的方式对文档进行操作
	- SAX是另外一种解析XML文件的方法，虽然不是官方标准，但它是XML社区上的事实标准，大部分XML解析器都支持它。SAX与DOM不同的是，它不是一次性地将XML加载到内存中，而是从XML文件的开始位置进行解析，根据已定义好的事件处理器来决定当前解析的部分是否有必要存储
	- DOM4j是一个简单、灵活的开源库，前身是JDOM，DOM4j使用接口和抽象类的基本方法，并使用了大量的Collections类，提供一些替代方法以允许更好的性能或更直接的编码方法
---
- XML与Java类映射JAXB
>分别使用DOM、DOM4j和SAX这3种方法解析XML，可以从XML文件中获得想要的数据，这非常有用，但需要编写大量的代码，工作巨大。通过JAXB的API可以更加简单地获取XML数据和生成XML
>
>将XML中的元素与User类中的属性一一对应，那么XML数据与Java类的对应关系就是一种映射
---
- JAXB的工作原理
>JAXB映射主要由4个部分构成：schema、JAXB映射类、XML文档、Java对象。通过JAXB可以将Java对象转化为XML，也可以将XML转化为Java对象
# EL标签
>在JSP页面中，经常利用JSP表达式<%=变量或者表达式%>来输出声明的变量以及页面传递的参数，当变量很多的时候，书写这样的表达式会显得累赘，EL标签很好地解决了这个问题，它简化了表达式
## 语法
`${参数名}`

例如：${param.name}获得参数name值，等同于<%=request.getParameter(‘name’)%>











































