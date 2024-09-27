```xml
<!-- 将引入Hutool的所有模块 -->
<dependency>
    <groupId>cn.hutool</groupId>
    <artifactId>hutool-all</artifactId>
    <version>5.8.32</version>
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

# ❤ 工具类
## 💛 唯一键 IdUtil
<u>UUID</u> ：全球唯一识别码
```java
//生成的UUID是带-的字符串，类似于：a5c8a5e8-df2b-4706-bea4-08d0939410e3
String uuid = IdUtil.randomUUID();

//生成的是不带-的字符串，类似于：b17f24ff026d40949c85a24f4f375d42
String simpleUUID = IdUtil.simpleUUID();
```

---

<u>雪花算法</u> ：分布式系统中，需要使用全局唯一 ID，这个 ID 要简单，但是又能够按照时间有序生成
- 有终端机器的使用
	- `Snowflake getSnowflake(终端id，数据中心id)` 获取带有机器属性的 Snowflake 对象【范围是 0 - 31】
		- `long nextId()` 
		- `String nextIdStr()` 
- 简单使用
	- `long getSnowflakeNextId()` 
	- `String getSnowflakeNextIdStr()`

```java
// 有终端机器的使用
IdUtil.getSnowflake(23L, 110L).nextId()

// 简单使用
long id = IdUtil.getSnowflakeNextId();
String id = IdUtil.getSnowflakeNextIdStr();
```



## 💛 随机 Random
- `RandomUtil` 静态对象
	- `randomInt()` 获取随机的 int
	- `randomInt(int minInclude, int maxExclude)` 获得指定范围内的随机数
	- `randomString(int length)` 获得一个随机的 length 长度的字符串

```java
// 生成一个8位的随机数
String randomNumber = RandomUtil.randomString(8);
System.out.println("生成的8位随机数是：" + randomNumber);
```

### 💙 权重随机
根据对象的权重值，来 Random 对象

```java
// 1.构建权重对象WeightObj，将其加入list集合
List<WeightRandom.WeightObj<String>> weightList = Stream.of(
		// 第一个值是权重对象，第二个值是权重
		new WeightRandom.WeightObj<String>("A", 20),
		new WeightRandom.WeightObj<String>("B", 30),
		new WeightRandom.WeightObj<String>("C", 40),
		new WeightRandom.WeightObj<String>("D", 10)
).collect(Collectors.toList());

// 2.生成权重随机对象
WeightRandom<String> wr = RandomUtil.weightRandom(weightList);
  
int numA = 0, numB = 0, numC = 0, numD = 0;  
  
// 3.打印随机结果  
for (int i = 0; i < 1000; i++) {  
    switch (wr.next()) {  
        case "A":  
            numA++;  
            break;  
        case "B":  
            numB++;  
            break;  
        case "C":  
            numC++;  
            break;  
        case "D":  
            numD++;  
            break;  
    }  
}  
  
System.out.println("A:" + numA);  
System.out.println("B:" + numB);  
System.out.println("C:" + numC);  
System.out.println("D:" + numD);

---
A:210
B:315
C:375
D:100
```

## 💛 Base64
>[!hint] 在浏览器中打开 Base64 编码的图片
>直接在浏览器的地址栏中输入：`data:image/png;base64,` + base64编码数据

- 字节数组 -> base64
```java
byte[] byteArray = new byte[10];
String base64 = Base64.encode(byteArray);
```

## 💛 二维码 QrCodeUtil
>[!hint] 使用之前还要再引入 zxing 依赖
> ```xml
> \<dependency>
> 	\<groupId>com.google.zxing\</groupId>
> 	\<artifactId>core\</artifactId>
> 	\<version>3.5.3\</version>
> \</dependency>
> ```

### 生成二维码
- 自定义二维码参数 `QrConfig`【长，宽，二维码的颜色，背景颜色，边距 ……】，<u>这个参数可以作为后续生成二维码</u>
```java
// 设置长宽
QrConfig config = new QrConfig(300, 300);

// 设置边距，即二维码和背景之间的边距
config.setMargin(3);

// 设置前景色，即二维码颜色（青色）
config.setForeColor(Color.CYAN.getRGB());

// 附带logo
config.setImg("logo_small.jpg")
```

---

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
byte[] imageBytes = QrCodeUtil.generatePng("https://www.baidu.com", 300, 300);
String base64 = Base64.encode(imageBytes);
return base64;
```

### 识别二维码
```java
// decode 就是被识别出来的链接
String decode = QrCodeUtil.decode(FileUtil.file("d:/qrcode.jpg"));
```

## 💛 数字工具 NumberUtil
<u>计算</u> ：
- **加减乘除** ：支持任意数字的包装类，String
	- `NumberUtil.add` 加
	- `NumberUtil.sub` 减
	- `NumberUtil.mul` 乘
	- `NumberUtil.div` 除
		- `double div(double d, double dd, int scale)` 使用 d 除以 dd ，保留 scale 位小数
		- `double div(double d, flost ff, int scale)` 使用 d 除以 ff ，保留 scale 位小数
- **其他**
	- `multiple(int m, int n)` 最小公倍数

---

<u>保留小数</u> ：
- `BigDecimal round(数字n，精度s)` 保留数字 n 的后 s 位小数，支持 BigDecimal，Double，String
- `String roundStr(n, s)` 返回的是数字的字符串类型

---

<u>校验数字</u> ：
- `NumberUtil.isNumber` 是否为数字
- `NumberUtil.isInteger` 是否为整数
- `NumberUtil.isDouble` 是否为浮点数
- `NumberUtil.isPrimes` 是否为质数

