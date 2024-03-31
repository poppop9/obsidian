```xml
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.17.0</version>
</dependency>
```

# 基本概念
- 序列化：将 Java 对象转换为 Json 格式的字符串
- 反序列化：将 JSON 格式的字符串转换回对应的 Java 对象


# ObjectMapper
> ObjectMapper 可以序列化和反序列化 JSON

## JSON 字符串 -> Java 对象
```java
// Car 类
public class Car {
	private String brand = null;
    private int doors = 0;

	// get，set 方法
}
```

```java
// 创建 ObjectMapper 对象
ObjectMapper objectMapper = new ObjectMapper();

String carJson ="{ \"brand\" : \"Mercedes\", \"doors\" : 5 }";

try {
	Car car = objectMapper.readValue(carJson, Car.class);
	
	System.out.println("car brand = " + car.getBrand());
	System.out.println("car doors = " + car.getDoors());
} catch (IOException e) {
	e.printStackTrace();
}
```

>[!hint] Jackson 如何匹配 JSON 字段和 Java 对象的属性
>- JSON 字段中的 `brand` 与Java 对象中的 `getBrand()` ，`setBrand()` 匹配
>
>>如果需要以其他方式将 JSON 字段与 Java 对象属性匹配，需要使用自定义序列化器和反序列化器，或者使用 Jackson 注解

## JSON 输入流 -> Java 对象
```java
ObjectMapper objectMapper = new ObjectMapper();
 
String carJson = "{ \"brand\" : \"Mercedes\", \"doors\" : 4 }";
Reader reader = new StringReader(carJson);
 
Car car = objectMapper.readValue(reader, Car.class);
```



































