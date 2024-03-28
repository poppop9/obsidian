$$
OkHttp 是一个高效的 HTTP 客户端，支持同步阻塞，异步回调
$$

# 同步
## 获取
>下载文件，打印文件头，以字符串形式打印响应正文

- 当响应体的正文 < 1MB，使用 `string()`
- 当响应体的正文 > 1MB，使用 `stream`

```java
private final OkHttpClient client = new OkHttpClient();

public void run() throws Exception {
Request request = new Request.Builder()
	.url("https://publicobject.com/helloworld.txt")
	.build();

try (Response response = client.newCall(request).execute()) {
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