## 💛 字符串 StrUtil
<u>判空</u> ：
- 单个
	- `isBlank()` / `isNotBlank()` 
	- `isEmpty()` / `isNotEmpty()` 
- 集合
	- `hasBlank(字符串数组)` 判断这个数组中是否有至少一个为 blank，如果是，则返回 true
	- `hasEmpty()`

## 💛 集合工具 CollUtil
<u>判空</u> ：
- `isEmpty()` 
- `isNotEmpty()` 



## 💛 旧 - 日期时间
<u>范围</u> ：
- `rangeToList(开始时间，结束时间，单位)` 获取到两个时间之间的时间集合
```java
List<DateTime> dateTimes = DateUtil.rangeToList(
        DateUtil.parse("2024-03-01"),
        DateUtil.parse("2024-05-01"),
        DateField.DAY_OF_YEAR
);
dateTimes.forEach(System.out::println);
```

## 💛 新 - 日期时间
<u>格式化</u> ：

- `parse(时间，时间的格式)` 
```java
LocalDateTime localDateTime2 = LocalDateTimeUtil.parse("2020-01-23 12:23:56", DatePattern.NORM_DATETIME_FORMATTER);
```

<u>偏移时间量</u> ：

- `offset(时间，偏移量，偏移单位)` 
```java
LocalDateTime localDateTime = LocalDateTime.of(2021, 1, 1, 0, 0, 30);
LocalDateTime offset = LocalDateTimeUtil.offset(  
        localDateTime,  
        -30,  
        ChronoUnit.MINUTES  
);
System.out.println(offset);

---
2020-12-31T23:30:30
```

---

<u>开始 / 结束</u> ：
- `LocalDateTime beginOfDay(时间)` 例如 "2020-01-23T00:00"
- `LocalDateTime endOfDay(时间)` 例如 "2020-01-23T23:59:59.999999999"

---

<u>时间间隔</u> ：
- `Duration between(开始时间，结束时间)` 计算时间差值

```java
LocalDateTime start = LocalDateTime.now();
LocalDateTime end = LocalDateTime.now()
		.plusDays(1)
		.plusHours(33);

Duration between = LocalDateTimeUtil.between(start, end);

System.out.println(between.toHours());
System.out.println(between.toMinutes());
System.out.println(between.toSeconds());
System.out.println(between.toMillis());

---
57
3420
205200
205200000
```

---

<u>判断范围</u> ：

- `isIn(需要判断的时间，开始时间点，结束时间点，是否包含开始时间，是否包含结束时间)` 判断某个时间是否在某个范围中
- `isSameDay(日期1，日期2)` 比较两个时间是否是同一天，~~支持 LocalDateTime，LocalDate~~
- `isWeekend(时间)` 判断这一天是否为周末，~~支持 LocalDateTime，LocalDate~~

```java
boolean in = LocalDateTimeUtil.isIn(  
        LocalDateTime.now(),  
        LocalDateTime.now().minusDays(1),  
        LocalDateTime.now().plusDays(1),  
        true,  
        true 
);
```

# ❤ Bean
Bean 就是有 setter，getter 的 Java 类

## 💛  Bean -> Bean
- Award 转 AwardBO
```java
Award award = Award.builder()
		.strategyId(1)
		.awardId(101)
		.awardKey("random_points")
		.awardTitle("随机积分")
		.awardCount(100)
		.awardRate(0.1f)
		.awardSort(1)
		.rules("rules")
		.build();

AwardBO awardBO = new AwardBO();

BeanUtil.copyProperties(award, awardBO);
System.out.println(awardBO);

---
AwardBO(strategyId=1, awardId=101, awardCount=100, awardRate=0.1)
```

---

- Award 对象集合转 AwardBO 对象集合
```java
List<Award> awards = Stream.of(
		Award.builder()
				.id(1).strategyId(1).awardId(101)
				.awardKey("random").awardConfig("random")
				.awardTitle("随机积分").awardSubtitle("副标题")
				.awardCount(100).awardRate(0.1f).awardSort(1)
				.rules("rules").createTime(LocalDateTime.now())
				.updateTime(LocalDateTime.now())
				.build(),
		Award.builder()
				.id(2).strategyId(1).awardId(102)
				.awardKey("random").awardConfig("config")
				.awardTitle("随机积分").awardSubtitle("副")
				.awardCount(100).awardRate(0.1f)
				.awardSort(1).rules("rules")
				.createTime(LocalDateTime.now())
				.updateTime(LocalDateTime.now())
				.build()
).toList();

List<AwardBO> awardBOs = BeanUtil.copyToList(awards, AwardBO.class);
awardBOs.forEach(System.out::println);

---
AwardBO(strategyId=1, awardId=101, awardCount=100, awardRate=0.1)
AwardBO(strategyId=1, awardId=102, awardCount=100, awardRate=0.1)
```

# ❤ 加密解密
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

# ❤ 断言 Assert
>[!hint] Java 原生的 Assert 的缺点
>断言 本意上是在调式时使用，而不是生产环境
>
>- assert 默认在程序运行时是关闭的，不会产生任何效果，只有在调试时会生效
>- assert 断言失败，程序将退出

- **判空**
	- `isNull` / `notNull` 是否为 null
	- `notEmpty` 不能为空，支持字符串，数组，集合 ……
	- `notBlank` 不能是空白字符串
- **判对错**
	- `isTrue` 必须为 true，否则抛出IllegalArgumentException异常
	- `state` 检查 Boolean 表达式，如果为 false ，则抛异常
- **判包含**
	- `notContain` 不能包含指定的子串
	- `noNullElements` 数组中不能包含 null 元素
- **判类关系**
	- `isInstanceOf` 必须是指定类的实例
	- `isAssignable` 必须是子类和父类关系

