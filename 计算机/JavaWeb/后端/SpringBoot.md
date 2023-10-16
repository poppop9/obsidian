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
```java
@RestController  
public class RequestController {
	……
}
```
##### 响应字符串
```java
@RequestMapping("/string")  
public String string() {  
    System.out.println("hello web");  
    return "Hello Web";  
}


hello web
```


##### 响应对象



##### 响应集合









































