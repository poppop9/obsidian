```xml
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.17.0</version>
</dependency>
```

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

# JsonNode 树模型
>树模型 由 JsonNode 类表示，可用于表示 JSON 对象

>[!hint] 什么时候使用<u>树模型</u> ?
>- 不知道接收到的 JSON 格式
>- 不想多创建一个类

## 创建树模型
```java
ObjectMapper objectMapper = new ObjectMapper();

String carJson = "{ \"brand\" : \"Mercedes\", \"doors\" : 5 }";

try {
	JsonNode jsonNode = objectMapper.readValue(carJson, JsonNode.class);
} catch (IOException e) {
	e.printStackTrace();
}
```

## 浏览树模型
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

## Java 对象 -> JsonNode
```java
ObjectMapper objectMapper = new ObjectMapper();

Car car = new Car();
car.brand = "Cadillac";
car.doors = 4;

JsonNode carJsonNode = objectMapper.valueToTree(car);
```

## JsonNode -> Java 对象
```java
ObjectMapper objectMapper = new ObjectMapper();

String carJson = "{ \"brand\" : \"Mercedes\", \"doors\" : 5 }";

JsonNode carJsonNode = objectMapper.readValue(carJson, JsonNode.class);

Car car = objectMapper.treeToValue(carJsonNode);
```

# ObjectNode 子树模型
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

# 注解
- `@JsonProperty` 在序列化时，转换属性的名称
```java
@JsonProperty("birth_date")
private Date birthDate;
```
---
- `@JsonFormat` 在序列化时，转换属性/方法返回值的格式
```java
@JsonFormat(timezone = "GMT+8", pattern = "yyyy-MM-dd HH:mm")
public Date getBirthDate()
```
---
- `@JsonPropertyOrder` 用于类，指定属性在序列化时 JSON 中的顺序
```java
@JsonPropertyOrder({ "birth_date", "name" }) 
public class Person
```
---
- `@JsonCreator` 用于有参构造方法，和 `@JsonProperty` 配合使用
```java
@JsonCreator 
public Person(@JsonProperty("name") String name) {…}
```
---
- `@JsonAnySetter` 用于属性或者方法，接收未知属性的键值对
```java
// 如果 JSON 中包含了额外属性，这些额外属性会被动态地添加到Map集合中
@JsonAnySetter 
public void set(String key, Object value) {   
	map.put(key, value); 
}
```

## 读写注解
>读写注解表示在序列化，和反序列化时都生效

### @JsonIgnore
`@JsonIgnore` 用于忽略 Java 对象的某个属性

```java
public class PersonIgnore {
	// 不会从JSON读取属性personId，和写入JSON属性personId
    @JsonIgnore
    public long personId = 0;
    public String name = null;
}
```

### @JsonIgnoreProperties
`@JsonIgnoreProperties` 用于指定要忽略的类的属性列表

```java
// 属性 firstName 和 lastName 都将被忽略
@JsonIgnoreProperties({"firstName", "lastName"})
public class PersonIgnoreProperties {
    public long personId = 0;
    public String firstName = null;
    public String lastName = null;
}
```

### @JsonIgnoreType
`@JsonIgnoreType` 忽略整个类

```java
public class PersonIgnoreType {
    @JsonIgnoreType
    public static class Address {
        public String streetName = null;
        public String houseNumber = null;
        public String zipCode = null;
        public String city = null;
        public String country = null;
    }

    public long personId = 0;
    public String name = null;
    public Address address = null;
}
```

## 读注解
>读注解只有在<u>反序列化</u>时生效

### @JsonSetter
`@JsonSetter` 将 `setter方法` 的名称与 JSON 数据中的属性名匹配

```json
{
  "id": 1234,
  "name": "John"
}
```

