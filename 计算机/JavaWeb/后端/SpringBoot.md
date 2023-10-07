# 基本概念
>Spring是一个开发生态圈，它提供了若干个子项目，用于完成特定功能
>![[JavaWeb Draw#^group=Lu3xncQA90nuAeKIaESZ_]]
# 准备工作
### 创建Spring项目
- 创建Spring模块
	- 勾选Web开发相关依赖
	![[JavaWeb Draw#^group=dMXiaySV]]
	![[JavaWeb Draw#^group=qCHuJWbK]]
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
# Web服务器
>Web服务器对HTTP协议的操作进行了封装，使得Web开发更为便携。Web服务器可以用来部署我们我们开发好的Web项目，对外提供网上信息浏览服务
### HTTP协议
- HTTP协议，一次请求对应一次响应
- HTTP协议每次请求和响应都是独立的，后一次请求无法知道前一次请求的数据
### Tomcat
>Tomcat是一款轻量级的Web服务器

SpringBoot的依赖项的起步依赖web【里面包含了很多依赖】中已经***内置了Tomcat***，当启动类运行时，会自动运行Tomcat服务器
![[JavaWeb Draw#^group=yrp52Usr]]

# 请求，响应，分层解耦
![[JavaWeb Draw#^group=tMdaT5BlcDIqJIyPd8ixX|770]]
### 请求
##### Apifox
>Apifox是一款 API设计/开发/测试工具
##### 简单参数




















































