
>[!quote] Optional\<T> 类
>Optional 类是一个<u>可以为 null 的容器对象</u>，使我们不用显式进行判空，很好的解决了空指针异常

- 静态方法
	- `of(T t)` 传递泛型 T 返回一个指定的 Optional，**如果泛型 T 为 null 会报错**
	- `ofNullable(T t)` 与 `of()` 不同的是，这个泛型 T 可以为 null，那将返回一个空 Optional
	- `empty()` 返回空的 Optional 对象
- 非静态方法
	- **判断**
		- `Boolean isPresent()` 判断 Optional 中是否有值
	- **返回结果**
		- `get()` 返回 Optional 中的对象，如果为 null ，则抛出异常
		- `orElse(T t)` 如果 Optional 中有值，则返回此值；反之，返回泛型 T
	- **处理**
		- `map(处理方法)` 将 Optional 里的对象，转为另一个类型，**不会在 Optional 为空时抛出异常**，当 Optional 未空时，将不会执行处理方法
		- `ifPresent(处理方法 A)` 如果该 Optional 对象的值存在，则将这个值传递给方法 A
		- `ifPresentOrElse(处理方法A, 处理方法B)` 如果该 Optional 对象的值存在，则将这个值传递给方法 A，否则用方法 B 处理
		- `or(处理方法A)` 当 Optional 有值时，保持原值，反之，使用 A 方法的返回值来替代

---

```java
Optional<AwardBO> optionalAwardBO = rList.stream()
		.filter(AwardBO -> Objects.equals(AwardBO.getAwardId(), awardId))
		.findFirst();
optionalAwardBO.ifPresent(rList::remove);
```

```java
optional.ifPresentOrElse(
		System.out::println,
		() -> System.out.println("没有值")
);
```


---



```java
psvm {
  Java8Tester java8Tester = new Java8Tester();
  Integer value1 = null;
  Integer value2 = new Integer(10);
	
  // Optional.ofNullable - 允许传递为 null 参数
  Optional<Integer> a = Optional.ofNullable(value1);
	
  // Optional.of - 如果传递的参数是 null，抛出异常 NullPointerException
  Optional<Integer> b = Optional.of(value2);
  System.out.println(java8Tester.sum(a,b));
}

public Integer sum(Optional<Integer> a, Optional<Integer> b){
  System.out.println("第一个参数值存在: " + a.isPresent());
  System.out.println("第二个参数值存在: " + b.isPresent());
	
  // Optional.orElse - 如果值存在，返回它，否则返回默认值
  Integer value1 = a.orElse(new Integer(0));
	
  //Optional.get - 获取值，值需要存在
  Integer value2 = b.get();
  return value1 + value2;
}
```