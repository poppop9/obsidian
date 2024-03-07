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
		  <localRepository>D:\apache-maven-3.9.6\mvn_repo</localRepository>
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
	  </mirrors>
	```
- 配置环境变量
>为了在任何目录下都可以运行Maven指令
- 在cmd中运行`mvn -v`测试版本号
## Maven目录结构
- `bin` 可执行文件
- `boot`
- `conf` 配置文件
- `lib` jar包资源
## 在idea中安装
### 配置单个项目
- 设置-构建-构建工具-Maven
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403031421719.png)
- 设置-构建-构建工具-Maven-runner
查看jre的配置是否正确
- 设置-构建-构建工具-compiler-java complier
配置正确的字节码版本
### 配置全局项目【推荐】
![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403031422200.png)

## 在idea中创建Maven项目
- 新建Maven模块
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403031422374.png)
- 设置信息
![400](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403031422705.png)

# 基本概念
>Maven是构建和管理Java项目的工具
## 作用
### 更好的依赖管理
- 不用手动导入`jar`包，只需在`pom.xml`文件中声明`jar包名`和`对应版本`即可，Maven会自动联网下载
	- 首先Maven先从本地仓库查找有无这个`jar包`
		- 有，则从本地仓库引用
		- 没有，则从私服仓库下载到本地仓库，然后引用
			- 若私服仓库没有，则从中央仓库下载到私服仓库，再到本地仓库 
- 后续需要更新`jar`包的版本也只需要更改声明中的版本号即可，不需要手动连锁改动
### 统一项目结构
>Maven规定了一套统一的Java开发目录，这样***可以让不同开发软件开发出来的项目可以互相移植***
#### 项目目录结构
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
### 标准的跨平台项目构建化流程
>对不同平台的***编译，测试，打包等操作***进行了统一标准化
# 依赖管理
## 依赖配置
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
## 依赖传递
![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403031423203.png)

### 查看依赖关系
右键`pom.xml`，选择`diagrams`的`show dependencies`
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403031423533.png)

### 排除依赖
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
### 依赖范围
依赖的jar包，默认作用在***主程序范围***，***测试程序范围***，***参与打包***。也可以通过`<scope>`标签来设置范围

|scope值|主程序|测试程序|打包|范例|
|:-:|:-:|:-:|:-:|:-:|
|complie【默认】|√|√|√|log4j|
|test|  |√|  |junit|
|provided|√|√|  |servlet-api|
|runtime|  |√|√|JDBC驱动|
```xml
<dependencies>  
    <dependency>  
        <groupId>ch.qos.logback</groupId>  
        <artifactId>logback-classic</artifactId>  
        <version>1.2.3</version>  
        <scope>test</scope>  //指定scope值
    </dependency>  
</dependencies>
```
### 生命周期
>Maven有三套独立的生命周期，每一套都有若干个阶段。***同一套生命周期的阶段具有依赖性，运行后阶段，前阶段也会运行***
#### clean
1. `pre-clean`
2. ==clean==：移除上一次构建生成的文件
3. `post-clean`
#### default
1. `validate`：验证项目是否正确且所有必需的信息可用。
2. `initialize`：初始化构建状态，例如设置属性或创建目录结构。
3. `generate-sources`：生成源代码，通常是从注解处理器或其他工具生成的代码。
4. `process-sources`：处理源代码，例如编译、过滤或转换。
5. `generate-resources`：生成资源文件，例如从非Java源代码生成的文件。
6. `process-resources`：处理资源文件，例如拷贝到输出目录或对资源文件进行过滤。
7. ==compile==：把项目的源代码编译为`.class`文件
8. `process-classes`：处理编译后的类文件，例如对字节码进行额外的操作。
9. `generate-test-sources`：生成测试代码的源代码。
10. `process-test-sources`：处理测试代码的源代码，例如编译、过滤或转换。
11. `generate-test-resources`：生成测试使用的资源文件。
12. `process-test-resources`：处理测试使用的资源文件。
13. `test-compile`：编译测试代码。
14. `process-test-classes`：处理编译后的测试类文件。
15. ==test==：运行测试
16. `prepare-package`：在打包之前执行任何必要的操作。
17. ==package==：将编译后的代码打包成可发布的格式【JAR】
18. `pre-integration-test`：在集成测试之前执行任何必要的操作。
19. `integration-test`：执行集成测试。
20. `post-integration-test`：在集成测试之后执行任何必要的操作。
21. `verify`：对集成测试的结果进行验证。
22. ==install==：将打包的项目安装到本地仓库，以供其他项目使用
23. `deploy`：将最终的包复制到远程仓库，以供其他开发人员和项目使用

#### site
1. `pre-site`：在生成站点之前运行的阶段。在此阶段，可以执行一些准备工作，例如准备生成站点所需的资源或检查先决条件。
2. `site`：生成项目的站点文档的阶段。在此阶段，Maven 将根据项目配置和插件设置生成站点文档，包括项目报告、文档页面等。
3. `post-site`：在生成站点之后运行的阶段。在此阶段，可以执行一些后处理操作，例如复制附加资源到生成的站点目录或进行站点发布的准备工作。
4. `site-deploy`：将生成的站点文档部署到指定的服务器或远程仓库的阶段。在此阶段，可以将生成的站点文档发布到远程服务器，以供他人访问。

>[!warning] 如何运行生命周期的某个阶段 ？
>在Maven的侧边栏中运行
>![[JavaWeb Draw#^group=QqvDzj8c|300]]

# Maven 的打包方式
- `jar` 【默认】Java 应用程序的标准打包格式，内嵌了 Tomcat
- `war` Web 应用程序的打包格式，需要自己部署到服务器上运行
- `pom` ***通常用在父级工程或聚合工程中***

# Maven 高级
## 分模块设计
![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403061147795.png)

>[!hint] 分模块设计可以方便项目管理，维护，扩展，模块间的共享复用

---
### 项目结构
- idea_project
	- ***blog_pojo*** 创建时创建 Maven 就好，不用创建 Spring
		- src
			- main
				- java
					- com.blog
						- `Dept`
						- `Emp`
						- ……
	- ***blog_utils*** 创建时创建 Maven 就好，不用创建 Spring
	- ***blog_manegement***
		- src
			- main
				- java
					- com.blog
						- controller
						- service
						- mapper
						- ……

---

在 ***blog_manegement*** 里添加 ***blog_utils*** 和 ***blog_pojo*** 依赖
```xml
<dependency>
	<groupId>com.blog</groupId>
	<artifactId>blog_pojo</artifactId>
	<version>1.0-SNAPSHOT</version>
