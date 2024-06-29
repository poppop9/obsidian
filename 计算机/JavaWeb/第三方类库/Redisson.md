引入 Redis 主要就是两方面的作用：
- <u>用作缓存</u>，比较简单，所有框架差距不大
- <u>用作分布式锁</u>，Redisson 的分布式锁功能比较完善，有很多功能不用手写，有现成的直接用【RedLock 算法，读写锁，上锁后自动续期的 watchDog】

>[!hint] 技术选型
>- `Jedis` 
>- `Lettuce`
>- `Redisson` Redisson 是基于 NIO【~~非阻塞的~~】 的 netty 框架
>

```xml
<dependency>
    <groupId>org.redisson</groupId>
    <artifactId>redisson-spring-boot-starter</artifactId>
    <version>3.32.0</version>
</dependency>
```

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
  
        return Redisson.create(config);  
    }  
}
```

# 使用
## 💛哈希
```java
@Autowired  
private RedissonClient redissonClient;

// 会在redis中创建awards
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








