# 基本概念
>Spring是一个开发生态圈，它提供了若干个子项目，用于完成特定功能
>![[Excalidraw/计算机/JavaWeb.md#^group=Lu3xncQA90nuAeKIaESZ_]]
# 准备工作
- 创建Spring模块
	- 勾选Web开发相关依赖
	![[Excalidraw/计算机/JavaWeb.md#^group=dMXiaySV]]
	![[Excalidraw/计算机/JavaWeb.md#^group=qCHuJWbK]]
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






























