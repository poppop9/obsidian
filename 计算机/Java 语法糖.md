
### Java 语法糖
#### 自动装箱和拆箱

这个语法糖应该是较为熟知的，自动装箱就是 Java 自动将原始类型值转换成对应的对象，比如将 int 的变量转换成 Integer 对象，这个过程叫做装箱，反之将 Integer 对象转换成 int 类型值，这个过程叫做拆箱。因为不用人工去转化，因此是自动装箱和拆箱。

举个例子（自动装箱）

    publicstaticvoidmain(String[]args){
    intnum=1;
    Integern=num;
    }

反编译

    publicstaticvoidmain(Stringargs[])
    {
    intnum=1;
    Integern=Integer.valueOf(num);
    }

自动拆箱

    publicstaticvoidmain(String[]args){

    Integernum=10;
    intn=num;
    }

反编译

    publicstaticvoidmain(Stringargs[])
    {
    Integernum=Integer.valueOf(10);
    intn=num.intValue();
    }

总结：装箱用 valueOf() 方法，拆箱用 xxxValue 方法，比如 intValue。

#### 断言

在 Java 中，`assert`关键字是从 JAVA SE 1.4 引入的，为了避免和老版本的 Java 代码中使用了`assert`关键字导致错误，Java 在执行的时候默认是不启动断言检查的。

举个例子

    publicclassTest{
    publicstaticvoidmain(Stringargs[]){
    inta=1;
    intb=1;
    asserta==b;
    System.out.println("HelloWord");
    }
    }

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

### 注意事项

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

### 总结
语法糖在大多数情况下被我们所使用，能够较大地提升开发效率，但是在开发效率提升的同时，我们要明白语法糖的底层原理，也就是反编译后的代码，JVM 虚拟机是怎么优化的，有哪些优化机制，可能会发生什么问题，这是我们需要注意的点，避免踩坑。

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

