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

- 创建 Retrofit 实例，并用 Retrofit 实例生成接口的实现类对象，用接口的实现类对象生成 Call 对象，使用 Call 对象发起请求，获取到 Response 对象
```java
// 创建Retrofit实例
Retrofit retrofit = new Retrofit.Builder()
	// 设置访问的基础url，并以其作为前缀
    .baseUrl("https://api.github.com/")
    // 这个client是使用OKHttp创建的OkHttpClient对象
    .client(client)
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

## 请求头
- `@Headers` 为方法设置头信息

```java
// 设置一个
@Headers("Cache-Control: max-age=640000")
@GET("widget/list")
Call<List<Widget>> widgetList();

// 设置多个
@Headers({
    "Accept: application/vnd.github.v3.full+json",
    "User-Agent: Retrofit-Sample-App"
})
@GET("users/{username}")
Call<User> getUser(@Path("username") String username);
```

---

- `@Header` 在方法调用时，动态传入头信息

```java
@GET("user")
Call<User> getUser(@Header("Authorization") String authorization)
```

---

- `@HeaderMap` 在方法调用时，动态传入一组头信息【~~对于复杂的请求头~~】
```java
@GET("user")
Call<User> getUser(@HeaderMap Map<String, String> headers)
```

## 请求正文
- `@Body` 指定一个对象作为 HTTP 请求的正文【~~需要与转换器搭配使用~~】

```java
@POST("users/new")
Call<User> createUser(@Body User user);
```

## 表单数据
>[!hint] application/x-www-form-urlencoded 与 multipart/form-data
>- `application/x-www-form-urlencoded` 
>	- 这是一种简单的文本格式，易于解析
>	- 只能用于非文件数据，不支持文件数据
>	- 传输效率高
>	- 兼容性好
>- `multipart/form-data` 
>	- 支持文件上传
>	- 可以传输的数据量更大

### application/x-www-form-urlencoded
- `@FormUrlEncoded` 指示该方法的请求体应该被编码为表单数据，每个键值对都使用 `@Field`
- `@Field` 用于指定表单中的单个键值对

```java
@FormUrlEncoded
@POST("user/edit")
Call<User> updateUser(@Field("first_name") String first, @Field("last_name") String last);
```

### multipart/form-data
- `@Multipart` 指示该方法的请求体应该被编码为 `multipart/form-data` ，Retrofit 会构造一个多部分请求，其中每个部分都由 `@Part` 定义
- `@Part` 每个 `@Part` 都对应请求体中的一个单独部分【~~可以包含文件，文本 ……~~】

```java
@Multipart
@PUT("user/photo")
Call<User> updateUser(@Part("photo") RequestBody photo, @Part("description") RequestBody description);
```

# 转换器
```xml
<dependency>
    <groupId>com.squareup.retrofit2</groupId>
    <artifactId>converter-jackson</artifactId>
    <version>2.11.0</version>
</dependency>
```

Retrofit 在默认情况下，会将服务器返回的 HTTP 响应体【~~JSON，XML ……~~】转换成 OkHttp 的 `ResponseBody` ，所以当请求体是 Java 对象，或是表单字段 ……，需要为 Retrofit 实例添加转换器，使得 Retrofit 能够自动将 Java 对象转换为 JSON 格式

```java
Retrofit retrofit = new Retrofit.Builder()  
        .baseUrl("https://pay.gm-pay.net/")  
        .client(client)  
        // 添加转换器
        .addConverterFactory(JacksonConverterFactory.create())  
        .build();
```

# 适配器
```xml
<dependency>
    <groupId>com.squareup.retrofit2</groupId>
    <artifactId>adapter-rxjava3</artifactId>
    <version>2.11.0</version>
</dependency>
```

# 同步异步
每个 `Call` 对象在执行一次请求后就会被消耗掉，不能再次使用。如果你需要再次发起相同的请求，需要重新创建一个新的 `Call` 对象。

但是，可以通过调用 `Call` 对象的 `clone()` 方法来创建一个新的 `Call` 实例，这个新实例可以用于发起新的请求

>[!hint] 在 JVM 上，回调将在执行 HTTP 请求的同一线程上进行
> 当你使用 Retrofit 的异步调用（通过回调函数）时，回调函数会在发起 HTTP 请求的同一个线程上被执行。也就是说，如果请求是在主线程发起的，那么回调也会在主线程上执行
> 
> 这通常不是我们想要的行为，因为网络请求通常需要一些时间，如果在主线程上同步执行，可能会导致界面冻结或无响应。因此，通常我们会在异步线程上执行网络请求，并在主线程上更新 UI 或处理结果
> 
> 为了安全地在主线程上更新 UI 或处理结果，通常会结合使用 `Executor` 来控制回调函数的执行线程。例如，Retrofit 2 允许你通过 `@MainThread` 或 `@WorkerThread` 注解来指定回调函数的执行线程，或者通过自定义 `Executor` 来控制。
