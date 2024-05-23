
>[!quote] Bean 定义
>Bean 定义 是用来描述一个 Bean 的各种属性的【Bean 的类名，Bean 的作用域，Bean 的构造函数参数，Bean 的属性值，Bean 的初始化方法，销毁方法……】

---

# 配置 Bean
>[!hint] 配置 Bean 主要有两种方式
> - `spring.factories` ：一般用于该项目是<u>组件项目</u>，<u>轮子项目</u>，<u>第三方依赖库项目</u> …… 。当这些项目被其他项目引入时，首先会扫描这个项目的 `spring.factories` ，然后根据路径准确地加载里面的配置类
> - `@Configuration` ：一般用于项目内部配置。SpringBoot 在启动时，会自动扫描项目中的所有文件，寻找带有 `@Configuration` 的类作为配置类


这些配置类中的方法可以用`@Bean`注解，Spring Boot会调用这些方法，将返回的对象自动添加到Spring的上下文中，这样我们就可以在项目中的其他地方通过依赖注入来使用这些对象。

然而，Spring Boot并不会扫描项目中的所有路径。它只会扫描某些特定的路径。具体来说，它会扫描主程序类（通常是带有`@SpringBootApplication`注解的类）所在的包以及这个包下的所有子包。

  

举个例子，如果你的主程序类位于`com.example.demo`包中，那么Spring Boot会扫描这个包以及所有像`com.example.demo.config`这样的子包。但是它不会扫描`com.example.config`这样的包，因为它不在主程序类的包或子包中。












