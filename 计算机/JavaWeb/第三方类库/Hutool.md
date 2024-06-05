```xml
<!-- 将引入Hutool的所有模块 -->
<dependency>
    <groupId>cn.hutool</groupId>
    <artifactId>hutool-all</artifactId>
    <version>5.8.27</version>
</dependency>
```

对文件、流、加密解密、转码、正则、线程、XML等 JDK 方法进行封装

|模块|介绍|
|---|---|
|hutool-aop|JDK动态代理封装，提供非IOC下的切面支持|
|hutool-bloomFilter|布隆过滤，提供一些Hash算法的布隆过滤|
|hutool-cache|简单缓存实现|
|hutool-core|核心，包括Bean操作、日期、各种Util等|
|hutool-cron|定时任务模块，提供类Crontab表达式的定时任务|
|hutool-crypto|加密解密模块，提供对称、非对称和摘要算法封装|
|hutool-db|JDBC封装后的数据操作，基于ActiveRecord思想|
|hutool-dfa|基于DFA模型的多关键字查找|
|hutool-extra|扩展模块，对第三方封装（模板引擎、邮件、Servlet、二维码、Emoji、FTP、分词等）|
|hutool-http|基于HttpUrlConnection的Http客户端封装|
|hutool-log|自动识别日志实现的日志门面|
|hutool-script|脚本执行封装，例如Javascript|
|hutool-setting|功能更强大的Setting配置文件和Properties封装|
|hutool-system|系统参数调用封装（JVM信息等）|
|hutool-json|JSON实现|
|hutool-captcha|图片验证码实现|
|hutool-poi|针对POI中Excel和Word的封装|
|hutool-socket|基于Java的NIO和AIO的Socket封装|
|hutool-jwt|JSON Web Token (JWT)封装实现|

# 工具类
## 随机 Random
- `RandomUtil` 静态对象
	- `randomInt()` 获取随机的 int
	- `randomInt(int minInclude, int maxExclude)` 获得指定范围内的随机数
	- `randomString(int length)` 获得一个随机的 length 长度的字符串

```java
// 生成一个8位的随机数
String randomNumber = RandomUtil.randomString(8);
System.out.println("生成的8位随机数是：" + randomNumber);
```

## Base64
>[!hint] 在浏览器中打开 Base64 编码的图片
>直接在浏览器的地址栏中输入：`data:image/png;base64,` + base64编码数据


## 二维码 QrCodeUtil
>[!hint] 使用之前还要再引入 zxing 依赖
> ```xml
> \<dependency>
> 	\<groupId>com.google.zxing\</groupId>
> 	\<artifactId>core\</artifactId>
> 	\<version>3.5.3\</version>
> \</dependency>
> ```

- URL -> 二维码图片
```java
QrCodeUtil.generate("https://hutool.cn/", 300, 300, FileUtil.file("d:/qrcode.jpg"));
```

- URL -> `BufferedImage` 图片对象
```java
String url = "https://www.baidu.com";
// 设置二维码的宽和高
QrConfig config = new QrConfig(300, 300);
// 生成二维码图片
BufferedImage qrImage = QrCodeUtil.generate(url, config);
```

- URL -> `byte[]` 格式的 PNG 二维码图片
```java
String url = "https://www.baidu.com";
byte[] imageBytes = QrCodeUtil.generatePng(url, 300, 300);
String base64 = Base64.encode(imageBytes);
return base64;
```

- URL -> 图片 -> 输出流 -> base64
```java
public static String urlToBase64(String url) {
	// 设置二维码的宽和高
	QrConfig config = new QrConfig(300, 300);
	// 生成二维码图片
	BufferedImage qrImage = QrCodeUtil.generate(url, config);
	// 输出流
	ByteArrayOutputStream outputStream = new ByteArrayOutputStream();

	try {
		// 将图片写入字节输出流
		ImgUtil.writePng(qrImage, outputStream);
		// 生成base64编码
		String base64 = Base64.encode(outputStream.toByteArray());
		// 将字节输出流转换为Base64编码字符串
		return base64;
	} finally {
		try {
			outputStream.close();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```


# 加密解密
>[!quote] 加密分类
>- **对称加密**
> 	- AES
> 	- ARCFOUR
> 	- Blowfish
> 	- DES
> 	- DESede
> 	- RC2
> 	- PBEWithMD5AndDES
> 	- PBEWithSHA1AndDESede
> 	- PBEWithSHA1AndRC2_40
> - **非对称加密**
> 	- RSA
> 	- DSA
> - **摘要加密**
> 	- MD2
> 	- MD5
> 	- SHA-1
> 	- SHA-256
> 	- SHA-384
> 	- SHA-512
> 	- HmacMD5
> 	- HmacSHA1
> 	- HmacSHA256
> 	- HmacSHA384
> 	- HmacSHA512

## 常见加密 SecureUtil
- 对称加密
	- `SecureUtil.aes`
	- `SecureUtil.des`
- 摘要加密
	- `String SecureUtil.md5`
		- `SecureUtil.md5()`
		- `SecureUtil.md5(File dataFile)` 加密文件，生成 16 进制 MD5 字符串
		- `SecureUtil.md5(InputStream data)`
		- `SecureUtil.md5(String data)`
	- `SecureUtil.sha1`
	- `SecureUtil.hmac`
	- `SecureUtil.hmacMd5`
	- `SecureUtil.hmacSha1`
- 非对称加密
	- `SecureUtil.rsa`
	- `SecureUtil.dsa`
- UUID
	- `SecureUtil.simpleUUID` 方法提供无“-”的UUID
- 密钥生成
	- `SecureUtil.generateKey` 针对对称加密生成密钥
	- `SecureUtil.generateKeyPair` 生成密钥对（用于非对称加密）
	- `SecureUtil.generateSignature` 生成签名（用于非对称加密）

```java
String stringSignTemp = "AAA";  
String MD5 = SecureUtil.md5(stringSignTemp);
```




