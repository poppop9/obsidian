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
	- `@Target({ElementType.TYPE})`  源注解，用于描述注解的使用范围【可以指定注解可以用于类、方法、字段……】
	- `@Retention(RetentionPolicy.RUNTIME)`  源注解，用于描述注解的生命周期【可以指定注解在编译时、运行时或两者都保留】
	- `@Documented`  源注解，用于描述注解是否应该包含在Javadoc中
	- `@Inherited`  源注解，用于描述注解是否应该继承到子类中
	- `@SpringBootConfiguration`  表示是一个<u>配置类</u>【所以可以在启动类里配置第三方 Bean，不过不推荐】
	- `@EnableAutoConfiguration`  
		- `@AutoConfigurationPackage` 
		- `@Import({AutoConfigurationImportSelector.class})` 导入了一个 `ImportSelector接口` 的实现类，`ImportSelector接口` 的其中一个方法的返回值是一个 `String[]` ，里面是导入到 IOC 容器中的类
			- 最终会跟踪到一个文件 `org.springframework.boot.autoconfigure.AutoConfiguration.imports` 里面包含了所有的配置类
	- `@ComponentScan(……)` 表示扫描包的范围【默认是扫描当前包及其子包】

## 条件装配
`org.springframework.boot.autoconfigure.AutoConfiguration.imports` 文件里所有的配置类基本都不是一次性就直接装配到 IOC 容器中的，都是***条件装配的***

### 条件装配注释树
- `@Conditional` 条件装配的父注解【可以加在类，方法上】
	- `@ConditionalOnClass` 判断环境中是否有对应的字节码文件，有才注册 Bean
	- `@ConditionalOnMissingBean` 判断环境中是否没有对应的 Bean，没有才注册 Bean
	- `@ConditionalOnProperty` 判断环境中是否有对应的属性名，属性值
	- ……


































