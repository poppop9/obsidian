$$
SLF4J 是一个接口，它本身不具有输出日志的功能，输出日志还是由抽象类来实现【比如 log4j，logback】【~~类比 JDBC 只是一种规则~~】
$$

# 概述
## 介绍
我们在编写代码的时候，只会使用 SLF4J 里的 API，应用程序在运行时再去类路径下查找绑定的具体日志实现，并使用其进行实际的日志操作【~~如果在应用程序的类路径下面没有找到合适的绑定的话，默认无操作~~】，**也就是说，你要使用日志，你要引入两个依赖**【slf4j-api，实现类 api】，~~但是 SpringBoot-Starter-Web 里已经有了 logback 依赖，所以我们还是只用引入 slf4j 就好了~~

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

# 配置
我们可以使用两种方式来配置 SLF4J：
- **直接在 yml 配置文件中配置**：简单方便
- **重新定义一个** `logback-spring.xml`，**再在 yml 配置文件中激活** `logback-spring.xml`：功能更强大，可以对<u>不同环境下</u>【开发环境，测试环境，生产环境……】进行日志配置

## 直接在 yml 配置文件中配置
```properties
logging:
  # 指定不同包下使用不同的日志级别
  level:
    com.atguigu: trace
  # 以文件形式打印日志logging.file
  file:
    name: D:/boot.log	#指定日志文件的具体位置
  #日志输出格式：控制台，文件
  pattern: 
  	console: %d{yyyy-MM-dd} [%thread] %-5level %logger{50} - %msg%n
  	file: %d{yyyy-MM-dd} === [%thread] === %-5level === %logger{50} ==== %msg%n
  	
    #    %d 表示日期时间
    #    %thread 表示线程名
    #    %-5level 表示日志级别的显示宽度是5【无论实际的日志级别是什么，它都会在控制台上占用 5 个字符的宽度】，为了使得不同的日志级别在控制台上更加整齐
    #    %logger{50} 表示logger名字最长50个字符，否则按照句点分割
    #    %msg 日志消息
    #    %n 换行符
```

## 使用 logback-spring.xml 配置
添加日志配置文件 `logback-spring.xml`，在 `logback-spring.xml` 中，你可以定义多个 `Spring Profile`

- 在 yml 配置文件中激活 `Spring Profile`
```yml
# 激活了名为"dev"的Spring Profile
spring:
  profiles:
    active: dev
```

- 在 `logback-spring.xml` 中指定 `Spring Profile` 
```xml
<configuration>
	<!-- 定义第一个Spring Profile文件 -->
    <springProfile name="dev">
        <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
            <encoder>
                <pattern>%d{HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
            </encoder>
        </appender>

        <root level="debug">
            <appender-ref ref="CONSOLE" />
        </root>
    </springProfile>

	<!-- 定义第二个Spring Profile文件 -->
    <springProfile name="!dev">
        <appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
            <encoder>
                <pattern>%d{HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
            </encoder>
            <file>logs/app.log</file>
        </appender>

        <root level="info">
            <appender-ref ref="FILE" />
        </root>
    </springProfile>
</configuration>
```

# 切换日志框架
SpringBoot 默认使用 `spring-boot-starter-logging 启动器`【Logback 的启动器】, 如果要切换成 Log4j2 进行日志记录，那就要切换成 `spring-boot-starter-log4j2 启动器`

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <!--排除默认spring-boot-starter-logging启动器-->
    <exclusions>
        <exclusion>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-logging</artifactId>
        </exclusion>
    </exclusions>
</dependency>

<!--使用spring-boot-starter-log4j2启动器-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-log4j2</artifactId>
</dependency>
```

# 具体操作
```xml
<dependency>
	<groupId>org.slf4j</groupId>
	<artifactId>slf4j-api</artifactId>
	<version>2.0.12</version>
</dependency>
```

## 基本操作
```java
@SpringBootTest
class Web2ApplicationTests {
    @Test
    public void test() {
	    // 使用 LoggerFactory 创建与该类名相同的记录器
        Logger logger = LoggerFactory.getLogger(Web2ApplicationTests.class);
        logger.info("Hello SLF4J !");
        
        // 使用占位符
        String s = "greenteck";  
		String ss = "pop";  
		logger.info("Hello {}!, {}", s, ss);
    }
}

---
2024-04-10T11:01:45.273+08:00  INFO 14720 --- [           main] com.example.web_2.Web2ApplicationTests   : Hello SLF4J !
2024-04-10T11:01:45.273+08:00  INFO 14720 --- [           main] com.example.web_2.Web2ApplicationTests   : Hello greenteck!, pop
```

## 链式编程记录日志
>[!hint] 这种方式可以使用 `addKeyValue(key, value)` 给日志添加键值对，更有利于后续分析

`atTrace()`，`atDebug()`，`atInfo()`，`atWarn()` ，`atError()`，`atFatal()` 方法都会返回一个 `LoggingEventBuilder` 实例

```java
@SpringBootTest  
class Web2ApplicationTests {  
    @Test  
    public void test() {  
        Logger logger = LoggerFactory.getLogger(Web2ApplicationTests.class);  
        logger.atInfo().log("Hello");  

        String oldT = "1";
        String newT = "3";
        logger.info("oldT={} newT={} Temperature changed.", oldT, newT);
        logger.atInfo().setMessage("Temperature changed.").addKeyValue("oldT", oldT).addKeyValue("newT", newT).log();
    }  
}

---
2024-04-10T11:14:51.204+08:00  INFO 10180 --- [           main] com.example.web_2.Web2ApplicationTests   : Hello
```




