```typescript
import com.fasterxml.jackson.annotation.JsonSetter;

public class Person {
    private long personId = 0;
    private String name = null;

    public long getPersonId() {
        return this.personId;
    }

    @JsonSetter("id")
    public void setPersonId(long personId) {
        this.personId = personId;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

### @JsonAnySetter
`@JsonAnySetter` 为JSON对象中所有无法识别的字段调用相同的setter方法。 “无法识别”是指尚未映射到Java对象中的属性或设置方法的所有字段。

看一下这个Bag类：

```typescript
public class Bag {     private Map<String, Object> properties = new HashMap<>();     public void set(String fieldName, Object value){        this.properties.put(fieldName, value);    }     public Object get(String fieldName){        return this.properties.get(fieldName);    }}复制代码
```

然后查看此JSON对象：

```cobol
{  "id"   : 1234,  "name" : "John"}复制代码
```

Jackson无法直接将此JSON对象的id和name属性映射到Bag类，因为Bag类不包含任何公共字段或setter方法。

可以通过添加@JsonAnySetter注解来告诉Jackson为所有无法识别的字段调用set()方法，如下所示：

```typescript
public class Bag {     private Map<String, Object> properties = new HashMap<>();     @JsonAnySetter    public void set(String fieldName, Object value){        this.properties.put(fieldName, value);    }     public Object get(String fieldName){        return this.properties.get(fieldName);    }}复制代码
```

现在，Jackson将使用JSON对象中所有无法识别的字段的名称和值调用set()方法。

请记住，这仅对无法识别的字段有效。 例如，如果您向Bag Java类添加了公共名称属性或setName（String）方法，则JSON对象中的名称字段将改为映射到该属性/设置器。

#### 3、@JsonCreator

Jackson注解@JsonCreator用于告诉Jackson该Java对象具有一个构造函数（“创建者”），该构造函数可以将JSON对象的字段与Java对象的字段进行匹配。

@JsonCreator注解在无法使用@JsonSetter注解的情况下很有用。 例如，不可变对象没有任何设置方法，因此它们需要将其初始值注入到构造函数中。

以这个PersonImmutable类为例：

```csharp
public class PersonImmutable {     private long   id   = 0;    private String name = null;     public PersonImmutable(long id, String name) {        this.id = id;        this.name = name;    }     public long getId() {        return id;    }     public String getName() {        return name;    } }复制代码
```

要告诉Jackson应该调用PersonImmutable的构造函数，我们必须在构造函数中添加@JsonCreator注解。 但是，仅凭这一点还不够。 我们还必须注解构造函数的参数，以告诉Jackson将JSON对象中的哪些字段传递给哪些构造函数参数。

添加了@JsonCreator和@JsonProperty注解的PersonImmutable类的示例如下：

```typescript
public class PersonImmutable {     private long   id   = 0;    private String name = null;     @JsonCreator    public PersonImmutable(            @JsonProperty("id")  long id,            @JsonProperty("name") String name  ) {         this.id = id;        this.name = name;    }     public long getId() {        return id;    }     public String getName() {        return name;    } }复制代码
```

请注意，构造函数上方的注解以及构造函数参数之前的注解。 现在，Jackson能够从此JSON对象创建PersonImmutable：

```cobol
{  "id"   : 1234,  "name" : "John"}复制代码
```

#### 4、@JacksonInject

Jackson注解@JacksonInject用于将值注入到解析的对象中，而不是从JSON中读取这些值。 例如，假设正在从各种不同的源下载Person JSON对象，并且想知道给定Person对象来自哪个源。 源本身可能不包含该信息，但是可以让Jackson将其注入到根据JSON对象创建的Java对象中。

要将Java类中的字段标记为需要由Jackson注入其值的字段，请在该字段上方添加@JacksonInject注解。

这是一个示例PersonInject类，在属性上方添加了@JacksonInject注解：

```java
public class PersonInject {     public long   id   = 0;    public String name = null;     @JacksonInject    public String source = null; }复制代码
```

为了让Jackson将值注入属性，需要在创建Jackson ObjectMapper时做一些额外的工作。

这是让Jackson将值注入Java对象的过程：

```vbnet
InjectableValues inject = new InjectableValues.Std().addValue(String.class, "jenkov.com");PersonInject personInject = new ObjectMapper().reader(inject)                        .forType(PersonInject.class)                        .readValue(new File("data/person.json"));复制代码
```

请注意，如何在InjectableValues addValue()方法中设置要注入到source属性中的值。 还要注意，该值仅绑定到字符串类型-而不绑定到任何特定的字段名称。 @JacksonInject注解指定将值注入到哪个字段。

如果要从多个源下载人员JSON对象，并为每个源注入不同的源值，则必须为每个源重复以上代码。

#### 5、@JsonDeserialize

Jackson注解@JsonDeserialize用于为Java对象中给定的属性指定自定义反序列化器类。

例如，假设想优化布尔值false和true的在线格式，使其分别为0和1。

首先，需要将@JsonDeserialize注解添加到要为其使用自定义反序列化器的字段。 这是将@JsonDeserialize注解添加到字段的示例：

```java
public class PersonDeserialize {     public long    id      = 0;    public String  name    = null;     @JsonDeserialize(using = OptimizedBooleanDeserializer.class)    public boolean enabled = false;}复制代码
```

其次，这是@JsonDeserialize注解中引用的OptimizedBooleanDeserializer类的实例：

```kotlin
public class OptimizedBooleanDeserializer    extends JsonDeserializer<Boolean> {     @Override    public Boolean deserialize(JsonParser jsonParser,            DeserializationContext deserializationContext) throws        IOException, JsonProcessingException {         String text = jsonParser.getText();        if("0".equals(text)) return false;        return true;    }}复制代码
```

请注意，OptimizedBooleanDeserializer类使用通用类型Boolean扩展了JsonDeserializer。 这样做会使deserialize()方法返回一个布尔对象。 如果要反序列化其他类型（例如java.util.Date），则必须在泛型括号内指定该类型。

可以通过调用jsonParser参数的getText()方法来获取要反序列化的字段的值。 然后，可以将该文本反序列化为任何值，然后输入反序列化程序所针对的类型（在此示例中为布尔值）。

最后，需要查看使用自定义反序列化器和@JsonDeserializer注解反序列化对象的格式：

```cobol
PersonDeserialize person = objectMapper        .reader(PersonDeserialize.class)        .readValue(new File("data/person-optimized-boolean.json"));复制代码
```

注意，我们首先需要如何使用ObjectMapper的reader()方法为PersonDeserialize类创建一个阅读器，然后在该方法返回的对象上调用readValue()。

### 三）、Write注解

Jackson还包含一组注解，这些注解可以影响Jackson将Java对象序列化（写入）到JSON的方式。 以下各节将介绍这些写（序列化）注解中的每一个。

#### 1、@JsonInclude

Jackson注解@JsonInclude告诉Jackson仅在某些情况下包括属性。 例如，仅当属性为非null，非空或具有非默认值时，才应包括该属性。 这是显示如何使用@JsonInclude注解的示例：

```kotlin
import com.fasterxml.jackson.annotation.JsonInclude; @JsonInclude(JsonInclude.Include.NON_EMPTY)public class PersonInclude {     public long  personId = 0;    public String name     = null; }复制代码
```

如果为该示例设置的值是非空的，则此示例将仅包括name属性，这意味着不为null且不是空字符串。

@JsonInclude注解的一个更通俗的名称应该是@JsonIncludeOnlyWhen，但是写起来会更长。

#### 2、@JsonGetter

@JsonGetter Jackson注解用于告诉Jackson，应该通过调用getter方法而不是通过直接字段访问来获取某个字段值。 如果您的Java类使用jQuery样式的getter和setter名称，则@JsonGetter注解很有用。

例如，您可能拥有方法personId()和personId（long id），而不是getPersonId()和setPersonId()。

这是一个名为PersonGetter的示例类，它显示了@JsonGetter注解的用法：

```kotlin
public class PersonGetter {     private long  personId = 0;     @JsonGetter("id")    public long personId() { return this.personId; }     @JsonSetter("id")    public void personId(long personId) { this.personId = personId; } }复制代码
```

如您所见，personId()方法带有@JsonGetter注解。 @JsonGetter注解上设置的值是JSON对象中应使用的名称。 因此，用于JSON对象中personId的名称是id。 生成的JSON对象如下所示：

```cobol
{"id":0}复制代码
```

还要注意，personId（long personId）方法使用@JsonSetter注解进行注解，以使Jackson识别为与JSON对象中的id属性匹配的设置方法。 从JSON读取Java对象时使用@JsonSetter注解-将Java对象写入JSON时不使用。 为了完整起见，仅包含@JsonSetter注解。

#### 3、@JsonAnyGetter

@JsonAnyGetter Jackson注解使您可以将Map用作要序列化为JSON的属性的容器。 这是在Java类中使用@JsonAnyGetter注解的示例：

```typescript
public class PersonAnyGetter {     private Map<String, Object> properties = new HashMap<>();     @JsonAnyGetter    public Map<String, Object> properties() {        return properties;    }}复制代码
```

当看到@JsonAnyGetter注解时，Jackson将从@JsonAnyGetter注解的方法中获取返回的Map，并将该Map中的每个键值对都视为一个属性。 换句话说，Map中的所有键值对都将作为PersonAnyGetter对象的一部分序列化为JSON。

#### 4、@JsonPropertyOrder

@JsonPropertyOrder Jackson注解可用于指定将Java对象的字段序列化为JSON的顺序。 这是显示如何使用@JsonPropertyOrder注解的示例：

```kotlin
@JsonPropertyOrder({"name", "personId"})public class PersonPropertyOrder {     public long  personId  = 0;    public String name     = null; }复制代码
```

通常，Jackson会按照在类中找到的顺序序列化PersonPropertyOrder中的属性。 但是，@JsonPropertyOrder注解指定了不同的顺序，在序列化的JSON输出中，name属性将首先出现，personId属性将随后出现。

#### 5、@JsonRawValue

@JsonRawValue Jackson注解告诉Jackson该属性值应直接写入JSON输出。 如果该属性是字符串，Jackson通常会将值括在引号中，但是如果使用@JsonRawValue属性进行注解，Jackson将不会这样做。

为了更清楚@JsonRawValue的作用，看看没有使用@JsonRawValue的此类：

```java
public class PersonRawValue {     public long   personId = 0;     public String address  = "$#";}复制代码
```

Jackson会将其序列化为以下JSON字符串：

```bash
{"personId":0,"address":"$#"}复制代码
```

现在，我们将@JsonRawValue添加到address属性，如下所示：

```java
public class PersonRawValue {     public long   personId = 0;     @JsonRawValue    public String address  = "$#";}复制代码
```

现在，当对地址属性进行序列化时，杰克逊将省略引号。 因此，序列化的JSON如下所示：

```csharp
{"personId":0,"address":$#}复制代码
```

当然它是无效的JSON，那么为什么要这么做呢？

如果address属性包含一个JSON字符串，那么该JSON字符串将被序列化为最终的JSON对象，作为JSON对象结构的一部分，而不仅是序列化为JSON对象的address字段中的字符串。

要查看其工作原理，让我们像下面这样更改address属性的值：

```swift
public class PersonRawValue {     public long   personId = 0;     @JsonRawValue    public String address  =            "{ \"street\" : \"Wall Street\", \"no\":1}"; }复制代码
```

Jackson会将其序列化为以下JSON：

```cobol
{"personId":0,"address":{ "street" : "Wall Street", "no":1}}复制代码
```

请注意，JSON字符串现在如何成为序列化JSON结构的一部分。

没有@JsonRawValue注解，Jackson会将对象序列化为以下JSON：

```swift
{"personId":0,"address":"{ \"street\" : \"Wall Street\", \"no\":1}"}复制代码
```

请注意，address属性的值现在如何用引号引起来，并且值内的所有引号均被转义。

#### 6、@JsonValue

Jackson注解@JsonValue告诉Jackson，Jackson不应该尝试序列化对象本身，而应在对象上调用将对象序列化为JSON字符串的方法。 请注意，Jackson将在自定义序列化返回的String内转义任何引号，因此不能返回例如 完整的JSON对象。 为此，应该改用@JsonRawValue（请参阅上一节）。

@JsonValue注解已添加到Jackson调用的方法中，以将对象序列化为JSON字符串。 这是显示如何使用@JsonValue注解的示例：

```typescript
public class PersonValue {     public long   personId = 0;    public String name = null;     @JsonValue    public String toJson(){        return this.personId + "," + this.name;    } }复制代码
```

要求Jackson序列化PersonValue对象所得到的输出是：

```csharp
"0,null"复制代码
```

引号由Jackson添加。 请记住，对象返回的值字符串中的所有引号均会转义。

#### 7、@JsonSerialize

@JsonSerialize Jackson注解用于为Java对象中的字段指定自定义序列化程序。 这是一个使用@JsonSerialize注解的Java类示例：

```java
public class PersonSerializer {     public long   personId = 0;    public String name     = "John";     @JsonSerialize(using = OptimizedBooleanSerializer.class)    public boolean enabled = false;}复制代码
```

注意启用字段上方的@JsonSerialize注解。

OptimizedBooleanSerializer将序列的真值序列化为1，将假值序列化为0。这是代码：

```scala
public class OptimizedBooleanSerializer extends JsonSerializer<Boolean> {     @Override    public void serialize(Boolean aBoolean, JsonGenerator jsonGenerator,         SerializerProvider serializerProvider)     throws IOException, JsonProcessingException {         if(aBoolean){            jsonGenerator.writeNumber(1);        } else {            jsonGenerator.writeNumber(0);        }    }}复制代码
```