</dependency>

<dependency>
	<groupId>com.blog</groupId>
	<artifactId>blog_utils</artifactId>
	<version>1.0-SNAPSHOT</version>
</dependency>
```

>[!warning] 分模块设计会引发一些问题，所以我们需要 <u>继承与聚合</u>
>- 各个模块引入了相同的依赖

## 继承
>Maven 继承同 Java 类似，描述了 Maven 项目之间的关系，使用 `<parent>……</parent>` 实现
>![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403061328780.png)

>[!warning] Maven 中项目只能 <u>单继承</u>【只能继承一个项目】

---

### 父工程
- 新建模块，选择 Maven 项目
- 父工程下不写代码，只进行子工程共用的依赖管理，~~所以可以把 `src` 目录直接删除~~
- 在设置父工程时，需要将打包方式设置为 `pom`【~~默认是 `jar`~~】
```xml
<packing>pom</packing>
```
- 指定 SpringBoot 父工程
```xml
// 这个父工程里面已经对 SpringBoot Web起步依赖做了统一管理
<parent>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-parent</artifactId>
	<version>3.2.3</version>
	<relativePath/> <!-- lookup parent from repository -->
</parent>
```

### 子工程
- **如果是次要项目**【比如 `pojo`，`utils`】，那就新建模块，选择 Maven 项目，选择父项![700](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403070914405.png)
- **如果是主项目**【`management`】，那就新建模块选择 Spring Initializr，再手动修改父工程的依赖
	```xml
	<parent>
		<groupId>com.blog</groupId>  
		<artifactId>blog-parent</artifactId>  
		<version>……</version>  
		<relativePath>../blog-parent/pom.xml</relativePath>  //指定父工程的pom文件位置
	</parent>
	```

>[!warning] 子工程会自动继承父工程的 `<groupId>`，子工程无需再添加 `<groupId>`

### 版本锁定
当拆分的模块越多，有部分模块需要用到某个依赖时，依赖的版本将变得难以管理，所以我们使用 ***版本锁定*** `<dependencyManagement>`

---

- 在父工程中版本锁定【***并没有将此依赖引入项目，只是如果子工程使用此依赖时，只能使用此版本***】
```xml
<dependencyManagement>
	<dependencies>
		<dependency>  
		    <groupId>org.mybatis.spring.boot</groupId>  
		    <artifactId>mybatis-spring-boot-starter</artifactId>  
		    <version>3.0.3</version>  
		</dependency>
	</dependencies>
</dependencyManagement>
```
- 在子工程中引入
```xml
<dependencies>
	<dependency>  
		<groupId>org.mybatis.spring.boot</groupId>  
		<artifactId>mybatis-spring-boot-starter</artifactId>  
	</dependency>
</dependencies>
```

## 聚合
- 在父工程下的 `pom.xml` 文件中指定 `<modules></modules>`
```xml
<modules>
	// module里写相对路径
	<module>blog-pojo</module>
	<module>blog-utils</module>
	<module>blog-management</module>
</modules>
```
- 直接在父工程下执行 `package`

---

>[!hint] 如果没有聚合，我们要将<u>除了主项目的所有模块</u>都一个一个执行 `install` 生命周期，安装到本地的 Maven 仓库，然后在主项目中执行 `package` 打包

## 私服
> 私服可以实现依赖的共享，当项目中引入依赖后，首先会到<u>本地仓库</u>中找依赖，找不到就会到<u>私服仓库</u>中找，还找不到就会到<u>中央仓库</u>中找

---

私服中有三种仓库：
- ***central 仓库*** ：里面存储了从中央仓库下载来的依赖
- ***RELEASE 仓库*** ：里面存储了发行版的相关依赖
- ***SNAPSHOT 仓库*** ：里面存储了测试版【功能不稳定】的相关依赖

---

![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403071340879.png)
### 上传
- 配置访问私服的用户名和密码
	- 找到 Maven 的安装目录里的 `setting.xml`
	- 找到里面的 `<servers>……</servers>` 标签
		```xml
		<servers>
			<server>
				<id>maven-releases</id>
				<username>admin</username>
				<password>123456</password>
			</server>
			
			<server>
				<id>maven-snapshots</id>
				<username>admin</username>
				<password>123456</password>
			</server>
		</servers>
		```



- 配置上传资源的目的地


### 下载











