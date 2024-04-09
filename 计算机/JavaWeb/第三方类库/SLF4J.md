$$
SLF4J 是一个接口，它本身不具有输出日志的功能，输出日志还是由抽象类来实现【比如 log4j，logback】【~~类比 JDBC 只是一种规则~~】
$$

# 概述
## 介绍
我们在编写代码的时候，只会使用 SLF4J 里的 API，应用程序在运行时再去类路径下查找绑定的具体日志实现，并使用其进行实际的日志操作【~~如果在应用程序的类路径下面没有找到合适的绑定的话，默认使用一个没有任何操作的实现~~】

---

SLF4J 只做两件事：
- 提供日志接口
- 提供获取具体日志对象的方法

---

>[!hint] 为什么要选择抽象层的 SLF4J，而不是实现类【log4j，logback】？
>假设 A 开发了一个通用组件，他在程序中使用的是 log4j，B 之前开发的的业务模块使用的是 logback。突然有一天 B 要在自己的业务系统中使用 A 的通用组件，那就很麻烦了，<u>那么解决方案就是使用 SLF4J</u>

## 日志级别
- `fatal` 灾难级的，因为代码异常导致程序退出执行的事件；系统级别，程序无法打印
- `error` 错误信息
- `warn` 警告信息
- `info` 普通的打印信息
- `debug` 需要调试时候的关键信息
- `trace` 级别最低

>[!hint] 当某个项目目录设置了日志级别，我们只能得到`此级别及更高级别`的日志，SpringBoot 的默认级别是 `info`

## 日志格式
日志 = 日志打印时间 + 日志级别 + 线程 id + 线程名称 + 日志所在类 + 日志内容

---

```xml
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-api</artifactId>
    <version>1.7.21</version>
</dependency>
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-log4j12</artifactId>
    <version>1.7.21</version>
</dependency>
```

# slf4j-api
>slf4j-api 作为 slf4j 的接口类，提供了一个 `Logger 类`【打日志】，和 `LoggerFactory 类`【获取 `Logger`】





# slf4j-log4j
> slf4j-log4j 是连接 slf4j 和 log4j 的桥梁





































