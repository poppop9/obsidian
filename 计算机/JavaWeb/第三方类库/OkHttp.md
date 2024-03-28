$$
OkHttp 是一个高效的 HTTP 客户端，支持同步阻塞，异步回调
$$

# 概述
## 请求步骤
- 创建 OKHttp 实例，用于发送请求 `OkHttpClient client = new OkHttpClient(); `
- 构建 Request 对象 `Request request = new Request.Builder() `
	- `url()` 访问的 url
	- `addHeader()` 添加请求头
	- `build()` 完成构建
- 发起请求，并获取到 Response 结果 `Response response = client.newCall(request).execute()`
	- `isSuccessful()` 判断


# 同步
## 获取
>下载文件，打印文件头，以字符串形式打印响应正文

>[!hint]
> - 当响应体的正文 < 1MB，使用 `string()`
> - 当响应体的正文 > 1MB，使用 `stream`

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
  
        Headers responseHeaders = response.headers();  
        for (int i = 0; i < responseHeaders.size(); i++) {  
            System.out.println(responseHeaders.name(i) + ": " + responseHeaders.value(i));  
        }  
  
        System.out.println(response.body().string());  
    }
}
```
















# 异步


