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

>[!hint] 有时候，JSON 中的字段非常冗余，我们只需要将一小部分字段写入到 Java 对象中。这时，可以忽略额外的字段：
> ```java
>objectMapper.configure(DeserializationFeature.FAIL_ON_UNKNOWN_PROPERTIES, false);
> ```

## JSON -> Java 对象
### JSON 字符串 -> Java 对象
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

### JSON 输入流 -> Java 对象
- 字节流
```java
ObjectMapper objectMapper = new ObjectMapper();
 
InputStream input = new FileInputStream("data/car.json");
 
Car car = objectMapper.readValue(input, Car.class);
```

- 字符流
```java
ObjectMapper objectMapper = new ObjectMapper();
 
String carJson = "{ \"brand\" : \"Mercedes\", \"doors\" : 4 }";
Reader reader = new StringReader(carJson);

Car car = objectMapper.readValue(reader, Car.class);
```

### JSON 文件 -> Java 对象
- 本机文件
```java
ObjectMapper objectMapper = new ObjectMapper();
 
File file = new File("data/car.json");
 
Car car = objectMapper.readValue(file, Car.class);
```

- 网络文件
```java
ObjectMapper objectMapper = new ObjectMapper();
 
URL url = new URL("http://jenkov.com/some-data.json");
 
Car car = objectMapper.readValue(url, Car.class);
```

### JSON 二进制数组 -> Java 对象
```java
ObjectMapper objectMapper = new ObjectMapper();
 
String carJson = "{ \"brand\" : \"Mercedes\", \"doors\" : 5 }";
 
byte[] bytes = carJson.getBytes("UTF-8");
 
Car car = objectMapper.readValue(bytes, Car.class);
```

### JSON 字符串数组 -> Java 对象数组
```java
ObjectMapper objectMapper = new ObjectMapper();

String jsonArray = "[{\"brand\":\"ford\"}, {\"brand\":\"Fiat\"}]";

Car[] cars2 = objectMapper.readValue(jsonArray, Car[].class);
```

## JSON -> 集合
### JSON 字符串数组 -> List
```java
ObjectMapper objectMapper = new ObjectMapper();

String jsonArray = "[{\"brand\":\"ford\"}, {\"brand\":\"Fiat\"}]";
 
List<Car> cars1 = objectMapper.readValue(jsonArray, new TypeReference<List<Car>>(){});
```

### JSON 字符串数组 -> Map
```java
ObjectMapper objectMapper = new ObjectMapper();

String jsonObject = "{\"brand\":\"ford\", \"doors\":5}";
 
Map<String, Object> jsonMap = objectMapper.readValue(jsonObject, new TypeReference<Map<String,Object>>(){});
```

## Java 对象 -> JSON
- `writeValue()` 
- `writeValueAsString()` 将生成的 JSON 作为 `String` 返回
- `writeValueAsBytes()` 将生成的 JSON 作为字节数组返回

```java
ObjectMapper objectMapper = new ObjectMapper();
 
Car car = new Car();
car.setBrand("BMW");
car.setDoors(4);

// 将car对象序列化为JSON，并写入到名为 "data/output-2.json" 的文件中
objectMapper.writeValue(new FileOutputStream("data/output-2.json"), car);

// 将car对象序列化为JSON，并转换为String
String json = objectMapper.writeValueAsString(car);
System.out.println(json);
```




























