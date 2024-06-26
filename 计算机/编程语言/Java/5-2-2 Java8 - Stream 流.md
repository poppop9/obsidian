
>[!quote] Stream 流
>Stream 允许你对集合进行链式调用，进行各种操作【~~过滤、映射、聚合 ……~~】
>
> ```java
> public interface Stream\<T> extends BaseStream<T,Stream\<T>>
> ```

# 生成流
通过数据源【~~数组、集合、IO 通道、生成器……~~】生成流

## Collection，Map 生成流
- 直接用集合调用 `stream()` 方法

```java
List<String> list = new ArrayList<String>();  
Stream<String> stringStream = list.stream();  
```

- `Stream.of()` 

## 数组，直接生成流
- `Stream.of()` 

```java
public static void main(String[] args) {  
    String arr[] = {"greenteck", "wiggles", "hoan"};  
    Stream<String> ArrStream = Stream.of(arr);  
}
```

```java
public static void main(String[] args) {  
    Stream<String> Stream = Stream.of("greenteck", "wiggles", "hoan"); 
}
```

# 中间操作
>打开流，做出数据过滤/映射，然后返回一个新的流

>[!summary] Method Summary
>Stream\<T> filter(Predicate\<T> pre)  ------ 以 Predicate 接口为条件，对流进行过滤
>
>Stream\<T> limit(long maxSize)  ------返回一个截取了前 maxSize 个元素的流
>Stream\<T> skip(long n)  ------跳过 n 个元素，返回剩下元素的流
>
>static \<T> Stream\<T> concat(Stream a, Stream b) -----合并 a 和 b 两个流
>Stream\<T> distinct()  ------去除流中的重复元素，再返回这个流
>
>Stream\<T> sorted()  ------返回一个按自然顺序排序后的流
>Stream\<T> sorted(Comparator c)  ------返回一个根据比较器 c 排序后的流
>
>Stream\<R> map(Function mapper)  ------返回一个由 Function 接口处理过的流
>IntStream mapToInt(ToIntFunction mapper)----返回一个由 mapper 处理过的 IntStream

## filter 过滤器
```java
public static void main(String[] args) {  
    List<String> list = new ArrayList<>();  
    list.add("吴彦祖");  
    list.add("陈冠希");  
    list.add("黎明");  
    list.add("吴京");  

    //生成stream流     
    list.stream()
    .filter(new Predicate<String>() {    //调用filter过滤器
        @Override                                   
        public boolean test(String s) {      //重写Predicate接口的test()方法
            return s.startsWith("吴");  
        }  
    }).filter(new Predicate<String>() {  
        @Override  
        public boolean test(String s) {  
            return s.length() == 3;  
        }  
    }).forEach(new Consumer<String>() {        //调用forEach迭代器
        @Override  
        public void accept(String s) {          //重写Consumer接口的accept()方法
            System.out.println(s);  
        }  
    });  
}


吴彦祖
```

## limit，skip
```java
public static void main(String[] args) {  
    List<String> list = new ArrayList<>();  
    list.add("吴彦祖");  
    list.add("陈冠希");  
    list.add("黎明");  
    list.add("吴京");  
  
    list.stream().limit(2).forEach(System.out::println);  
    System.out.println("----------");  
    list.stream().skip(1).forEach(System.out::println);  
}


吴彦祖
陈冠希
----------
陈冠希
黎明
吴京
```

## concat，distinct
```java
public static void main(String[] args) {  
    List<String> list = new ArrayList<>();  
    list.add("吴彦祖");  
    list.add("陈冠希");  
    list.add("黎明");  
    list.add("吴京");  
  
    Stream<String> s1 = list.stream().limit(2);  
    Stream<String> s2 = list.stream().skip(1);  
	    Stream.concat(s1, s2).forEach(System.out::println);  //合并a，b。然后输出
  
    System.out.println("----------");  
  
    Stream<String> s3 = list.stream().limit(2);  
    Stream<String> s4 = list.stream().skip(1);  
    Stream.concat(s3, s4).distinct().forEach(System.out::println);  //去除重复
}


吴彦祖
陈冠希
陈冠希
黎明
吴京
----------
吴彦祖
陈冠希
黎明
吴京
```

## sorted
```java
public static void main(String[] args) {  
    List<Integer> list = new ArrayList<>();  
    list.add(32);  
    list.add(1);  
    list.add(992);  
    list.add(33);  
  
    list.stream().sorted().forEach(System.out::println);  
  
    list.stream().sorted(new Comparator<Integer>() {  
        @Override  
        public int compare(Integer o1, Integer o2) {  
            return 0;  
        }  
    }).forEach(System.out::println);  
}


1
32
33
992
----------
32
1
992
33
```

## map，mapToInt
这里的 map 不是 map 集合，而是“映射”的意思

---

