引入 Redis 主要就是两方面的作用：
- <u>用作缓存</u>，比较简单，所有框架差距不大
- <u>用作分布式锁</u>，Redisson 的分布式锁功能比较完善，有很多功能不用手写，有现成的直接用【RedLock 算法，读写锁，上锁后自动续期的 watchDog】

>[!hint] 技术选型
>- `Jedis` 
>- `Lettuce`
>- `Redisson` 基于 NIO【~~非阻塞的~~】 的 netty 框架

```xml
<dependency>
    <groupId>org.redisson</groupId>
    <artifactId>redisson-spring-boot-starter</artifactId>
    <version>3.32.0</version>
</dependency>
```

---

- [教程1](https://blog.csdn.net/A_art_xiang/article/details/125525864?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171964322916800222820133%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171964322916800222820133&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-125525864-null-null.142^v100^pc_search_result_base5&utm_term=redisson&spm=1018.2226.3001.4187) 非常全面
- [简化教程](https://blog.csdn.net/black_pp/article/details/131836775?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171964322916800222820133%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171964322916800222820133&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-131836775-null-null.142^v100^pc_search_result_base5&utm_term=redisson&spm=1018.2226.3001.4187) 
- [精化教程](https://www.cnblogs.com/xfeiyun/p/17795581.html)

# 配置
- 添加 redis 配置
```yml
# Redis  
redis:  
  sdk:  
    config:  
      host: 127.0.0.1  
      port: 6379  
      pool-size: 10  
      min-idle-size: 5  
      idle-timeout: 30000  
      connect-timeout: 5000  
      retry-attempts: 3  
      retry-interval: 1000  
      ping-interval: 60000  
      keep-alive: true
```

- 添加配置类 `RedissonConfig` 
```java
package app.xlog.ggbond.config;  

@Configuration  
public class RedissonConfig {  
    @Bean  
    public RedissonClient redissonClient() {  
        Config config = new Config();  
  
        //设置redis的地址，这里是单机模式  
        config.useSingleServer()  
                .setAddress("redis://127.0.0.1:6379")  
//                .setPassword(……)  
                // 设置连接池的大小，默认为64  
                .setConnectionPoolSize(64)  
                // 设置连接池的最小空闲连接数，默认为10  
                .setConnectionMinimumIdleSize(10)  
                // 设置连接的最大空闲时间（单位：毫秒），超过该时间的空闲连接将被关闭，默认为10000  
                .setIdleConnectionTimeout(10000)  
                // 设置连接超时时间（单位：毫秒），默认为10000  
                .setConnectTimeout(10000)  
                // 设置连接重试次数，默认为3  
                .setRetryAttempts(3)  
                // 设置连接重试的间隔时间（单位：毫秒），默认为1000  
                .setRetryInterval(1000)  
                // 设置定期检查连接是否可用的时间间隔（单位：毫秒），默认为0，表示不进行定期检查  
                .setPingConnectionInterval(0)  
                // 设置是否保持长连接，默认为true  
                .setKeepAlive(true);  
                
	    // 设置Redisson存储数据的格式，这里使用Json，一定要配置，防止乱码 
		config.setCodec(new JsonJacksonCodec());
  
        return Redisson.create(config);  
    }  
}
```

# 使用
## 💛 Key
- redissonClient 下的方法
	- `RKeys getKeys();` 返回 RKeys 对象

---

- RKeys 下的方法
	- **删**
		- `delete(键 ……)` 单/多删
		- `deleteByPattern()` 模糊删
	- **查**
		- `getKeys()` 返回所有 key 集合
		- `getKeysByPattern(模糊匹配)` 根据模糊匹配条件，返回所有 key 集合
			- `*` 匹配 0 个或多个字符
			- `?` 匹配单个字符
			- `[]` 匹配指定字符范围内的单个字符
		- `randomKey()` 随机获取 key
		- `count()` 统计 key 的数量
		- `countExists(键)` 判断 key 是否存在

---

```java
@Autowired  
private RedissonClient redissonClient;

@Test
public void testRedisson() {
	RKeys keys = redissonClient.getKeys();
	//获取所有key值
	keys.getKeys().forEach(System.out::println);
	System.out.println("====================================");

	//模糊获取key值
	keys.getKeysByPattern("*sys*").forEach(System.out::println);

	// 删除key
	keys.delete("sys1111", "2222_sys2222");

	// 判断key是否存在
	System.out.println(keys.countExists("awards"));

	// 获取key的数量
	System.out.println(keys.count());
}
```

## 💛 字符串 / 对象
- redissonClient 下的方法
	- `getBucket(键)` 获取对应 key 的 RBucket 对象
- RBucket 对象下的方法
	- `set(值)` 设置 value，如果 key 存在则覆盖
	- `trySet(值)` 设置 value，<u>如果 key 存在则不做任何操作</u>
	- **删**
		- `delete()` 删除键值对
	- **查**
		- `get()` 查询 key 对应的 value
		- `isExists()` 判断 RBucket 对象是否存在【~~不能直接通过是否为 null 来判断，因为即使不存在对应的 key，查出来的 RBucket 对象也不为 null~~】

---

- 字符串
```java
// 使用myStringKey作为key，创建bucket对象
RBucket<String> bucket = redissonClient.getBucket("myStringKey");

// 存储字符串
bucket.set("Hello, Redisson!");

// 获取字符串
System.out.println("Stored value: " + bucket.get());
```

- 对象
```java
TestUser testUser = new TestUser(1, "harvey", 32);
TestUser testUser2 = new TestUser(2, "tom", 32);

//用TestUser的id作为key
RBucket<TestUser> bucket = redissonClient.getBucket("user:id:" + testUser.getId());
bucket.set(testUser);

//删除
RBucket<TestUser> bucket3 = redissonClient.getBucket("user:id:" + testUser.getId());
System.out.println(bucket3.delete());
```

### 💙 批量处理
```java
// 创建 Buckets
RBuckets buckets = redissonClient.getBuckets();

// 创建map集合，存储键值对
Map<String, TestUser> userMap = new HashMap<>();
userMap.put("user:id:" + testUser.getId(), testUser);
userMap.put("user:id:" + testUser2.getId(), testUser2);

buckets.set(userMap);

// 批量获取 value
Map<String, TestUser> bucketsMap = buckets.get("user:id:" + testUser.getId(), "user:id:" + testUser2.getId());

System.out.println(bucketsMap);
```

## 💛  列表 List
- RedissonClient 下的方法
	- `getList(键)` 生成 RList 对象
- RList 下的方法
	- `add(值)` 向 List 中添加值
	- `addAll(集合)` 批量添加

>[!hint] 可以直接把 `RList` 看成 Java 里的 `List 集合`

---

```java
// 构建集合
List<AwardBO> AwardBOs = Stream.of(
		new AwardBO(1, 1, 1, 0.1f),
		new AwardBO(1, 2, 1, 0.2f),
		new AwardBO(1, 3, 1, 0.3f)
).toList();

// 生成 RList
RList<Object> rList = redissonClient.getList("testList");

rList.addAll(AwardBOs);

rList.forEach(System.out::println);
```

## 💛  哈希
```java
@Autowired  
private RedissonClient redissonClient;

// 会在redis中创建名为awards的HASH数据结构，然后存储以下三个数据
@Test
public void testRedisson() {
	RMap<String, String> rMap = redissonClient.getMap("awards");
	rMap.put("101", "随机积分");
	rMap.put("102", "淘宝优惠券");
	rMap.put("103", "京东优惠券");

	// 通过key获取value
	System.out.println(redissonClient.getMap("awards").get("102"));
}

---
淘宝优惠券
```

## 💛  布隆过滤器
>[!quote] 布隆过滤器
>布隆过滤器 用于检索一个元素是否在一个集合中
>
>- 空间效率，和查询时间都比一般的算法要好的多
>- 有一定的误识别率，而且删除困难


```java
@Autowired  
private RedissonClient redissonClient;

@Test
public void testRBloomFilter() {
	RBloomFilter rBloomFilter = redissonClient.getBloomFilter("seqId");
	// 初始化预期插入的数据量为10000，和期望误差率为0.01
	rBloomFilter.tryInit(10000, 0.01);
	
	// 插入部分数据
	rBloomFilter.add("100");
	rBloomFilter.add("200");
	rBloomFilter.add("300");
	
	//设置过期时间
	rBloomFilter.expire(30, TimeUnit.SECONDS);
	
	// 判断是否存在
	System.out.println(rBloomFilter.contains("300"));
	System.out.println(rBloomFilter.contains("200"));
	System.out.println(rBloomFilter.contains("999"));
}
```









