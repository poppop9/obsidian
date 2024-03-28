$$
OkHttp 是一个高效的 HTTP 客户端，支持同步阻塞，异步回调
$$

# 同步
## 概述
- 创建 OKHttp 实例，用于发送请求 `OkHttpClient client = new OkHttpClient(); `
- 构建 **Request 对象** `Request request = new Request.Builder() `
	- `url()` 访问的 url
	- `addHeader()` 添加请求头
	- `build()` 完成构建
- 发起同步请求，并获取到 **Response 结果** `Response response = client.newCall(request).execute()`
	- `isSuccessful()` 判断请求是否成功【200 - 299】
	- `headers()` 获取 Response 对象的头部信息
		- `size()` 头部信息的个数
		- `name(索引)` 头部信息的名称
		- `value(索引)` 头部信息的值
	- `body()` 响应体

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

		// 获取到响应对象的响应头
        Headers responseHeaders = response.headers();  
        for (int i = 0; i < responseHeaders.size(); i++) {  
            System.out.println(responseHeaders.name(i) + ": " + responseHeaders.value(i));  
        }  
  
        System.out.println(response.body().string());  
    }
}
```




# 异步
## 概述
- 发起异步请求 `client.newCall(request).enqueue(new Callback() {……});`
- 在 `{……}` 中添加回调函数
	- 失败时被调用 `onFailure(Call, IOException) {……}`
	- 接收到响应时被调用 `onResponse(Call, Response) {……}`

## 获取
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