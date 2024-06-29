
>[!hint] 技术选型
>- `Jedis` 
>- `Lettuce`
>- `Redisson` 
>
>引入 Redis 主要就是两方面的作用：
>- <u>用作缓存</u>，比较简单，所有框架差距不大
>- <u>用作分布式锁</u>，Redisson 的分布式锁功能比较完善，有很多功能不用手写，有现成的直接用【RedLock 算法，读写锁，上锁后自动续期的 watchDog】

```xml
<dependency>
    <groupId>org.redisson</groupId>
    <artifactId>redisson</artifactId>
    <version>3.32.0</version>
</dependency>
```










