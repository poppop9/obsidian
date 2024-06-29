```xml  
// 不用指定版本号，因为在SpringBoot的父工程里已经集成了lombok
<dependency>  
    <groupId>org.projectlombok</groupId>  
    <artifactId>lombok</artifactId>   
</dependency>           
```

>[!quote] Lombok
>Lombok 可以通过注解来简化 Java 类的编写，提高代码的可读性和简洁性

---

>[!hint]+ 未使用 lombok
> ```java
> public class user {  
> 	private Integer id;  
> 	private String name;  
> 	private Integer age;  
> 	private Integer gender;  
> 	private String phone;  
>   
> 	public user() {  }  
>   
> 	public user(Integer id, String name, Integer age, Integer gender, String phone) {  
> 		this.id = id;  
> 		this.name = name;  
> 		this.age = age;  
> 		this.gender = gender;  
> 		this.phone = phone;  
> 	}  
>   
> 	public Integer getId() {  return id;  }  
> 	public void setId(Integer id) {  this.id = id;  }  
>   
> 	public String getName() {  return name;  }  
> 	public void setName(String name) {  this.name = name;  }  
>   
> 	public Integer getAge() {  return age;  }  
> 	public void setAge(Integer age) {  this.age = age;  }  
>   
> 	public Integer getGender() {  return gender;  }  
> 	public void setGender(Integer gender) {  this.gender = gender;  }  
>   
> 	public String getPhone() {  return phone;  }  
> 	public void setPhone(String phone) {  this.phone = phone;  }  
>   
> 	@Override  
> 	public String toString() {  
> 		return "user{" +  
> 				"id=" + id +  
> 				", name='" + name + '\'' +  
> 				", age=" + age +  
> 				", gender=" + gender +  
> 				", phone='" + phone + '\'' +  
> 				'}';  
> 	}  
> }
> ```

>[!hint]+ 使用 lombok
> ```java
> import lombok.*;  
>   
> @Getter  
> @Setter  
> @ToString  
> @NoArgsConstructor  
> @AllArgsConstructor  
> public class user {  
> 	private Integer id;  
> 	private String name;  
> 	private Integer age;  
> 	private Integer gender;  
> 	private String phone;  
> }
> ```

# 注解
## get，set，toString，equals
- `@Data`  是 @Getter+@Setter+@ToString+@EqualsAndHashCode 的集合
	- `@Getter/@Setter`  为所有属性提供 get/set 方法
	- `@ToString`  给类自动生成的 toString 方法
	- `@EqualsAndHashCode`  根据类所拥有的非静态字段重写 equals 方法和 hashCode 方法

## 构造方法
- `@NoArgsConstructor`  为实体类生成无参构造方法
- `@AllArgsConstructor`  为实体类生成除了 static 修饰的字段之外带有所有参数的构造方法
- `@RequiredArgsConstructor` 与 `@NonNull` 注解配合使用，自定义字段参数构造方法
	- `@NonNull` 将某个属性规定为必须传入

```java
// id属性没有加@NonNull注解，所以构造方法里不会有id属性
@RequiredArgsConstructor  
public class User implements Serializable {  
    private Integer id;  
  
    @NonNull  
    private String name;  
  
    @NonNull  
    private String password;  
  
    @NonNull  
    private Integer authority;  
}
```

## 💛 建造者
- `@Builder` 可以自动生成一个建造者模式相关的代码【~~不需要手动 setter 构建对象，而是链式调用来构建对象~~】，使得对象的构建更加简洁

```java
// Person类
@Builder
public class Person {
    private String name;
    private int age;
    private String address;
}

// 构建对象
Person person = Person.builder()
                      .name("张三")
                      .age(25)
                      .address("北京")
                      .build();
```











