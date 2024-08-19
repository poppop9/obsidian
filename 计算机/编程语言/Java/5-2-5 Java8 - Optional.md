
>[!quote] Optional 类
>Optional 类是一个<u>可以为 null 的容器对象</u>，使我们不用显式进行判空，很好的解决了空指针异常

- 静态方法
- 非静态方法
	- `ifPresent(处理方法 A)` 如果该 Optional 对象的值存在，则将这个值传递给方法 A
	- `get()` 返回 Optional 中的对象，可能为 null

---

```java
Optional<AwardBO> optionalAwardBO = rList.stream()
		.filter(AwardBO -> Objects.equals(AwardBO.getAwardId(), awardId))
		.findFirst();
optionalAwardBO.ifPresent(rList::remove);
```



---

https://www.runoob.com/java/java8-optional-class.html

https://www.runoob.com/java/java9-optional-class-improvements.html

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