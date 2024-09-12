
>[!quote] Bean 定义
>Bean 定义 是用来描述一个 Bean 的各种属性的【Bean 的类名，Bean 的作用域，Bean 的构造函数参数，Bean 的属性值，Bean 的初始化方法，销毁方法……】

# ❤ 配置 Bean
>[!hint] 配置 Bean 主要有两种方式
> - `resource/META-INF/spring.factories` ：一般用于该项目是<u>组件项目</u>，<u>轮子项目</u>，<u>第三方依赖库项目</u> …… 。当这些项目被其他项目引入时，首先会扫描这个项目的 spring.factories 文件 ，然后根据路径准确地加载里面的配置类
> - `@Configuration` ：一般用于项目内部配置。SpringBoot 在启动时，会自动扫描主程序类所在的包及其所有的子包中的所有文件，寻找带有 @Configuration 的类作为配置类

## spring.factories
```yml
# 检测到`@EnableAutoConfiguration`注解时，应该自动加载`DynamicThreadPoolAutoConfig`这个类
org.springframework.boot.autoconfigure.EnableAutoConfiguration=app.xlog.ggbond.config.DynamicThreadPoolAutoConfig
```

## @Configuration


# ❤ Bean 管理
Spring 项目启动后，**默认**会把 Bean 都创建好放入到 IOC 容器中【还受到<u>作用域</u>，<u>延迟初始化</u>的影响】

>[!quote] 循环依赖
> 循环依赖是指两个或多个 Bean 之间相互依赖，互相注入对方的实例，形成一个闭环，当 IOC 容器尝试创建这些 Bean 时，它会陷入无限循环，~~因为每个 Bean 都需要另一个尚未完全创建的 Bean~~
> 
> **解决循环依赖**：
> - 三级缓存：Spring容器使用三级缓存来解决单例Bean的构造器循环依赖问题。当创建Bean时，Spring会将其放入三级缓存中，这样即使Bean还没有完全初始化，其他Bean也可以引用它
> - `@Lazy`注解：使用`@Lazy`注解可以延迟Bean的加载，直到它被实际使用。这可以防止在Bean的初始化过程中发生循环依赖
> - `@Autowired`与`@Qualifier`注解：使用`@Autowired`注解时，如果指定了`required=false`，Spring 将不会抛出异常，而是返回`null`，这可以避免某些循环依赖的情况
> - 使用`@Lookup`注解：`@Lookup` 允许在运行时而不是在Bean初始化时进行依赖注入，这可以打破循环依赖
> 
> 尽管 Spring 提供了解决循环依赖的方法，但最佳实践是尽量避免循环依赖的发生，通过重构代码和使用设计模式来改善代码结构

## 💛 手动获取 Bean
<u>手动获取 Bean 有三种方法</u>：
- 根据 name 获取
- 根据类型获取
- 根据 name，类型获取

```java
@SpringBootTest
class SpringAopApplicationTests {
    @Autowired
    private ApplicationContext applicationContext;

    @Test
    public void TestGetBean() {
		// 根据name获取bean
	    System.out.println(applicationContext.getBean("helloController"));

		// 根据类型获取bean
		System.out.println(applicationContext.getBean(HelloController.class));

		// 根据name, 类型获取bean
		System.out.println(applicationContext.getBean("helloController", HelloController.class));
    }
}

---
com.example.spring_aop.controller.HelloController@65af05b2
com.example.spring_aop.controller.HelloController@65af05b2
com.example.spring_aop.controller.HelloController@65af05b2
```

## 在非 Spring 中管理的类中注入 Bean
- 添加一个 SpringContextUtil 工具类 ：借助 ApplicationContext 的 getBean 功能，再利用 Java 的静态方法，就可以实现无需注解即可注入
```java
package app.xlog.ggbond.strategy.utils;

@Component
public class SpringContextUtil implements ApplicationContextAware {

    private static ApplicationContext context;

    @Override
    public void setApplicationContext(ApplicationContext applicationContext) throws BeansException {
        this.context = applicationContext;
    }

    public static <T> T getBean(Class<T> clazz) {
        return context.getBean(clazz);
    }

    public static <T> T getBean(String name, Class<T> clazz) {
        return context.getBean(name, clazz);
    }
}
```

- 添加一个配置类，使得在依赖注入完成之后，但 Bean 完全初始化之前，立即将正确的 Context 对象传递给 SpringContextUtil
```java
@Configuration
public class AppConfig {

    @Resource
    private ApplicationContext applicationContext;
    @Resource
    private SpringContextUtil springContextUtil;

    @PostConstruct
    public void init(){
	    springContextUtil.setApplicationContext(applicationContext);
    }
}
```

- 非 Spring 管理的类
```java
// 根据用户id判断是否是黑名单用户
public class BlacklistRaffleFilter implements RaffleFilter {

    private IUserService userService;

    public BlacklistRaffleFilter() {
	    // 利用静态方法查找UserService注入
        userService = SpringContextUtil.getBean(UserService.class);
    }

	// 使用IUserService里的方法 ……
}
```

- 测试
```java
@SpringBootTest
public class FilterTest {
    @Test
    public void test_FilterChain() {
	    BlacklistRaffleFilter b = new BlacklistRaffleFilter();
	    // 不会报错找不到UserService
	    b.filter();
    }
}
```

## 延迟初始化
添加 `@Lazy` 注解，我们用测试类来测试<u>默认</u>，与<u>延迟初始化</u>

