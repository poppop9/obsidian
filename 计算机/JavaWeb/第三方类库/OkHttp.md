$$
OkHttp 是一个高效的 HTTP 客户端，支持同步阻塞，异步回调
$$

```xml
<dependency>
    <groupId>com.squareup.okhttp3</groupId>
    <artifactId>okhttp</artifactId>
    <version>5.0.0-alpha.12</version>
</dependency>
```

# 同步
## Get，获取响应
- 创建 OKHttp 实例，用于发送请求 `OkHttpClient client = new OkHttpClient(); `
- 构建 **Request 对象** `Request request = new Request.Builder() `
	- `url()` 访问的 url
	- `header(name, value)` 添加请求头，会覆盖已有 name 的 value 值
	- `addHeader(name, value)` 添加请求头，不会移除已有的头信息
	- `build()` 完成构建
- 发起同步请求，并获取到 **Response 结果** `Response response = client.newCall(request).execute()`
	- `isSuccessful()` 判断请求是否成功【200 - 299】
	- `header(name)` 返回 name 的最后一个 value，response.header("Server")
	- `headers(name)` 以列表形式读取某个 name 的所有 value
	- `headers()` 获取 Response 对象的头部信息
		- `size()` 头部信息的个数
		- `name(索引)` 头部信息的名称
		- `value(索引)` 头部信息的值
	- `body()` 响应体

```java
// 创建 OkHttpClient 实例
private final OkHttpClient client = new OkHttpClient();  
  
@Test  
public void QueryUnanswered() throws IOException {  
	// 创建 Request 对象并添加请求头
    Request request = new Request.Builder()  
            .url("https://api.zsxq.com/v2/groups/15555541222422/topics?scope=all&count=20")  
            .addHeader("cookie", "……")  
            .addHeader("Content-type", "application/json; charset=UTF-8")  
            .build();  

	// 发起请求并处理响应
    try (Response response = client.newCall(request).execute()) {  
	    // 如果响应不成功，则抛出异常
        if (!response.isSuccessful()) throw new IOException("Unexpected code " + response);  

		// 获取到响应对象的响应头
        Headers responseHeaders = response.headers();  
        for (int i = 0; i < responseHeaders.size(); i++) {  
            System.out.println(responseHeaders.name(i) + ": " + responseHeaders.value(i));  
        }  
  
        System.out.println(response.body().string());  
    }
}
```

>[!hint]
> - 当响应体的内容 < 1MB，使用 `string()`
> - 当响应体的内容 > 1MB，使用 `stream`

## Post 小内容
- ……
- `Request`
	- `post(请求的媒体类型, 内容)` 

```java
// 表示请求的媒体类型为 Markdown 格式
public static final MediaType MEDIA_TYPE_MARKDOWN = MediaType.parse("text/x-markdown; charset=utf-8");
    
private final OkHttpClient client = new OkHttpClient();

public void run() throws Exception {
    String postBody = "" +
        "Releases\n" +
        "--------\n" +
        "\n" +
        " * _1.0_ May 6, 2013\n" +
        " * _1.1_ June 15, 2013\n" +
        " * _1.2_ August 11, 2013\n";

	// 使用 RequestBody.create 方法创建请求体，指定了请求的媒体类型和内容
    Request request = new Request.Builder()
        .url("https://api.github.com/markdown/raw")
        .post(RequestBody.create(MEDIA_TYPE_MARKDOWN, postBody))
        .build();
        
    try (Response response = client.newCall(request).execute()) {
        if (!response.isSuccessful()) throw new IOException("Unexpected code " + response);
        System.out.println(response.body().string());
    }
}
```

## Post 大内容
```java
public static final MediaType MEDIA_TYPE_MARKDOWN = MediaType.parse("text/x-markdown; charset=utf-8");

private final OkHttpClient client = new OkHttpClient();

public void run() throws Exception {
    RequestBody requestBody = new RequestBody() {
	    // 定义请求体的媒体类型
        @Override public MediaType contentType() {
            return MEDIA_TYPE_MARKDOWN;
        }

		// 内容写入
        @Override public void writeTo(BufferedSink sink) throws IOException {
            sink.writeUtf8("Numbers\n");
            sink.writeUtf8("-------\n");
            for (int i = 2; i <= 997; i++) {
                sink.writeUtf8(String.format(" * %s = %s\n", i, factor(i)));
            }
        }

		// 创建 factor() 函数，用于上面内容写入
        private String factor(int n) {
            for (int i = 2; i < n; i++) {
                int x = n / i;
                if (x * i == n) return factor(x) + " × " + i;
            }
            return Integer.toString(n);
        }
    };
    
    Request request = new Request.Builder()
        .url("https://api.github.com/markdown/raw")
        .post(requestBody)
        .build();
        
    try (Response response = client.newCall(request).execute()) {
        if (!response.isSuccessful()) throw new IOException("Unexpected code " + response);
        System.out.println(response.body().string());
    }
}
```

## 发布文件
```java
public static final MediaType MEDIA_TYPE_MARKDOWN
    = MediaType.parse("text/x-markdown; charset=utf-8");
private final OkHttpClient client = new OkHttpClient();
public void run() throws Exception {
    File file = new File("README.md");
    Request request = new Request.Builder()
        .url("https://api.github.com/markdown/raw")
        .post(RequestBody.create(MEDIA_TYPE_MARKDOWN, file))
        .build();
    try (Response response = client.newCall(request)
        .execute()) {
        if (!response.isSuccessful()) throw new IOException("Unexpected code " + response);
        System.out.println(response.body()
            .string());
    }
}

```





# 异步
## 概述
- 发起异步请求 `client.newCall(request).enqueue(new Callback() {……});`
- 在 `{……}` 中添加回调函数
	- 失败时被调用 `onFailure(Call, IOException) {……}`
	- 接收到响应时被调用 `onResponse(Call, Response) {……}`

## get，获取响应
```java
private final OkHttpClient client = new OkHttpClient();

public void run() throws Exception {
    Request request = new Request.Builder()
        .url("http://publicobject.com/helloworld.txt")
        .build();

    // 将请求放入队列中，并设置一个回调函数来处理响应结果
    client.newCall(request)
        .enqueue(new Callback() {
            // 定义了回调函数中的 onFailure 方法，请求失败时被调用，Call 对象表示当前请求
            @Override public void onFailure(Call call, IOException e) {
                e.printStackTrace();
            }

            // 定义了回调函数中的 onResponse 方法，在接收到响应时被调用
            @Override public void onResponse(Call call, Response response) throws IOException {
                try (ResponseBody responseBody = response.body()) {
                    if (!response.isSuccessful()) throw new IOException("Unexpected code " + response);
                    Headers responseHeaders = response.headers();
                    for (int i = 0, size = responseHeaders.size(); i < size; i++) {
                        System.out.println(responseHeaders.name(i) + ": " + responseHeaders.value(i));
                    }
                    System.out.println(responseBody.string());
                }
            }
        });
}
```