
# Java 语法糖
   **Lambda 表达式的闭包问题：** 在使用 Lambda 表达式时，需要注意对外部变量的访问，因为 Lambda 表达式默认是对外部变量的"读取"操作，对于局部变量需要是最终的（effectively final）。


1）如何在运行时获取泛型类的信息进行处理？

2）如何有效避免或降低自动装箱和拆箱带来的性能问题？

3）如何避免或解决 Lambda 表达式的闭包问题？

# 有趣的判断
```java
Class cache = Integer.class.getDeclaredClasses()[0];
Field c = cache.getDeclaredField("cache");
c.setAccessible(true);
Integer[] array = (Integer[]) c.get(cache);
// array[129] is 1
array[130] = array[129]; // Set 2 to be 1
array[131] = array[129]; // Set 3 to be 1
Integer a = 1;
if (a == (Integer) 1 && a == (Integer) 2 && a == (Integer) 3) {
    System.out.println("Success");
}
```

```java
@PrepareForTest(Integer.class)
@RunWith(PowerMockRunner.class)
public class Ais123 {

    @Before
    public void before() {
        //"value" is just a place to store an incrementing integer
        AtomicInteger value = new AtomicInteger(1);
        replace(method(Integer.class, "intValue"))
                .with((proxy, method, args) -> value.getAndIncrement());
    }

    @Test
    public void test() {
        Integer a = 1;
        if (a == 1 && a == 2 && a == 3) {
            System.out.println("Success");
        } else {
            Assert.fail("(a == 1 && a == 2 && a == 3) != true, a = " + a.intValue());
        }
    }
}
```