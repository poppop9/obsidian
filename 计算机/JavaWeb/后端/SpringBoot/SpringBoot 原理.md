# 起步依赖
```xml
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

当引入起步依赖后，Maven 会根据起步依赖进行依赖传递，把 Web 开发相关的依赖都传递进来

# 自动配置
>Spring 容器启动后，会自动将一些<u>配置类</u>，<u>Bean 对象</u>放入到 IOC 容器中，我们就可以直接使用

由于，直接讲解很晦涩，所以我们自己编写一个第三方依赖，然后在项目中手动导入，来解释 SpringBoot 底层是如何实现自动配置的

## 自定义依赖导入
### 依赖包项目
#### 项目结构
- DependencyTool
	- src
		- main
			- java
				- com.example
					- `EnableHeaderConfig` 用来给主项目导入整个依赖包
					- `HeaderConfig`
					- `HeaderGenerator`
					- `HeaderParser`
					- `MyImportSelector`
					- `TokenParser`

```java
// 定义了一个注解EnableHeaderConfig
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
@Import(MyImportSelector.class)  // 指定到底要导入哪些配置类
public @interface EnableHeaderConfig {}
```

### 主项目
```java
// 启动类
@EnableHeaderConfig  // 引入注解
@SpringBootApplication  
public class SpringAopApplication {  
    public static void main(String[] args) {  
       SpringApplication.run(SpringAopApplication.class, args);  
    }  
}
```

通过添加依赖包中的注解，即可将依赖包中的对象加入到 IOC 容器，从而引入项目

## @SpringBootApplication
- `@SpringBootApplication`

@Target({ElementType.TYPE})  
@Retention(RetentionPolicy.RUNTIME)  
@Documented  
@Inherited  
@SpringBootConfiguration  
@EnableAutoConfiguration  
@ComponentScan(





































