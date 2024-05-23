
>[!quote] Bean 定义
>Bean 定义 是用来描述一个 Bean 的各种属性的【Bean 的类名，Bean 的作用域，Bean 的构造函数参数，Bean 的属性值，Bean 的初始化方法，销毁方法……】

---

# 配置 Bean
>[!hint] 配置 Bean 主要有两种方式
> - `resource/META-INF/spring.factories` ：一般用于该项目是<u>组件项目</u>，<u>轮子项目</u>，<u>第三方依赖库项目</u> …… 。当这些项目被其他项目引入时，首先会扫描这个项目的 `spring.factories` 文件 ，然后根据路径准确地加载里面的配置类
> - `@Configuration` ：一般用于项目内部配置。SpringBoot 在启动时，会自动扫描主程序类所在的包及其所有的子包中的所有文件，寻找带有 `@Configuration` 的类作为配置类

## spring.factories
```yml
# 检测到`@EnableAutoConfiguration`注解时，应该自动加载`DynamicThreadPoolAutoConfig`这个类
org.springframework.boot.autoconfigure.EnableAutoConfiguration=app.xlog.ggbond.config.DynamicThreadPoolAutoConfig
```




## @Configuration


# Bean 管理
Spring 项目启动后，**默认**会把 Bean 都创建好放入到 IOC 容器中【还受到<u>作用域</u>，<u>延迟初始化</u>的影响】

## 手动获取 Bean
有三种方法：
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

## 延迟初始化
>添加 `@Lazy` 注解

我们用测试类来测试<u>默认</u>，与<u>延迟初始化</u>
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
>项目已启动，各种 Bean 就创建好了

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
>在要使用到 Bean 时，才创建 Bean 对象

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
>加入 `@Scope("prototype")`

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



