```java
// Test 测试类
package com.example.spring_aop;

@SpringBootTest
class SpringAopApplicationTests {
    @Autowired
    private ApplicationContext applicationContext;

    @Test
    public void TestLazyInitialization() {
        System.out.println(applicationContext.getBean("helloController"));
    }
}
```

### 不延迟初始化
项目已启动，各种 Bean 就创建好了

```java
// HelloController
package com.example.spring_aop.controller;

@RestController
public class HelloController {
    // 无参构造
    public HelloController() {
        System.out.println("HelloController实例化了");
    }
    ……
    接口方法……
}

// 在测试类中打印出
---
HelloController实例化了
……
com.example.spring_aop.controller.HelloController@65af05b2
```

### 添加延迟初始化
在要使用到 Bean 时，才创建 Bean 对象

```java
// HelloController
package com.example.spring_aop.controller;

@Lazy
@RestController
public class HelloController {
    // 无参构造
    public HelloController() {
        System.out.println("HelloController实例化了");
    }
    ……
    接口方法……
}

// 在测试类中打印出
---
……
HelloController实例化了
com.example.spring_aop.controller.HelloController@38fb151a
```

## Bean 的作用域

|       作用域       |          说明           |
| :-------------: | :-------------------: |
| `singleton`【默认】 | 容器内同名称的 Bean，只有一个实例对象 |
|   `prototype`   | 每次使用 Bean，都会创建新的实例对象  |
|    `request`    |    每个请求范围内，会创建新的实例    |
|    `session`    |    每个会话范围，会创建新的实例     |
|  `application`  |    每个应用范围内，会创建新的实例    |

### prototype
加入 `@Scope("prototype")`

```java
package com.example.spring_aop.controller;

@Scope("prototype")
@RestController
public class HelloController {
    // 无参构造
    public HelloController() {
        System.out.println("HelloController实例化了");
    }
    ……
    接口方法……
}
```

```java
// Test 测试类
package com.example.spring_aop;

import com.example.spring_aop.controller.HelloController;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.context.ApplicationContext;

@SpringBootTest
class SpringAopApplicationTests {
    @Autowired
    private ApplicationContext applicationContext;

    @Test
    public void TestScope() {
        for (int i = 0; i < 4; i++) {
            System.out.println(applicationContext.getBean("helloController"));
        }
    }
}

---
HelloController实例化了
com.example.spring_aop.controller.HelloController@182e4365
HelloController实例化了
com.example.spring_aop.controller.HelloController@1e6d30c0
HelloController实例化了
com.example.spring_aop.controller.HelloController@38929da
HelloController实例化了
com.example.spring_aop.controller.HelloController@69d667a5
```

## 第三方 Bean
有时我们会在项目中引入第三方的依赖，其中会用到第三方包的对象，如果重复创建对象会消耗资源，我们会想将这个对象放到 IOC 容器中，但是**第三方包是只读的，无法修改**，这时我们就需要使用 `@Bean` 

```java
// 配置类
package com.example.spring_aop.config;

@Configuration
public class OthersBeansConfig {
	@Bean
	public SAXReader saxReader() {  // 这里的方法名就是 Bean 对象名
		return new SAXReader();
	}
}
```

```java
// 原本的创建
SAXReader saxReader = new SaxReader();

// 使用依赖注入
@AutoWired
private SAXReader saxReader;
```

### 如何在定义第三方 Bean 的过程中进行依赖注入
- 直接声明，不用使用 `@AutoWired`，SpringBoot 会自动进行依赖注入
```java
@Bean
public SAXReader saxReader(DeptService deptService) {  // Spring会自动对deptService注入
	sout(deptService);
	return new SAXReader();
}
```

- 如果是带有 `@ConfigurationProperties` 注解的类，那需要 `@EnableConfigurationProperties(……)`
```java
@ConfigurationProperties(prefix = "dept.data")
public class DeptProperties {
	private ……
	……

	get，set方法……
}
```

```java
@Configuration
// 将带有@ConfigurationProperties注解的DeptService.class注册为一个Bean
@EnableConfigurationProperties(DeptProperties.class)
public class SaxReaderConfiguration {
	@Bean
	public SAXReader saxReader(DeptProperties deptProperties) {  // Spring会自动对deptProperties注入
		sout(deptService);
		return new SAXReader();
	}
}
```

# ❤ Bean 的生命周期
- 通过 注解 / XML 配置文件，获取到 Bean 的元数据，注册 Bean 的信息
- 当某个地方需要 Bean 时，IOC 容器会根据注册的元数据创建 Bean 实例
- IOC 容器会将 Bean 实例注入到需要的地方
- **初始化回调** ：
    - `@PostConstruct` 可以标记任何无参方法，这个方法会在依赖注入完成后被自动调用
- Bean 被完全初始化，可以被应用程序使用
- **销毁回调** ：
	- `@PreDestroy` 在 Bean 的生命周期结束之前，会调用
- Bean 的生命周期在 IOC 容器中结束，但是，Bean 实例是否从内存中消失还取决于 Java 的垃圾回收机制

>[!quote] `@PostConstruct` 
>一个类中只要有一个方法被 `@PostConstruct` 注解标识，则这个类的所有方法都会被执行一遍，即使其他方法没有任何注解标识，顺序是：
>- 先执行 `@PostConstruct` 标识的方法，~~A 方法~~
>- 再执行其他方法，~~B 方法~~
>
> ```java
> @Configuration
> public class A {
>     @PostConstruct  
>     private void A() { …… }
> 
> 	private void B() { …… }
> }
> ```























