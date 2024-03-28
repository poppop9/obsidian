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

## Post 发布文件
```java
public static final MediaType MEDIA_TYPE_MARKDOWN = MediaType.parse("text/x-markdown; charset=utf-8");

private final OkHttpClient client = new OkHttpClient();

public void run() throws Exception {
    File file = new File("README.md");
    
    Request request = new Request.Builder()
        .url("https://api.github.com/markdown/raw")
        .post(RequestBody.create(MEDIA_TYPE_MARKDOWN, file))
        .build();
        
    try (Response response = client.newCall(request).execute()) {
        if (!response.isSuccessful()) throw new IOException("Unexpected code " + response);
        System.out.println(response.body().string());
    }
}

```

## Post 表单参数
使用 `FormBody.Builder()` 生成请求体

```java
private final OkHttpClient client = new OkHttpClient();

public void run() throws Exception {
	// search 参数，Jurassic Park 值
    RequestBody formBody = new FormBody.Builder()
        .add("search", "Jurassic Park")
        .build();
        
    Request request = new Request.Builder()
        .url("https://en.wikipedia.org/w/index.php")
        .post(formBody)
        .build();
        
    try (Response response = client.newCall(request).execute()) {
        if (!response.isSuccessful()) throw new IOException("Unexpected code " + response);
        System.out.println(response.body().string());
    }
}
```

## Post 复杂数据
我们可以使用 `MultipartBody.Builder` 【箱子】，里面放各种的请求体【文件，文本……】

并可定义自己的标头。如果存在，这些标头应描述该部分正文，如其 Content-Disposition。如果有 Content-Length 和 Content-Type 标头，则会自动添加。

如何使用 MultipartBody.Builder 来构建复杂的请求体，以便与 HTML 文件上传表单兼容。在 multipart 请求体中的每个部分本身都是一个请求体，并且可以定义自己的头信息。如果存在的话，这些头信息应该描述部分主体，比如它的 Content-Disposition。如果可用的话，Content-Length 和 Content-Type 头信息会被自动添加。

当你需要向服务器发送一个包含文件上传等复杂数据的请求时。MultipartBody.Builder 就像是你在准备这个包裹的箱子，你可以往里面放入各种不同的东西（比如文件、文本等），每样东西都有自己的标签（头信息），告诉收件人这个东西是什么，该怎么处理。

每个东西（部分）都是这个箱子（请求体）的一部分，而这些标签（头信息）会告诉服务器如何处理这些东西。如果有必要的话，还会自动添加一些标签，比如内容长度和内容类型。这样，你就可以将复杂的数据打包发送给服务器，让通信更加顺畅有效，就像寄快递一样简单明了。希望这样说能让你更容易理解！

简单来说，当需要向服务器发送包含文件上传等复杂数据的请求时，可以使用 MultipartBody.Builder 构建请求体。每个部分都可以具有自己的头信息，用于描述该部分的内容类型、长度等信息。这种方式可以使请求体更加灵活，能够处理各种类型的数据上传需求，并且根据数据内容自动生成一些必要的头信息，如 Content-Length 和 Content-Type。这样就可以更方便地与服务器进行通信，实现文件上传等功能。



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