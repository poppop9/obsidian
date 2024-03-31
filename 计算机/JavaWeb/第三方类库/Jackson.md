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

>[!warning] Jackson 的日期转换
>Jackson 默认会将 `java.util.Date` 对象序列化为 `long` 毫秒数。但是，我们大多数时候希望能将 `java.util.Date` 转换为日期格式的字符串
>
> - 默认
> ```java
> ObjectMapper objectMapper = new ObjectMapper();
> 
> Transaction transaction = new Transaction("transfer", new Date());
> 
> String output = objectMapper.writeValueAsString(transaction);
> System.out.println(output);
> ```
> 
> - 改进
> ```java
> ObjectMapper objectMapper = new ObjectMapper();
> 
> Transaction transaction = new Transaction("transfer", new Date());
> 
> // 设置日期格式
> SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd");
> // 在objectMapper中设置日期格式
> objectMapper.setDateFormat(dateFormat);
> 
> String output2 = objectMapper.writeValueAsString(transaction);
> System.out.println(output2);
> ```

## JsonNode 树模型
>树模型 由 JsonNode 类表示，可用于表示 JSON 对象

>[!hint] 什么时候使用<u>树模型</u> ?
>- 不知道接收到的 JSON 格式
>- 不想多创建一个类

### 创建树模型
```java
ObjectMapper objectMapper = new ObjectMapper();

String carJson = "{ \"brand\" : \"Mercedes\", \"doors\" : 5 }";

try {
	JsonNode jsonNode = objectMapper.readValue(carJson, JsonNode.class);
} catch (IOException e) {
	e.printStackTrace();
}
```

### 浏览树模型
- 获取字段
	- `JsonNode.get("字段名")` <u>根据字段名</u>获取 JSON 的字段
	- `JsonNode.at("JSON 路径")` 根据路径获取 JSON 的字段【例如 `/nestedObject/value`】
- 获取字段里的内容
	- `jsonNode.get("字段名").asText();` 获取对应字段的内容为 `String`
	- `jsonNode.get("字段名").asDouble();` 获取对应字段的内容为 `double`
	- `jsonNode.get("字段名").asInt();` 获取对应字段的内容为 `int`
	- `jsonNode.get("字段名").asLong();` 获取对应字段的内容为 `long`


```java
ObjectMapper objectMapper = new ObjectMapper();

String carJson =
        "{ \"brand\" : \"Mercedes\", \"doors\" : 5," +
        "  \"owners\" : [\"John\", \"Jack\", \"Jill\"]," +
        "  \"nestedObject\" : { \"field\" : \"value\" } }";

try {
    JsonNode jsonNode = objectMapper.readValue(carJson, JsonNode.class);

	// 访问 JSON 字段
    JsonNode brandNode = jsonNode.get("brand");
    String brand = brandNode.asText();
    System.out.println("brand = " + brand);
 
    JsonNode doorsNode = jsonNode.get("doors");
    int doors = doorsNode.asInt();
    System.out.println("doors = " + doors);

	// 访问 JSON 数组
    JsonNode array = jsonNode.get("owners");
    JsonNode jsonNode = array.get(0);
    String john = jsonNode.asText();
    System.out.println("john  = " + john);

	// 访问 JSON 嵌套对象
    JsonNode child = jsonNode.get("nestedObject");
    JsonNode childField = child.get("field");
    String field = childField.asText();
    System.out.println("field = " + field);
 
} catch (IOException e) {
    e.printStackTrace();
}
```

### Java 对象 -> JsonNode
```java
ObjectMapper objectMapper = new ObjectMapper();

Car car = new Car();
car.brand = "Cadillac";
car.doors = 4;

JsonNode carJsonNode = objectMapper.valueToTree(car);
```

### JsonNode -> Java 对象
```java
ObjectMapper objectMapper = new ObjectMapper();

String carJson = "{ \"brand\" : \"Mercedes\", \"doors\" : 5 }";

JsonNode carJsonNode = objectMapper.readValue(carJson, JsonNode.class);

Car car = objectMapper.treeToValue(carJsonNode);
```

## ObjectNode 子树模型
>[!hint] JsonNode 里的属性是不可修改的，所以引入 ObjectNode，ObjectNode 是 JsonNode 的子类

- 创建 ObjectNode
```java
// 创建 ObjectMapper 对象 
ObjectMapper objectMapper = new ObjectMapper(); 

String jsonData = "{\"name\":\"Alice\",\"age\":20,\"courses\":[\"Math\",\"Physics\",\"Biology\"],\"grades\":{\"Math\":85,\"Physics\":90,\"Biology\":75}}"; 

// 将 JSON 数据解析为 ObjectNode 对象 
ObjectNode objectNode = (ObjectNode) objectMapper.readValue(jsonData, JsonNode.class);
```

- 添加 / 修改
```java
// 如果ObjectNode中没有 'field1' 字段，那就向 `ObjectNode` 中添加一个 "field1" 字段，并将字符串 "value1" 作为它的值
// 如果ObjectNode中存在 'field1' 字段，那就修改其值
objectNode.put("Math", "value1");
```

- 删除
```java
objectNode.remove("Math");
```

- 迭代
```java
// 生成迭代器
Iterator<String> fieldNames = jsonNode.fieldNames();

while(fieldNames.hasNext()) {
    String fieldName = fieldNames.next();

	// 通过迭代器找到的字段名，创建字段JsonNode
    JsonNode field = jsonNode.get(fieldName);
}
```










