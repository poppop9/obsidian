# 基本概念
>Spring是一个开发生态圈，它提供了若干个子项目，用于完成特定功能
>![[Excalidraw/计算机/JavaWeb.md#^group=Lu3xncQA90nuAeKIaESZ_]]
# 准备工作
### 创建Spring项目
- 创建Spring模块
	- 勾选Web开发相关依赖
	![[Excalidraw/计算机/JavaWeb.md#^group=dMXiaySV]]
	![[Excalidraw/计算机/JavaWeb.md#^group=qCHuJWbK]]
### 目录结构
- `.mvn` - Maven wrapper文件
- `src` - 源码目录
    - `main`
        - `java`
            - `包路径`
                - `启动类` 
        - `resources` - 资源文件目录
            - `application.properties` - Spring Boot配置文件
    - `test`
        - `java`
            - `包路径`
			- `项目名称ApplicationTests.java` - 测试 starters
- `pom.xml` - Maven项目对象模型配置文件
# HTTP协议
### 概述
- HTTP协议，一次请求对应一次响应
- HTTP协议每次请求和响应都是独立的，后一次请求无法知道前一次请求的数据




- 定义请求处理类，添加请求处理方法，添加注解
```java
@RestController  //如果不定义则是一个普通java类，定义了表示是一个请求处理类
public class hello {  
    @RequestMapping("/hello")  //表示当请求/hello时，会执行hello()方法
    public String hello() {  
        System.out.println("hello spring");  
        return "hello spring";  
    }  
}
```

























