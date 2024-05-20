
# Java 语法糖
## For-Each

For-Each 是程序员都会经常用到的，底层也是普遍都讲过是利用 for 循环和迭代器，因此使用要注意 fail-fast 机制，建议了解 Stream 流的知识。

```java
import com.google.common.collect.ImmutableList;
import java.util.List;
import java.util.Iterator;

public class Main {

    public static void main(String... args) {
        String[] strs = {"Hello"};
        for (String s : strs) {
            System.out.println(s);
        }

        List<String> strList = ImmutableList.of("Hello");
        for (String s : strList) {
            System.out.println(s);
        }
    }

    public static transient void main(String args[]) {
        String[] strs = {"Hello"};
        String[] args1 = strs;
        int i = args1.length;
        for (int j = 0; j < i; j++) {
            String s = args1[j];
            System.out.println(s);
        }

        List<String> strList = ImmutableList.of("Hello");
        String s;
        for (Iterator<String> iterator = strList.iterator(); iterator.hasNext(); ) {
            s = iterator.next();
            System.out.println(s);
        }
    }
}
```

#### 注意事项

2）try catch 中的异常不能再去区别异常的泛型类型，同样是泛型擦除机制。

3）自动拆箱和装箱，但是整数值有缓存机制。

    publicstaticvoidmain(String[]args){
    Integera=129;
    Integerb=129;
    Integerc=100;
    Integerd=100;
    System.out.println(a==b);
    System.out.println(c==d);
    }

输出结果

    false
    true

-128 到 127 和缓存机制可以实现重用，也就是说使用的是相同的对象引用，这个也比较经典。

4）增强 for 循环，上文有提到过，增强 for 底层有用到迭代器，迭代器在遍历的时候对象不允许修改或者删除。因此 CMS 异常也就是 fail-fast 多线程修改，解决方法可以直接用迭代器或者 Stream 流的方法，推荐 Stream 流掌握。

#### 总结
2.
   **自动装箱和拆箱：** 基本数据类型和对应的包装类型之间可以自动进行转换，这使得代码更易读。例如，`int` 到 `Integer` 的转换。
4.
   **枚举类型：** 提供了更简洁、类型安全的枚举定义方式，避免了使用常量的硬编码
7.
   **Diamond 语法（菱形语法）：** 在创建泛型实例时，允许省略类型参数的重复声明。
2.
   **自动装箱拆箱带来的性能开销：** 自动装箱和拆箱可能导致额外的性能开销，特别是在大量数据操作时。
3.
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