# 基本概念
>Spring是一个开发生态圈，它提供了若干个子项目，用于完成特定功能
>![[JavaWeb Draw#^group=Lu3xncQA90nuAeKIaESZ_]]
# 准备工作
## 创建Spring项目
- 创建Spring模块
	- 勾选Web开发相关依赖
	![[JavaWeb Draw#^group=dMXiaySV]]
	![[JavaWeb Draw#^group=qCHuJWbK]]
## 目录结构
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
## HTTP协议
- HTTP协议，一次请求对应一次响应
- HTTP协议每次请求和响应都是独立的，后一次请求无法知道前一次请求的数据
## Tomcat
>Tomcat是一款轻量级的Web服务器

SpringBoot的依赖项的起步依赖web【里面包含了很多依赖】中已经***内置了Tomcat***，当启动类运行时，会自动运行Tomcat服务器
![[JavaWeb Draw#^group=yrp52Usr]]

# 请求，响应，分层解耦
![[JavaWeb Draw#^group=tMdaT5BlcDIqJIyPd8ixX|770]]
## 请求
>***Apifox***
>Apifox是一款 API设计/开发/测试工具

`RequestMapping`的子集：
- `@GetMapping`  限定路径的请求方式只能是 HTTP GET
- `@PostMapping`  限定路径的请求方式只能是 HTTP POST
- `@PutMapping`：限定路径的请求方式只能是 HTTP PUT
- `@DeleteMapping`  限定路径的请求方式只能是 HTTP DELETE
……
### 简单参数
GET请求：`http://localhost:8080/simpleParam?name=Tom&age=10`
```java
@RestController  //注释@RestController，表示这是一个Controller类
public class RequestController {  
    @RequestMapping("/simpleParam")    //注释RequestMapping，定义请求路径
    public String simpleParam(String name, Integer age) {  
        System.out.println(name + ":" + age);         //变量名需要和请求参数名保持一致
        return "OK";  
    }  
}


Tom:10
```
***@RestController = @Controller + @ResponseBody***
### 简单对象
GET请求：`http://localhost:8080/simplePojo?name=Tom&age=20`
```java
@RestController  
public class RequestController {  
    @RequestMapping("/simplePojo")  
    public String simplePojo(User user) {  //把请求的参数封装成User对象
        System.out.print(user.name);  
        System.out.print(":");  
        System.out.print(user.age);  
        return "OK";  
    }  

    private class User {  //定义User对象
        String name;  
        Integer age;  //定义的变量需要与请求参数保持一致
  
        public String getName() {  return name;  }  
        public void setName(String name) {  this.name = name;  }  
        public Integer getAge() {  return age;  }  
        public void setAge(Integer age) {  this.age = age;  }  
    }  
}


Tom:20
```
### 复杂参数
GET请求：`http://localhost:8080/complexPojo?name=Tom&age=20&address.province=广东&address.city=广州`
```java
@RequestMapping("/complexPojo")  
public String complexPojo(User user) {  
    System.out.println(user);  
    return "OK";  
}


User{name='Tom', age=20, address=Address{province='广东', city='广州'}}
```

```java
public class User {  
    private String name;  
    Integer age;  
    Address address;  

	get，set方法
	toString方法
}
```

```java
public class Address {  
    String province;  
    String city;  
  
    public String getProvince() {  return province;  }  
  
    public void setProvince(String province) {  this.province = province;  }  
  
    public String getCity() {  return city;  }  
  
    public void setCity(String city) {  this.city = city;  }  
  
    @Override  
    public String toString() {  
        return "Address{" +  
                "province='" + province + '\'' +  
                ", city='" + city + '\'' +  
                '}';  
    }  
}
```
### 数组参数
GET请求：`http://localhost:8080/arrayParam?hobby=dance&hobby=game&hobby=sing`
```java
@RequestMapping("/arrayParam")  
public String ArrayParam(String[] hobby) {    //数组名与请求参数名相同
    System.out.println(Arrays.toString(hobby));  
    return "OK";  
}


[dance, game, sing]
```
### 集合参数
GET请求：`http://localhost:8080/listParam?hobby=dance&hobby=game&hobby=sing`
```java
@RequestMapping("/listParam")  
public String ListParam(@RequestParam List<String> hobby) {  //需要添加RequestParam注解
    System.out.println(hobby);  
    return "OK";  
}


[dance, game, sing]
```

`@RequestParam`***注解用于从请求的URL查询参数中获取值，并将其绑定到Controller类方法的参数上***，其属性可以指定参数是否是必需的；可以设置参数的默认值
### 日期参数
GET请求：`http://localhost:8080/dateParam?updateTime=2023-10-09 15:50:20`
```java
@RequestMapping("/dateParam")  
public String DateParam(@DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss") LocalDateTime updateTime) {         //添加注解来指定参数格式
    System.out.println(updateTime);  
    return "OK";  
}


2023-10-09T15:50:20
```
### Json参数
POST请求：`http://localhost:8080/jsonParam`
```json
{
    "name": "Tom",
    "age": 20,
    "address": {
        "province": "广东",
        "city": "广州"
    }
}
```

```java
@RequestMapping("/jsonParam")  
public String JsonParam(@RequestBody User user) {  //注解表示将json数据封装成对象
    System.out.println(user);  
    return "OK";  
}


User{name='Tom', age=20, address=Address{province='广东', city='广州'}}
```
### 路径参数
GET请求：`http://localhost:8080/123`
```java
@RequestMapping("/{id}")  
public String PathParam(@PathVariable Integer id) {  //注解表示id是路径变量
    System.out.println(id);          //路径名与变量名要一致
    return "OK";  
}


123
```
### 文件参数
#### MultipartFile
>`MultipartFile` ***是SpringBoot提供的保存文件的一种格式***

>[!summary] 方法
> - `getName()`  返回前端form表单的名称
> - `getOriginalFilename()`  获取源文件的昵称
> - `getContentType()`  返回文件的内容类型
> - `isEmpty()`  判断上传的文件是否有内容
> - `getSize()`  返回文件大小【单位为字节】
> - `getBytes()`  返回一个将文件内容转化成一个以byte为元素的数组
> - `getInputStream()`  返回InputStream读取文件的内容
> - `transferTo(File var1)`  复制file文件到指定位置

- 前端
```html
<form action="/upload" method="get" enctype="multipart/form-data">
	图像: <input type="file" name="image">
</form>
```

- 后端
```Properties
#在配置文件中限制上传文件的Size

#配置单个文件上传大小限制（默认值为1M）  
spring.servlet.multipart.max-file-size=10MB  
#配置单次请求上传文件总大小限制（默认值为10M）  
spring.servlet.multipart.max-request-size=100MB
```

```java
@RestController  
public class UploadController {  
    @PostMapping("/upload")  
    public Result UploadFile(MultipartFile image) throws IOException {  
	    //获取到image对象的文件名
        String originalFilename = image.getOriginalFilename();  
        //拿到文件名的最后一个.的索引
        int indexOf = originalFilename.lastIndexOf(".");  
        //获取到该文件的后缀名
        String suffixName = originalFilename.substring(indexOf);  

		//获取uuid
        String uuid = UUID.randomUUID().toString();  
        //拼接uuid和后缀名
        String newFileName = uuid + suffixName;  

		//将文件保存到指定路径
        image.transferTo(new File("E:/抖音/" + newFileName));  
  
        return Result.buildResult(Result.Status.OK);  
    }  
}
```



>[!hint] 文件通过MultipartFile传递到服务器后，会产生一个临时文件，如果这时不对文件做任何操作。只要请求响应完毕之后，***这个文件就会被自动删除，不会保存***
## 响应
### 首先包装一个Result类
```java
public class Result<T> {   
    private String status;      //状态码 
  
    public String getStatus() {      //获取状态  
        return status;  
    }  
   
    private String message;      //状态信息,错误描述 
    
    public String getMessage() {  //获取消息内容
        return message;  
    }  
   
    private T data;      //数据 
   
    public T getData() {  //获取数据内容
        return data;  
    }  
  
    private Result(String status, String message, T data) {  
        this.status = status;  
        this.message = message;  
        this.data = data;  
    }  
  
    private Result(String status, String message) {  
        this.status = status;  
        this.message = message;  
    }  
  
    private Result(String message) {  
        this.message = message;  
    }  
  
    //创建一个带有状态、消息和数据的结果对象 
    public static <T> Result<T> buildResult(Status status, String message, T data) {  
        return new Result<T>(status.getCode(), message, data);  
    }  
  
    //创建一个带有状态、消息和数据的结果对象
    public static <T> Result<T> buildResult(Status status, String message) {  
        return new Result<T>(status.getCode(), message);  
    }  
  
    // 创建一个带有状态和数据的结果对象
    public static <T> Result<T> buildResult(Status status, T data) {  
        return new Result<T>(status.getCode(), status.getReason(), data);  
    }  
  
    public static <T> Result<T> buildResult(Status status) {  
        return new Result<T>(status.getCode(), status.getReason());  
    }  
  
    public enum Status {  
        OK("200", "正确"),  
        BAD_REQUEST("400", "错误的请求"),  
        UNAUTHORIZED("401", "禁止访问"),  
        NOT_FOUND("404", "没有可用的数据"),  
        PWD_ERROR("300", "密码错误"),  
        EXIT("403", "已经存在"),  
        INTERNAL_SERVER_ERROR("500", "服务器遇到了一个未曾预料的状况"),  
        SERVICE_UNAVAILABLE("503", "服务器当前无法处理请求"),  
        ERROR("9999", "数据不能为空");  
  
        // 状态码,长度固定为6位的字符串.  
        private String code;  
  
        // 错误信息  
        private String reason;  
  
        Status(String code, String reason) {  
            this.code = code;  
            this.reason = reason;  
        }  
  
        public String getCode() {  
            return code;  
        }  
  
        public String getReason() {  
            return reason;  
        }  
  
        @Override  
        public String toString() {  
            return code + ": " + reason;  
        }  
    }  
}
```
### 响应对象
```java
@RequestMapping("/address")  
public Result<Address> address() {  
    Address address = new Address();  
    address.setProvince("广东");  
    address.setCity("广州");  
    return Result.buildResult(Result.Status.OK, address);  //传递状态码，数据
}
```
网页：
```
{
    "status": "200",
    "message": "正确",
    "data": {
        "province": "广东",
        "city": "广州"
    }
}
```
### 响应集合
```java
@RequestMapping("/list")  
public Result<List<Address>> list() {  
    List<Address> list = new ArrayList<>();  
    Address add1 = new Address();  
    add1.setProvince("广东");  
    add1.setCity("广州");  
  
    Address add2 = new Address();  
    add2.setProvince("福建");  
    add2.setCity("厦门");  
  
    list.add(add1);  
    list.add(add2);  
  
    return Result.buildResult(Result.Status.OK, list);  
}
```
网页：
```
{
    "status": "200",
    "message": "正确",
    "data": [
        {
            "province": "广东",
            "city": "广州"
        },
        {
            "province": "福建",
            "city": "厦门"
        }
    ]
}
```
## 分层
### Dao
>Dao层的作用是获取数据【文件数据，xml数据，json数据等】，==在MyBatis中叫Mapper==

```java
package com.example.web_2.Dao;  
  
public interface EmpDao {  //定义一个接口，固定格式
    public List<String> listEmp();  
}
```

```java
package com.example.web_2.Dao;  

//加载数据【文件数据，xml数据，json数据等】
public class EmpDaoA implements EmpDao {    
    @Override  
    public List<String> listEmp() {  
        List<String> list1 = new ArrayList(List.of("吴彦祖", "陈冠希", "金城武"));  
        return list1;  
    }  
}
```
### Service
>Sevice层的作用对数据进行处理，然后返回给Controller类

```java
package com.example.web_2.Service;  

public interface EmpServie {  
    public List<String> listEmp();  
}
```

```java
package com.example.web_2.Service;  
  
//对数据进行逻辑处理，返回给Controller类  
public class EmpServiceA implements EmpServie {  
    private EmpDao empDao = new EmpDaoA();  //需要从EmpDao获取数据，所以创建接口对象

    @Override  
    public List<String> listEmp() {  
        List<String> emplist = empDao.listEmp();  
        emplist.add("黎明");  //对数据进行处理【添加数据】
        return emplist;  
    }  
}

/*
使用private EmpDao empDao = new EmpDaoA();的方式是为了遵循编程中的"面向接口编程"原则，这样可以在需要时轻松替换具体的实现类，而无需修改EmpServiceA类的其他部分。这样，代码在处理empDao时只关注EmpDao接口定义的方法，而不依赖于具体的实现细节。

另外，通过使用依赖注入的设计模式，可以将EmpDao对象的创建和管理交给外部的代码（例如使用依赖注入容器或手动注入）。这样可以更好地解耦和组织代码，提高代码的可测试性和可维护性。
*/
```
### Controller
>Controller的作用是获取来自Service类发来的数据，响应数据给前端

```java
package com.example.web_2.Controller;  

//获取Service发来的数据，并响应数据给前端  
@RestController  
public class EmpController {  
    private EmpServie empServie = new EmpServiceA();  //创建EmpService对象
  
    @RequestMapping("/emp")  
    public Result listEmp() {  
        List<String> list = empServie.listEmp();  //获取Service处理过后的数据
        return Result.buildResult(Result.Status.OK, list);  //返回数据
    }  
}


---
GET请求：`http://localhost:8080/emp`
json：
{
    "status": "200",
    "message": "正确",
    "data": [
        "吴彦祖",
        "陈冠希",
        "金城武",
        "黎明"
    ]
}
```
#### 公共路径
>在类的头部指定`@RequestMapping`注解

```java
@RestController  
@RequestMapping("/user")             //指定公共路径
public class UserController {  
    @Autowired  
    private UserService us;  

    @PostMapping                   //表示路径为POST请求的/user
    public Result InsertUser(@RequestBody user user) {  
        us.InsertUser(user);  
        return Result.buildResult(Result.Status.OK);  
    }  
    
    @GetMapping("/1")              //表示路径为Get请求的/user/1
    public List<user> SelectUser(Integer id) {  
	    return ……
    }  
}
```
## 解耦
>以上的分层方式，实现了***高内聚***，但是依然没有实现***低耦合***【Controller中还是有依赖Service，Service还是有依赖Dao】
>![[Excalidraw/计算机/JavaWeb Draw.md#^group=g1pvEhriTd5poW0zM1k4o|500]]
>EmpController需要EmpService，那我们可以把EmpService放到IOC容器里，然后EmpController需要时就到容器中取
### 控制反转 IOC
>对象的创建控制权由程序自身转移到容器【本身由EmpController自身创建EmpService对象，变为由容器创建对象】

- ***添加***`@Component`***注释***【如果某个类不属于以下三类，但是也想交给IOC处理时使用】
	- 如果是控制器类上就用`@Controller`
	- 如果是逻辑处理Service类就用`@Service`
	- 如果是访问Dao类上就用`@Repository`，==如果Dao层中需要使用MyBatis，那要将`@Repository`注解改为`@Mapper`==
### 依赖注入 DI
>容器为应用程序提供运行时所依赖的资源【容器为EmpController提供运行时所需要的EmpService对象】

- ***添加***`@Autowired`***注释***【通过类型注入==单个注解中的单个依赖==】
- 添加`@Primary`注释【通过类型注入==多个注解中的单个依赖==】
	```java
	package com.example.web_2.Service;  
	  
	@Service
	public class EmpServiceA implements EmpServie {……}
	```
	```java
	package com.example.web_2.Service;  
	  
	@Primary  //表示优先这个Service类
	@Service  
	public class EmpServiceB implements EmpServie {……}
	```
- 添加`@Qualifier`注释【通过类型注入==多个注解中的单个依赖==】
	```java
	package com.example.web_2.Controller;  
	
	@RestController  
	public class EmpConteoller {  
		@Qualifier("empServiceB")  //指定使用的Bean对象的名称【默认为类名首字母小写】
		@Autowired  
		private EmpServie empServie;  
	  
		@RequestMapping("/emp")  
		public Result listEmp() {  
			List<String> list = empServie.listEmp();  
			return Result.buildResult(Result.Status.OK, list);  
		}  
	}
	```
- 添加`@Resource`注释【通过名称注入依赖】
	```java
	package com.example.web_2.Controller;  
	
	@RestController  
	public class EmpConteoller {  
	    @Resource(name = "empServiceB")  //直接指定Bean的名称
	    private EmpServie empServie;  
	  
	    @RequestMapping("/emp")  
	    public Result listEmp() {  
	        List<String> list = empServie.listEmp();  
	        return Result.buildResult(Result.Status.OK, list);  
	    }  
	}
	```

---

```java
@Repository  //将这个类交给IOC容器处理，成为IOC容器中的Bean
public class EmpDaoA implements EmpDao {  
    //加载数据【文件数据，xml数据，json数据等】  
    @Override  
    public List<String> listEmp() {  
        List<String> list1 = new ArrayList(List.of("吴彦祖", "陈冠希", "金城武"));  
        return list1;  
    }  
}
```

```java
package com.example.web_2.Service;  

@Service //将这个类交给IOC容器处理，成为IOC容器中的Bean  
public class EmpServiceA implements EmpServie {  
    @Autowired  //程序运行时，IOC容器会为这个变量提供Bean对象  
    private EmpDao empDao;  
  
    @Override  
    public List<String> listEmp() {  
        List<String> emplist = empDao.listEmp();  
        emplist.add("黎明");  
        return emplist;  
    }  
}
```

```java
@RestController  
public class EmpController {  
    @Autowired  //程序运行时，IOC容器会为这个变量提供Bean对象
    private EmpServie empServie;  
  
    @RequestMapping("/emp")  
    public Result listEmp() {  
        List<String> list = empServie.listEmp();  
        return Result.buildResult(Result.Status.OK, list);  
    }  
}
```
# 配置文件
## properties 配置文件
### 参数配置化
>将项目中的参数定义在 `properties文件中` 集中化管理，然后在java文件中使用 `@Value` 注解来注入配置文件中的值

- ***未采用参数配置化***
```java
@RestController
public class Test {
	public void test() {
		String secretId = "AKIDtlYAZjRbefnkT4Siz8Zz";  
		String secretKey = "IOQKLDty66wcBlDTh";
		String bucketName = "test-1307744200";
	}
}
```
【如果将参数分散在各个java类中，会导致***查找困难***，而且这种硬编码的方式，在***每次更改参数时都要重新编译项目***】

- ***采用参数配置化***
```java
public class Test {
	@Value("${tencent.secretId}")
	String secretId;

	@Value("${tencent.secretKey}")
	String secretKey;

	@Value("${tencent.bucketName}")
	String bucketName;
	
	public void test() {
		……
	}
}
```

```properties
tencent.secretId=AKIDtlYAZjRbefnkT4Siz8Zz  
tencent.secretKey=IOQKLDty66wcBlDTh  
tencent.bucketName=test-1307744200
```
## yml 配置文件
- 大小写敏感
- 数值前面必须有 `空格` 作为分割符
- `#` 表示注释
### 数据格式
- 对象 / Map集合
```yml
user:  
  name: "Ness"  
  style: "popping style"  
  age: 37
```

- 数组 / List集合 / Set集合
```yml
style:  
  - popping  
  - locking  
  - breaking  
  - house  
  - hip-hop
```
### @ConfigurationProperties
>使用该注释之后，会自动将配置文件中的值注入到bean对象对应的属性中去，***简化了每次注入yml里的数值都要使用 ***`@Value` ***的麻烦 ***

```properties
tencent.secretId=AKIDtlYAZjRbefnkT4Siz8Zz  
tencent.secretKey=IOQKLDty66wcBlDTh  
tencent.bucketName=test-1307744200
```

```java
@Data  //指定变量的get，set方法
@Component    //将这个类交给IOC容器管理
@ConfigurationProperties(prefix = "tencent")  //指定属性值的前缀
public class Test1 {
	String secretId;
	String secretKey;
	String bucketName;
}
```

```java
public class Test2 {
	@Autowired
	private Test1 t1;

	public void summart(){
		String secretId = t1.getSecretId;
		String secretKey = t1.getSecretKey;
		String bucketName = t1.getBucketName;
		……
	}
}
```


---

>[!hint] properties 对比 yml
>- properties
> ```properties
> spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
> spring.datasource.url=jdbc:mysql://localhost:3306/mybatis
> spring.datasource.username=root
> spring.datasource.password=13433026660
> 
> spring.servlet.multipart.max-file-size=10MB
> spring.servlet.multipart.max-request-size=100MB
> 
> mybatis.configuration.map-underscore-to-camel-case=true
> mybatis.configuration.log-impl=org.apache.ibatis.logging.stdout.StdOutImpl
> 
> tencent.secretId=AKIDtlYAZjgQwiMmzxhDi7RbefnkT4Siz8Zz
> tencent.secretKey=IOQKLDtOirptnjbN0Tkooqy66wcBlDTh
> tencent.bucketName=test-1307744200
> ```
>- yml
> ```yml
> spring:
>   #数据库连接信息
>   datasource:
>     driver-class-name: com.mysql.cj.jdbc.Driver
>     url: jdbc:mysql://localhost:3306/mybatis
>     username: root
>     password: 13433026660
>   #文件上传撇配置
>   servlet:
>     multipart:
>       max-file-size: 10MB
>       max-request-size: 100MB
> 
> #mybatis配置
> mybatis:
>   configuration:
>     map-underscore-to-camel-case: true
>     log-impl: org.apache.ibatis.logging.stdout.StdOutImpl
> 
> #腾讯云对象存储
> tencent:
>   secretId: AKIDtlYAZjgQwiMmzxhDi7RbefnkT4Siz8Zz
>   secretKey: IOQKLDtOirptnjbN0Tkooqy66wcBlDTh
>   bucketName: test-1307744200
> ```
# 依赖
## lombok
>Lombok是一种Java库，它通过注解的方式来简化Java类的编写，提高代码的可读性和简洁性
### 引入lombok依赖
```xml  
<dependency>  
    <groupId>org.projectlombok</groupId>  
    <artifactId>lombok</artifactId>   
</dependency>           //不用指定版本号，因为在SpringBoot的父工程里已经集成了lombok
```
### 具体操作
`@Getter/@Setter`  为所有属性提供get/set方法
`@ToString`  给类自动生成的toString方法
`@EqualsAndHashCode`  根据类所拥有的非静态字段重写equals方法和hashCode方法
`@Data`  是@Getter+@Setter+@ToString+@EqualsAndHashCode的集合
`@NoArgsConstructor`  为实体类生成无参构造方法
`@AllArgsConstructor`  为实体类生成除了static修饰的字段之外带有所有参数的构造方法

- 未使用lombok
	```java
	public class user {  
	    private Integer id;  
	    private String name;  
	    private Integer age;  
	    private Integer gender;  
	    private String phone;  
	  
	    public user() {  }  
	  
	    public user(Integer id, String name, Integer age, Integer gender, String phone) {  
	        this.id = id;  
	        this.name = name;  
	        this.age = age;  
	        this.gender = gender;  
	        this.phone = phone;  
	    }  
	  
	    public Integer getId() {  return id;  }  
	    public void setId(Integer id) {  this.id = id;  }  
	  
	    public String getName() {  return name;  }  
	    public void setName(String name) {  this.name = name;  }  
	  
	    public Integer getAge() {  return age;  }  
	    public void setAge(Integer age) {  this.age = age;  }  
	  
	    public Integer getGender() {  return gender;  }  
	    public void setGender(Integer gender) {  this.gender = gender;  }  
	  
	    public String getPhone() {  return phone;  }  
	    public void setPhone(String phone) {  this.phone = phone;  }  
	  
	    @Override  
	    public String toString() {  
	        return "user{" +  
	                "id=" + id +  
	                ", name='" + name + '\'' +  
	                ", age=" + age +  
	                ", gender=" + gender +  
	                ", phone='" + phone + '\'' +  
	                '}';  
	    }  
	}
	```
- 使用lombok
	```java
	import lombok.*;  
	  
	@Getter  
	@Setter  
	@ToString  
	@NoArgsConstructor  
	@AllArgsConstructor  
	public class user {  
	    private Integer id;  
	    private String name;  
	    private Integer age;  
	    private Integer gender;  
	    private String phone;  
	}
	```
# 异常处理
>通过定义<u>全局异常处理器</u>来统一处理三层架构抛出的异常

- `@RestControllerAdvice` 
```java
package com.example.exception;

@RestControllerAdvice  //表示这是一个全局异常处理器
public class GlobalExceptionHandle {
    @ExceptionHandler(Exception.class)  //Exception.class表示要捕获所有的异常
    public Result ex(Exception ex) {
        return Result.buildResult(Result.Status.UNAUTHORIZED, "禁止访问", "http://localhost:7000/Exception#/Exception");
    }
}
```











