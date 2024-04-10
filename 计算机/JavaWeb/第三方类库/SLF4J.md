$$
SLF4J 是一个接口，它本身不具有输出日志的功能，输出日志还是由抽象类来实现【比如 log4j，logback】【~~类比 JDBC 只是一种规则~~】
$$

# 概述
## 介绍
我们在编写代码的时候，只会使用 SLF4J 里的 API，应用程序在运行时再去类路径下查找绑定的具体日志实现，并使用其进行实际的日志操作【~~如果在应用程序的类路径下面没有找到合适的绑定的话，默认无操作~~】，**也就是说，你要使用日志，你要引入两个依赖**【slf4j-api，实现类 api】

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


当日志配置命名为logback.xml时, 这个配置直接就被日志框架识别了

当日志配置命名为logback-spring.xml时, 这个配置由springboot解析识别, 可以使用更高级的功能, 例如 springProfile, 他与springboot中的Profiles对应, 在springboot默认配置文件中激活指定Profiles, 日志配置也将改变

```
<springProfile name="staging">
    <!-- configuration to be enabled when the "staging" profile is active -->
</springProfile>

```

如果使用logback.xml作为日志配置文件，还要使用profile功能，会有以下错误：`no applicable action for [springProfile]`

比如在logback-spring.xml中做出以下配置，就可以指定某段配置只在某个环境下生效

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration scan="true">
    <include resource="org/springframework/boot/logging/logback/defaults.xml" />
    <property name="log.path" value="./logs" />
    <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <pattern>${CONSOLE_LOG_PATTERN}</pattern>
            <charset>utf8</charset>
        </encoder>
        <layout class="ch.qos.logback.classic.PatternLayout">
            <pattern>[%X{trackId}][%thread] [%d{yyyy-MM-dd HH:mm:ss.SSS}] %-5level %logger{30} - %msg%n</pattern>
        </layout>
    </appender>
    <!-- level为 info 日志，时间滚动输出  -->
    <appender name="Log_FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <!-- 正在记录的日志文档的路径及文档名 -->
        <file>${log.path}/info.log</file>
        <!--日志文档输出格式-->
        <encoder>
            <pattern>[%X{trackId}][%thread] [%d{yyyy-MM-dd HH:mm:ss.SSS}] %-5level %logger{30} - %msg%n</pattern>
            <charset>UTF-8</charset> <!-- 设置字符集 -->
        </encoder>
        <!-- 日志记录器的滚动策略，按日期，按大小记录 -->
        <rollingPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">
            <!-- 日志归档 -->
            <fileNamePattern>${log.path}/info-%d{yyyy-MM-dd}.%i.log</fileNamePattern>
            <!--日志文档保留天数-->
            <maxHistory>5</maxHistory>
            <maxFileSize>100MB</maxFileSize>
            <totalSizeCap>5GB</totalSizeCap>
            <cleanHistoryOnStart>true</cleanHistoryOnStart>
        </rollingPolicy>
        <filter class="ch.qos.logback.classic.filter.LevelFilter">
            <level>INFO</level>
            <onMatch>ACCEPT</onMatch>
            <onMismatch>ACCEPT</onMismatch>
        </filter>
    </appender>

    <springProfile name="dev">
        <root level="info">
            <appender-ref ref="CONSOLE" />
        </root>
        <!--    mybatis sql单独控制输出级别    -->
        <logger name="com.demo.example.dao" level="debug"/>
    </springProfile>
    <springProfile name="prod">
        <root level="info">
            <appender-ref ref="Log_FILE" />
        </root>
        <!--    mybatis sql单独控制输出级别    -->
        <logger name="com.demo.example.dao" level="debug"/>
    </springProfile>
    <springProfile name="online">
        <root level="info">
            <appender-ref ref="Log_FILE" />
        </root>
        <!--    mybatis sql单独控制输出级别    -->
        <logger name="com.demo.example.dao" level="debug"/>
    </springProfile>
</configuration>
```

## 切换日志框架
springboot默认使用spring-boot-starter-logging启动器, 使用这个启动器默认使用Logback 进行日志记录, 如果要使用Log4j2 进行日志记录, 那么可以切换spring-boot-starter-log4j2启动器

具体切换方法为, 将默认spring-boot-starter-logging启动器排除, 使用spring-boot-starter-log4j2启动器
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

切换log4j日志框架

首先排除日志框架的实现jar, 比如偷梁换柱jar, log4j-to-slf4j.jar, 和logback-classic.jar(logback实现jar), 然后引入log4j的实现jar
```xml
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-log4j12</artifactId>
</dependency>
```






