- `对象::属性名` 把对象集合 -> 对象中的某个属性集合
```java
// 将awardBO集合，转为awardBO的属性awardId的集合
List<Integer> awardIds = awardBOs.stream()
		.map(AwardBO::getAwardId)
		.toList();
```

---

```java
public static void main(String[] args) {  
    List<String> list = new ArrayList<>();  
    list.add("32");  
    list.add("1");  
    list.add("992");  
    list.add("33");  
  
    list.stream().map(new Function<String, Integer>() {  
        @Override  
        public Integer apply(String s) {  
            return Integer.parseInt(s) + 1;  
        }  
    }).forEach(System.out::println);  
  
    System.out.println("-----------------");  
  
    list.stream().mapToInt(new ToIntFunction<String>() {  
        @Override  
        public int applyAsInt(String value) {  
            return Integer.parseInt(value) + 2;  
        }                             //通过mapToInt可以将Stream转换为IntStream
    }).forEach(System.out::println);            //在IntStream里有一些对int的特有操作
}


33
2
993
34
-----------------
34
3
994
35
```

## flatMap

`flatMap`通常用于将一个流中的每个元素转换成另一个流，然后将这些流连接起来形成一个单一的流。而`.map`通常用于将流中的每个元素应用一个函数，转换成另一种形式的元素


`.flatMap(map -> map.entrySet().stream())`

这里，`flatMap`正在被用来处理一个由`Map`对象组成的流。每个`Map`对象都包含键值对（entry），而`map.entrySet().stream()`将每个`Map`的键值对转换成一个流。这个流包含`Map.Entry`对象，每个对象都是一个键值对。

这步操作的用途可能包括：

1. **转换流**：将一个由`Map`组成的流转换成一个由`Map.Entry`组成的流。
2. **处理键值对**：在后续的操作中，可以对这些键值对进行进一步的处理，例如过滤、映射或收集。
3. **简化代码**：在流操作中，使用`flatMap`可以简化代码，避免使用循环或中间变量。

例如，如果你有一个包含多个`Map`的列表，并且你想要对所有`Map`中的所有键值对执行操作，你可以首先将这个列表转换成流，然后使用`flatMap`将每个`Map`转换成一个流，最后对这个结果流进行操作。这样，你可以在流操作中直接处理所有的键值对，而不需要显式地遍历每个`Map`。

# 终结操作
一个流使用终结操作后，就无法再进行操作了，**这是流的最后一个操作**

>[!summary] Method Summary
>void forEach(Consumer action)  ------对该流的每个元素执行操作
>long count()  ------返回该流中的元素个数
>R collect(Collector collector)  ------按照 collector 的要求，把元素收集到集合中

## forEach
```java
public static void main(String[] args) {  
    List<String> list = new ArrayList<>();  
    list.add("32");  
    list.add("1");  
    list.add("992");  
    list.add("33");  
  
    list.stream().forEach(new Consumer<String>() {  
        @Override  
        public void accept(String s) {  
            StringBuilder sb = new StringBuilder(s);  
            sb.append(1);  
            System.out.println(sb.toString());  
        }  
    });  
}


321
11
9921
331
```

## count
```java
public static void main(String[] args) {  
    List<String> list = new ArrayList<>();  
    list.add("32");  
    list.add("1");  
    list.add("992");  
    list.add("33");  
  
    System.out.println(list.stream().count());  
}


4
```

## collect
- `Collectors.toList()` 收集到其他集合

```java
public static void main(String[] args) {  
    List<Integer> list = new ArrayList<>();  
    list.add(32);  
    list.add(1);  
    list.add(992);  
    list.add(33);  
  
    List<Integer> collect = list.stream().filter((Integer i) -> {  
        return i > 1;  
    }).collect(Collectors.toList());   //接口中传入的是Collectors实现类的toList()方法
  
    System.out.println(collect);  
}


[32, 992, 33]
```

- `Collectors.toMap(new Function<>(){} ,new Function<>(){})` 收集到 Map 集合

```java
String arr[] = {"陈冠希,14", "吴彦祖,66", "刘德华,2"};  
  
Stream<String> stream = Stream.of(arr).filter((String s) -> {  
	return Integer.parseInt(s.split(",")[1]) > 2;//过滤掉年龄大于2的，并生成流  
});  
  
Map<String, Integer> collect = stream.collect(Collectors.toMap(new Function<String, String>() {  
	@Override  
	public String apply(String s) {  
		return s.split(",")[0];  
	}                              //第一个Function是map的键，由,前面的元素构成  
}, new Function<String, Integer>() {  
	@Override  
	public Integer apply(String s) {  
		return Integer.parseInt(s.split(",")[1]);  
	}                             //第二个Function是map的值，由,后面的元素构成  
}));  

System.out.println(collect);  


{陈冠希=14, 吴彦祖=66}
```























