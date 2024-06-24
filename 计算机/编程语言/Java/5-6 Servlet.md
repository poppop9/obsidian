
# HttpServletRequest
>[!quote] `HttpServletRequest`
>`HttpServletRequest` 代表客户端对 Servlet 的请求，提供了获取请求信息的方法【头信息，参数，cookies，URI ……】


# HttpServletResponse
>[!quote] `HttpServletResponse` 
>`HttpServletResponse` 允许 Servlet 向客户端制定 HTTP 响应，可以使用它设置响应头，状态码，发送错误响应 ……

- `setContentType(……)` 设置响应体的内容类型
- `getWriter()` 返回一个可以向客户端发送文本数据的 `PrintWriter` 对象
	- `println()` 将参数中的字符串，加上一个换行符，然后发送给客户端

```java
String jsonData = "……";

response.setContentType("application/json;charset=utf-8");
response.getWriter().println(jsonData);
```


