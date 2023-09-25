# 安装 创建
- 解压`apache-maven-3.8.8-bin,zip`
- 配置本地仓库
	- 在Maven根目录下新建`mvn_repo文件夹`来当作本地仓库
	- 在`conf`文件夹下的`setting.xml`中添加一行本地仓库路径
		```xml
		  <!-- localRepository
		   | The path to the local repository maven will use to store artifacts.
		   |
		   | Default: ${user.home}/.m2/repository
		  <localRepository>/path/to/local/repo</localRepository>
		  -->
		  <localRepository>D:\apache-maven-3.8.8\mvn_repo</localRepository> //添加这行
		```
- 在`conf`文件夹下的`setting.xml`中配置阿里云私服
	```xml
	  <mirrors>
	    <mirror>
	      <id>maven-default-http-blocker</id>
	      <mirrorOf>external:http:*</mirrorOf>
	      <name>Pseudo repository to mirror external repositories initially using HTTP.</name>
	      <url>http://0.0.0.0/</url>
	      <blocked>true</blocked>
	    </mirror>
	  	 
	<!--添加阿里云镜像-->
	    <mirror>
	      <id>alimaven</id>
	      <name>aliyun maven</name>
	      <url>http://maven.aliyun.com/nexus/content/groups/public</url>
		  <mirrorOf>central</mirrorOf>
	    </mirror>
	<!--          -->
	  </mirrors>
	```
- 配置环境变量
>为了在任何目录下都可以运行Maven指令
- 在cmd中运行`mvn -v`测试版本号
### Maven目录结构
- `bin` 可执行文件
- `boot`
- `conf` 配置文件
- `lib` jar包资源
### 在idea中安装
##### 配置单个项目
- 设置-构建-构建工具-Maven
![[Excalidraw/计算机/JavaWeb.md#^group=nbor17Ei|780]]
- 设置-构建-构建工具-Maven-runner
查看jre的配置是否正确
- 设置-构建-构建工具-compiler-java complier
配置正确的字节码版本
##### 配置全局项目【推荐】
![[Excalidraw/计算机/JavaWeb.md#^group=b9Q6iSUb|500]]
- 设置-构建-构建工具-Maven
![[Excalidraw/计算机/JavaWeb.md#^group=nbor17Ei|780]]
- 设置-构建-构建工具-Maven-runner
查看jre的配置是否正确
- 设置-构建-构建工具-compiler-java complier
配置正确的字节码版本
### 在idea中创建Maven项目
- 新建Maven模块
![[Excalidraw/计算机/JavaWeb.md#^group=9k6ZEAZA|600]]
- 设置信息
![[Excalidraw/计算机/JavaWeb.md#^group=C5fG4EIs]]
# 基本概念
>Maven是构建和管理Java项目的工具
### 作用
##### 更好的依赖管理
- 不用手动导入`jar`包，只需在`pom.xml`文件中声明`jar包名`和`对应版本`即可，Maven会自动联网下载
	- 首先Maven先从本地仓库查找有无这个`jar包`
		- 有，则从本地仓库引用
		- 没有，则从私服仓库下载到本地仓库，然后引用
			- 若私服仓库没有，则从中央仓库下载到私服仓库，再到本地仓库 
- 后续需要更新`jar`包的版本也只需要更改声明中的版本号即可，不需要手动连锁改动
##### 统一项目结构
Maven规定了一套统一的Java开发目录，这样***可以让不同开发软件开发出来的项目可以互相移植***
###### 项目目录结构
- `Maven-project`
	- `src`
		- `main` 实际项目资源
			- `java` java源代码
			- `resources` 配置文件
		- `test` 测试项目资源
			- `java` 测试相关的java源代码
			- `resources` 测试相关的配置文件
		- `pom.xml` Maven的核心配置文件
			- Maven坐标
				```xml
				<groupId>org.example</groupId>  //组织名称【通常是域名反写】
				<artifactId>maven-project_1</artifactId>  //项目名称
				<version>1.0-SNAPSHOT</version>  //版本号
				```
##### 提供标准的跨平台项目构建化流程
对不同平台的***编译，测试，打包等操作***进行了统一标准化
# 依赖管理
### 依赖配置
- 编写dependencies标签
- 编写dependency标签
- 去[Maven仓库](https://mvnrepository.com/)找到自己想要引入的依赖，查看三个坐标信息，填写到dependency里
- 填写完成后点击悬浮的刷新按钮
```xml
<dependencies>    //编写dependencies标签
    <dependency>    //编写dependency标签
        <groupId>ch.qos.logback</groupId>  
        <artifactId>logback-classic</artifactId>  //需要引入的依赖名  
        <version>1.2.3</version>  
    </dependency>  
</dependencies>
```
### 依赖传递
![[Excalidraw/计算机/JavaWeb.md#^group=L9zUCejmwM7J5nO09dTMN|600]]
##### 查看依赖关系
右键`pom.xml`，选择`diagrams`的`show dependencies`
![[Excalidraw/计算机/JavaWeb.md#^group=B2BAxMME|600]]
##### 排除依赖
>排除依赖就是，`A项目`引用了`B项目`但是不想引用`B项目`底下的jar包
```xml
<dependencies>  
    <dependency>  
        <groupId>组织名</groupId>  
        <artifactId>项目B</artifactId>  
        <version>版本</version>  

		<!--排除依赖-->
		<exclusions>
			<exclusion>
				<groupId>依赖名</groupId>
				<artifactId>依赖名</artifactId>
			</exclusion>
		</exclusions>
    </dependency>  
</dependencies>
```
##### 依赖范围
依赖的jar包，默认作用在***主程序范围***，***测试程序范围***，***参与打包***。也可以通过`<scope>`标签来设置范围

|scope值|主程序|测试程序|打包|范例|
|:-:|:-:|:-:|:-:|:-:|
|complie【默认】|√|√|√|log4j|
|test|  |√|  |junit|
|provided|√|√|  |servlet-api|
|runtime|  |√|√|JDBC驱动|















