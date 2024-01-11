第一章
~~第二章~~
三，注释生命，指令，动作
四，
五，√√√
六，javabean的生命周期
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




























