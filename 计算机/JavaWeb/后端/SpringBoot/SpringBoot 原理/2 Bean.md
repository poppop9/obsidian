
>[!quote] Bean 定义
>Bean 定义 是用来描述一个 Bean 的各种属性的【Bean 的类名，Bean 的作用域，Bean 的构造函数参数，Bean 的属性值，Bean 的初始化方法，销毁方法……】

---

# 配置 Bean
>[!hint] 配置 Bean 主要有两种方式
> - `spring.factories` ：一般用于该项目shi
> - `@Configuration` ：



1. 使用`spring.factories`。这是一种更适合第三方库自动配置的方式。无论你的库在哪个路径下，只要被包含在项目的classpath中，Spring Boot都会在启动时扫描到你的`spring.factories`文件，并执行其中指定的自动配置类。这种方式对于创建可以被其他项目引用的库，比如一个通用组件或者"轮子"，非常适合。
    
2. 使用`@Configuration`注解。这种方式主要用于项目内部的配置，Spring Boot只会扫描它知道的路径下的`@Configuration`类。在你的项目中有一些Bean需要初始化，或者需要做一些特殊的配置时，你可以创建一个带有`@Configuration`注解的Java类，然后在这个类中进行配置。
    

  

这两种方式各有优势，选择哪种方式取决于你的具体需求和使用场景。














