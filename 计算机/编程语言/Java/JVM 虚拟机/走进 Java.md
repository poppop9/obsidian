
$$
Write Once，Run Anywhere
$$

# Java 技术体系
>[!quote] Java 技术体系：
 >- Java 程序设计语言
 >- 各种硬件平台上的 Java 虚拟机实现
 >- Class 文件格式
 >- Java 类库 API

>[!quote] JDK【~~Java Development Kit~~】
>JDK 是用于支持 Java 程序开发的最小环境，包括了：
>- Java 程序设计语言
>- JRE
>- 各种工具

>[!quote] JRE【~~Java Runtime Environment~~】
>JRE 是支持 Java 程序运行的标准环境，包括：
>- Java 类库 API 中的 Java SE API
>- JVM

![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202405101917285.png)

---

>[!quote] Java 的四条主要产品线：
> - `Java Card`：支持 Java 小程序运行在小内存设备（如智能卡）上的平台
> - `Java ME`【~~Micro Edition~~】：支持 Java 程序运行在移动终端上的平台，对 Java API 有所精简，并加入了移动终端的针对性支持。~~但是在智能手机上非常流行的主要使用 Java 语言开发的 Android 并不属于 Java ME~~
> - `Java SE`【~~Standard Edition~~】：支持面向桌面级应用的 Java 平台，提供了完整的 Java 核心 API
> - `Java EE`【~~Enterprise Edition~~】：支持使用多层架构的企业应用（如ERP、MIS、CRM应用）的 Java 平台，除了提供 Java SE API 外，还对其做了大量有针对性的扩充，并提供了相关的部署支持

>[!hint] 解释型语言 和 编译型语言
>- **解释型语言**：在程序运行的时候，解释器会逐行读取源代码，然后逐行翻译和执行，例如 Python
>	- <u>解释器不会生成目标代码文件</u>，每次运行程序都需要重新翻译，这就是为什么解释型语言的运行速度通常比编译型语言慢
>- **编译型语言**：在程序运行之前，先将整个源代码翻译成目标代码【~~通常是机器语言~~】，生成的目标代码文件可以单独运行，无需再次翻译，例如 C++
>
>>而我的神 “Java” ，是解释型【~~在 JVM 中解释~~】和编译型【~~生成了 .class 文件~~】的结合

# JDK 版本演进过程
- `JDK 1.0` 提供了一个纯解释执行的 Java 虚拟机实现，Applet，AWT ……
- `JDK 1.1` JAR 文件格式，JDBC，JavaBeans，RMI ……
- `JDK 1.2` EJB，Java Plug-in，Java IDL，Swing …… ；添加了 HotSpot 虚拟机，在 Java 虚拟机中第一次内置了 JIT 【~~Just In Time~~】 即时编译器；添加了 strictfp 关键字，Collections 集合类 ……
- `JDK 1.3` 改进 Java 类库
- `JDK 1.4` 正则表达式，异常链，NIO，日志类，XML 解析器，XSLT转换器 ……
- 微软的 .NET 出现与 Java 竞争
- `JDK 5` 自动装箱，泛型，动态注解，枚举，可变长参数，遍历循环 …… ；改进了虚拟机中 Java 的内存模型；提供了并发包
- `JDK 6` 对 JVM 内部做了大量改进：锁与同步，垃圾收集，类加载
- `JDK 7` 提供新的 G1 收集器，加强对非 Java 语言的调用支持，可并行的类加载架构 …… ；对 ARM 指令集架构提供了支持，意味着可以为 Mac OS X 系统提供支持
- `JDK 8` 对 Lambda 表达式的支持，内置 Nashorn JavaScript 引擎的支持【~~允许在 JVM 上运行 JavaScript 代码~~】，新的时间日期 API
- `JDK 9` 引入了 Jigsaw 模块化系统【~~把 Java 的庞大的运行时环境 JRE 分解为一系列可互换的模块，这样开发者可以只选择他们需要的模块来构建应用，从而减少应用的大小和复杂度~~】；支持 HTTP 2 客户端 API 等 91 个 JEP
- `JDK 10` 内部重构【统一源仓库，统一垃圾收集器接口，统一即时编译器接口 ……】
- `JDK 11` 引入 ZGC 垃圾收集器
- `JDK 12` Switch 表达式、Java 微测试套件 ……

>[!quote] JIT 即时编译器
>JIT 编译器在程序运行时将<u>热点代码</u>【被频繁执行的代码】编译为机器代码，这样就可以直接执行，而不需要再解释字节码，大大提高了执行效率

# JVM 家族的变迁
- `Sun Classic/Exact VM` 虚拟机始祖，这款虚拟机只能使用纯解释器方式来执行 Java 代码，但是也可以用外挂的方式来使用即时编译器，只是如果外挂了即时编译器，即时编译器就会完全接管虚拟机的执行系统，解释器便不能再工作了







