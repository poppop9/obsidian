```xml
<dependency>
    <groupId>com.squareup.retrofit2</groupId>
    <artifactId>retrofit</artifactId>
    <version>2.11.0</version>
</dependency>
```

>[!quote] Retrofit 2
>Retrofit 2 可以将 HTTP API 转换为 Java 接口【~~这意味着可以使用 Java 接口来定义网络请求~~】，然后 Retrofit 会负责将这些接口调用转换为实际的 HTTP 请求
>
> - **类型安全**：由于通过 Java 接口来定义 HTTP 请求，这使得编译时就可以检查错误
> - **自动序列化**：可以自动将 Java 对象序列化为 JSON 请求体，以及将 JSON 格式的响应体反序列化为 Java 对象
> - **支持同步，异步请求**
> - **拦截器**：允许添加拦截器【~~在客户端与服务端之间~~】，用于处理认证、日志记录、缓存 ……



