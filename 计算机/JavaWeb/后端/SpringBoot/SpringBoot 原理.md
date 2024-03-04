# 配置优先级
SpringBoot 中正常支持<u>三种</u>配置文件【`properties`，`yml`，`yaml`】，如果一个项目中出现了多个配置文件配置相同属性的冲突，则它们的优先级排行是`properties` > `yml` > `yaml`

## 外部配置
其实 SpringBoot 中还可以使用 ***Java系统属性***，或***命令行参数*** 来配置项目属性，但是在项目中一般不使用

>[!hint] 如果要在项目打包成 `jar包` 后，非永久性的修改配置，可以使用 ***Java系统属性***，或***命令行参数*** 
>- 运行 `jar包`
>- 在命令行运行 `java -jar your-application.jar --server.port=8080`

---

>[!hint] 总的优先级排行
>***命令行参数*** > ***Java系统属性*** > `properties` > `yml` > `yaml`

# Bean管理
Spring 项目启动后，***默认***会把 Bean 都创建好放入到 IOC 容器中【还受到<u>作用域</u>，<u>延迟初始化</u>的影响】

## 手动获取Bean
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




## Bean的作用域

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

## 第三方Bean
有时我们会在项目中引入第三方的依赖，其中会用到第三方包的对象，如果重复创建对象会消耗资源，我们会想将这个对象放到 IOC 容器中，但是***第三方包是只读的，无法修改***，这时我们就需要使用 `@Bean` 

```java
SAXReader saxReader = new SaxReader();
```

```java
// 启动类
package com.example.spring_aop;

@SpringBootApplication
public class SpringAopApplication {
	public static void main(String[] args) {
		SpringApplication.run(SpringAopApplication.class, args);
	}

	// 声明第三方 Bean
	@Bean
	public SAXReader putIOCSaxReader(){
		return new SAXReader();
	}
}
```
















