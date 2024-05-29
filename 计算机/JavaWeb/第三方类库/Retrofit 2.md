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

# 示例
- 编写一个接口
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

- 创建 Retrofit 实例，并用 Retrofit 实例生成接口的实现类对象，用接口的实现类对象生成 Call 对象，使用 Call 对象发起请求，获取到 Respn
```java
// 创建Retrofit实例
Retrofit retrofit = new Retrofit.Builder()
	// 设置访问的基础url，并以其作为前缀
    .baseUrl("https://api.github.com/")
    .build();

// 创建GitHubService服务实例
GitHubService service = retrofit.create(GitHubService.class);

// 传入用户名，生成Call对象
Call<List<Repo>> call = service.listRepos("octocat");
// 发起请求，拿到Response对象
Response<Object> response = call.execute();
System.out.println(response.body());
```

# 注解
## 请求方式
- HTTP
- GET
- POST
- PUT
- PATCH
- DELETE
- OPTIONS
- HEAD

```java
@GET("users/list")

// 可以在 URL 中指定查询参数
@GET("users/list?sort=desc")
```

## 请求 url
>[!hint] 请求的 url 可以在方法调用时传入，<u>并且还可以指定查询参数【~~?key=value~~】</u>

- `@Path("与url对应")`
- `@Query("查询参数")` 

```java
// {id} 参数会在方法调用时传入
@GET("group/{id}/users")
Call<List<User>> groupList(@Path("id") int groupId, @Query("sort") String sort);
```

## 请求正文
- `@Body` 指定一个对象作为 HTTP 请求的正文

```java
@POST("users/new")
Call<User> createUser(@Body User user);
```

它接受一个 `User` 对象作为参数，这个参数将被用作请求的正文
    
    
3. **If no converter is added, only RequestBody can be used.** 如果开发者没有为 Retrofit 实例添加转换器，那么只能使用 `RequestBody` 类型的对象。`RequestBody` 是 Retrofit 中的一个抽象类，它需要一个具体的实现来指定如何将对象转换为请求正文

# 适配器
```xml
<dependency>
    <groupId>com.squareup.retrofit2</groupId>
    <artifactId>adapter-rxjava3</artifactId>
    <version>2.11.0</version>
</dependency>
```


# 转换器
可以为 Retrofit 实例添加转换器，使得 Retrofit 能够自动将 Java 对象转换为 JSON 格式，用于 HTTP 请求的正文

```xml
<dependency>
    <groupId>com.squareup.retrofit2</groupId>
    <artifactId>converter-jackson</artifactId>
    <version>2.11.0</version>
</dependency>
```
