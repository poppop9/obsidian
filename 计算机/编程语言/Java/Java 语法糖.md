
# Java 语法糖
## 断言
1. 调试和测试：断言可用于验证程序的某些假设或条件是否成立。它们可以帮助开发人员在开发和测试过程中捕获错误和异常情况，提供更好的调试支持。
2. 文档和规范：断言可以用于在代码中明确地指定预期的条件，从而提供文档和规范的作用。这有助于其他开发人员理解代码的预期行为，并且可以用来检查代码是否符合规范。
    
3. 安全性和错误检测：断言可以用于检测潜在的错误或不变条件的违反。它们允许在代码中定义和验证某些前提条件，以确保程序以正确的方式执行。
    

然而，需要注意以下几点：

1. 断言应该仅用于调试和测试目的，不应该用于处理预期的错误情况或异常处理。它们不应该用于替代正常的错误处理机制，如异常处理。
    
2. 断言在默认情况下是被禁用的。在生产环境中，断言语句将被忽略。因此，不应该将断言用于控制程序的正常流程或业务逻辑。
    
3. 断言的使用应该谨慎，并且应该根据具体情况进行评估。过多或不必要的断言可能会导致代码变得冗长和复杂，降低程序的性能。
    

总而言之，断言是一种有用的工具，可以在开发和测试过程中帮助捕获错误和异常情况。但是，它们应该被正确地用于适当的场景，并且不应该被滥用或替代正常的错误处理机制。

```java
public static void main(String[] args) {
	int a = 1;
	int b = 1;
	assert a == b;
	System.out.println("Hello World");
}
```

当 a不等于b 时，会抛出断言的异常，相等才会输出 HelloWorld，反编译后相当于一个 if else。

#### 数值字面量

在 java 7 中，数值字面量，不管是整数还是浮点数，都允许在数字之间插入任意多个下划线。

    publicclassTest{
    publicstaticvoidmain(String...args){
    inti=10_000;
    System.out.println(i);
    }
    }

反编译后会自动把下划线去掉，就是为了方便阅读。

#### For-Each

For-Each 是程序员都会经常用到的，底层也是普遍都讲过是利用 for 循环和迭代器，因此使用要注意 fail-fast 机制，建议了解 Stream 流的知识。

举个例子

    publicstaticvoidmain(String...args){
    String[]strs={"Hello"};
    for(Strings:strs){
    System.out.println(s);
    }
    List<String>strList=ImmutableList.of("Hello");
    for(Strings:strList){
    System.out.println(s);
    }
    }

    publicstatictransientvoidmain(Stringargs[])
    {
    Stringstrs[]={
    "Hello"
    };
    Stringargs1[]=strs;
    inti=args1.length;
    for(intj=0;j<i;j++)
    {
    Strings=args1[j];
    System.out.println(s);
    }

    ListstrList=ImmutableList.of("Hello");
    Strings;
    for(Iteratoriterator=strList.iterator();iterator.hasNext();System.out.println(s))
    s=(String)iterator.next();
    }

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