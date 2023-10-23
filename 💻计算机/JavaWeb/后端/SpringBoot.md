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
>***Apifox***
>Apifox是一款 API设计/开发/测试工具
##### 简单参数
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
##### 简单对象
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
##### 复杂参数
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
  
    public String getName() {  return name;  }  
    public void setName(String name) {  this.name = name;  }  
  
    public Integer getAge() {  return age;  }  
    public void setAge(Integer age) {  this.age = age;  }  
  
    public Address getAddress() {  return address;  }  
    public void setAddress(Address address) {  this.address = address;  }  
  
    @Override  
    public String toString() {  
        return "User{" +  
                "name='" + name + '\'' +  
                ", age=" + age +  
                ", address=" + address +  
                '}';  
    }  
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
##### 数组参数
GET请求：`http://localhost:8080/arrayParam?hobby=dance&hobby=game&hobby=sing`
```java
@RequestMapping("/arrayParam")  
public String ArrayParam(String[] hobby) {    //数组名与请求参数名相同
    System.out.println(Arrays.toString(hobby));  
    return "OK";  
}


[dance, game, sing]
```
##### 集合参数
GET请求：`http://localhost:8080/listParam?hobby=dance&hobby=game&hobby=sing`
```java
@RequestMapping("/listParam")  
public String ListParam(@RequestParam List<String> hobby) {  //需要添加RequestParam注解
    System.out.println(hobby);  
    return "OK";  
}


[dance, game, sing]
```
##### 日期参数
GET请求：`http://localhost:8080/dateParam?updateTime=2023-10-09 15:50:20`
```java
@RequestMapping("/dateParam")  
public String DateParam(@DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss") LocalDateTime updateTime) {         //添加注解来指定参数格式
    System.out.println(updateTime);  
    return "OK";  
}


2023-10-09T15:50:20
```
##### Json参数
POST请求：`http://localhost:8080/jsonParam`
```json
{
    "name":"Tom",
    "age":20,
    "address":{
        "province":"广东",
        "city":"广州"
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
##### 路径参数
GET请求：`http://localhost:8080/123`
```java
@RequestMapping("/{id}")  
public String PathParam(@PathVariable Integer id) {  //注解表示id是路径变量
    System.out.println(id);          //路径名与变量名要一致
    return "OK";  
}


123
```
### 响应
##### 首先包装一个Result类
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
##### 响应对象
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
##### 响应集合
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
### 分层
##### Dao
>Dao层的作用是获取数据【文件数据，xml数据，json数据等】

```java
package com.example.web_2.Dao;  

import java.util.List;  
  
public interface EmpDao {  //定义一个接口，固定格式
    public List<String> listEmp();  
}
```

```java
package com.example.web_2.Dao;  
  
import java.util.ArrayList;  
import java.util.List;  

//加载数据【文件数据，xml数据，json数据等】
public class EmpDaoA implements EmpDao {    
    @Override  
    public List<String> listEmp() {  
        List<String> list1 = new ArrayList(List.of("吴彦祖", "陈冠希", "金城武"));  
        return list1;  
    }  
}
```
##### Service
>Sevice层的作用是处理数据

```java
package com.example.web_2.Service;  
  
import java.util.List;  
  
public interface EmpServie {  
    public List<String> listEmp();  
}
```

```java
package com.example.web_2.Service;  
  
import com.example.web_2.Dao.EmpDao;  
import com.example.web_2.Dao.EmpDaoA;  
  
import java.util.List;  
  
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
```
##### Controller
>Controller的作用是响应数据给前端

```java
package com.example.web_2.Controller;  
  
import com.example.web_2.Pojo.Result;  
import com.example.web_2.Service.EmpServiceA;  
import com.example.web_2.Service.EmpServie;  
import org.springframework.web.bind.annotation.RequestMapping;  
import org.springframework.web.bind.annotation.RestController;  

import java.util.List;  
  
//获取Service发来的数据，并响应数据给前端  
@RestController  
public class EmpConteoller {  
    private EmpServie empServie = new EmpServiceA();  //创建EmpService对象
  
    @RequestMapping("/emp")  
    public Result listEmp() {  
        List<String> list = empServie.listEmp();  //获取Service处理过后的数据
        return Result.buildResult(Result.Status.OK, list);  //返回数据
    }  
}
```
---
GET请求：`http://localhost:8080/emp`
```json
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
### 解耦
>以上的分层方式，实现了***高内聚***，但是依然没有实现***低耦合***【Controller中还是有依赖Service，Service还是有依赖Dao】
##### 控制反转 IOC
>对象的创建控制权由程序自身转移到容器【本身由EmpController自身创建EmpService对象，变为由容器创建对象】

***添加***`@Component`***注释***
##### 依赖注入
>容器为应用程序提供运行时所依赖的资源【容器为EmpController提供运行时所需要的EmpService对象】

***添加***`@Autowired`***注释***

![[Excalidraw/计算机/JavaWeb Draw.md#^group=g1pvEhriTd5poW0zM1k4o|500]]

































