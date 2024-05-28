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

```java
public interface GitHubService {
	// `{user}` 是一个路径参数，它将在调用时替换为具体的用户名
	@GET("users/{user}/repos")
	// `Repo` 是一个自定义类，用于表示GitHub上的仓库信息
	// listRepos方法接受一个用户名作为参数
	Call<List<Repo>> listRepos(@Path("user") String user);
}

// 总结：定义了一个api规范，根据后续实现类的baseUrl，拼接上 ‘users/{user}/repos’ ，其中的 ‘{user}’ 参数在调用时传入
```

```java
// 该 Retrofit 类生成 GitHubService 接口的实现
Retrofit retrofit = new Retrofit.Builder()
    .baseUrl("https://api.github.com/")
    .build();

GitHubService service = retrofit.create(GitHubService.class);

Call<List<Repo>> repos = service.listRepos("octocat");
```


- `Retrofit` 类用于构建和配置Retrofit客户端。
- `new Retrofit.Builder()` 创建一个新的Retrofit构建器。
- `.baseUrl("https://api.github.com/")` 设置API的基础URL，所有请求都会以这个URL作为前缀。
- `.build()` 构建并返回一个配置好的Retrofit实例。


