
>[!quote] Stream 流
>Stream 允许你对集合进行链式调用，进行各种操作【~~过滤、映射、聚合 ……~~】
>
> ```java
> public interface Stream\<T> extends BaseStream<T,Stream\<T>>
> ```
> 
> - Stream 流的操作不会影响原集合

# ❤ 生成流
通过数据源【~~数组、集合、IO 通道、生成器……~~】生成流

## 单列集合 Collection 生成流
- 直接用集合调用 `stream()` 方法

```java
List<String> list = new ArrayList<String>();  
Stream<String> stringStream = list.stream();  
```

## 双列集合 Map 生成流
无法直接生成流，如果想要处理<u>可以分开获取 key 流，和 value 流</u>；<u>也可以通过 entrySet 获取</u>

## 数组生成流
调用 `stream()` 方法

```java
int[] numbers = {1, 2, 3, 4, 5};
IntStream stream = Arrays.stream(numbers);
```

## 零散数据生成流
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

# ❤ 中间操作
打开流，做出数据过滤/映射，然后返回一个新的流

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

## filter
filter 里传入一个 Predicate 接口，用于判断流中的元素是否符合条件，如果返回 True 则留下，如果是 False 则过滤掉

```java
public static void main(String[] args) {  
    List<String> list = new ArrayList<>();  
    list.add("吴彦祖");  
    list.add("陈冠希");  
    list.add("黎明");  
    list.add("吴京");  

	// 生成 Stream 流
	list.stream()
		// 调用filter接口
	    .filter(new Predicate<String>() {
	        @Override
	        public boolean test(String s) {
	            return s.startsWith("吴");  // 只有姓吴的可以留下
	        }
	    })
	    .filter(new Predicate<String>() {
	        @Override
	        public boolean test(String s) {
	            return s.length() == 3;  // 只有长度大于3可以留下
	        }
	    })
	    .forEach(new Consumer<String>() {
	        @Override
	        public void accept(String s) {
	            System.out.println(s);
	        }
	    });
}


吴彦祖
```

## limit，skip
- `limit(个数)` 获取流前面的 n 个元素
- `skip(个数)` 跳过流前面的 n 个元素

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
- `concat()` 合并流
- `distinct()` 去重

```java
public static void main(String[] args) {  
    List<String> list = new ArrayList<>();  
    list.add("吴彦祖");  
    list.add("陈冠希");  
    list.add("黎明");  
    list.add("吴京");  
  
    Stream<String> s1 = list.stream().limit(2);  
    Stream<String> s2 = list.stream().skip(1);  
	Stream.concat(s1, s2)
		.forEach(System.out::println);  //合并a，b。然后输出
  
    System.out.println("----------");  
  
    Stream<String> s3 = list.stream().limit(2);  
    Stream<String> s4 = list.stream().skip(1);  
    Stream.concat(s3, s4)
	    .distinct().forEach(System.out::println);  //去除重复
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
- 返回值为 0 ，排序位置保持不变
- 返回值 > 0，排序位置 o1 在后面
- 返回值 < 0，排序位置 o1 在前面

```java
public static void main(String[] args) {  
    List<Integer> list = new ArrayList<>();  
    list.add(32);  
    list.add(1);  
    list.add(992);  
    list.add(33);  
  
    list.stream()
	    .sorted()
	    .forEach(System.out::println);  
  
    list.stream()
	    .sorted(new Comparator<Integer>() {  
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
- `map` 对 Stream 中的每个元素应用一个函数，用这个函数的返回值替代原始元素，从而生成一个新的 Stream

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
>[!quote] `flatMap()` 
>`flatMap` 将流中的每个元素，转换成另一个流，然后将这些流连接起来形成一个单一的流


稍微觉得 flatMap 有用的场景：
```java
// 使用 map，你要手动过滤空值
List<String> filteredList = list.stream()
    .map(o -> o.isPresent() ? o.get() : null)
    .filter(Objects::nonNull)
    .collect(Collectors.toList());

// 使用 flatMap，在将元素转换成流时，空值会被转为空流，空流在合并时会自动消失
List<String> filteredListJava9 = list.stream()
    .flatMap(Optional::stream)
    .collect(Collectors.toList());
```

## peek
peek 只对流进行操作，不会改变流的元素，<u>相当于没有返回值的 map 操作</u>

# ❤ 终结操作
>[!warning] 如果一个流不进行终结操作，则这个流在执行时，不会执行中间操作，相当于这个流从来没有执行过 ：
> ```java
> // 这个程序看似会将数据add进list中，但是由于这个流操作没有终结操作，peek操作压根不会执行
> List\<JSONObject> list = new ArrayList<>();
> sbdqas.queryAll(qs).stream()
>         .peek(a -> {
>             Map<String, String> contentMap = a.toContentMap();
>             contentMap.put("t", AmountUtil.c(contentMap.get("t")));
>             list.add(new JSONObject(contentMap));
>         });
> ```

一个流使用终结操作后，就无法再进行操作了，**这是流的最后一个操作**

- `void forEach(Consumer action)` 对该流的每个元素执行操作
- `long count()` 返回该流中的元素个数
- `R collect(Collector collector)` 按照 collector 的要求，把元素收集到集合中

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

```java
// 简化版
list.stream().forEach(s -> {
	StringBuilder sb = new StringBuilder(s);
	sb.append(1);
	System.out.println(sb.toString());
});
```

## min，max
- `min(比较器)` 是返回一个比较器中最左边的元素，因为比较器默认左小右大
- `max(比较器)` 是返回一个比较器中最右边的元素，因为比较器默认左小右大

```java

Optional<JSONObject> first = referenceRateData.stream()
        .map(AbstractStandingBookData::getContent)
        .max((o1, o2) -> {
            LocalDateTime timeOne = LocalDateTimeUtil.parse(o1.getString("lastModDateTime"), DatePattern.NORM_DATETIME_PATTERN);
            LocalDateTime timeTwo = LocalDateTimeUtil.parse(o2.getString("lastModDateTime"), DatePattern.NORM_DATETIME_PATTERN);
            if (timeOne.isEqual(timeTwo)) {
                return 0;
            } else if (timeOne.isBefore(timeTwo)) {
                return -1;
            } else {
                return 1;
            }
        });
```

## findFirst
- `Optional findFirst` 获取流中的第一个元素，并返回 Optional 对象
	- `get()` 获取到 Optional 对象的值，也就是 Stream 流中的元素

>[!hint] 获得 Stream 流中的最后一个元素：
>- 先 skip （长度 - 1） 个元素
>- 再 findFirst

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

## reduce
- `reduce(初始值，累加器)` 必须保证初始值，和累加器的数据类型一致

```java
List<String> props = List.of("profile=native", "debug=true", "logging=warn", "interval=500");
Map<String, String> map = props.stream()
		// 把k=v转换为Map[k]=v:
		.map(kv -> {
			String[] ss = kv.split("\\=", 2);
			return Map.of(ss[0], ss[1]);
		})
		// 把所有Map聚合到一个Map:
		.reduce(new HashMap<String, String>(), (m, kv) -> {
			m.putAll(kv);
			return m;
		});
```

## anyMatch，allMatch，noneMatch
- `anyMatch` 判断的条件里，任意一个元素 true，返回 true
- `allMatch` 判断条件里的元素，所有的元素都 true，返回 true
- `noneMatch` 判断条件里的元素，所有的都 false，返回 true

```java
List<String> words = List.of("apple", "banana", "cherry");
boolean anyMatch = words.stream()
		.anyMatch(word -> word.equals("apple"));
boolean allMatch = words.stream()
		.allMatch(word -> word.equals("apple"));
boolean noneMatch = words.stream()
		.noneMatch(word -> word.equals("pear"));

System.out.println(anyMatch);
System.out.println(allMatch);
System.out.println(noneMatch);

---
true
false
true
```

## collect
### toList
- `collect(……)` 
	- `Collectors.toList()` 将 Stream 流收集成 List 集合
- `toList()` 将 Stream 流收集成<u>不可变的</u> List 集合

```java
public static void main(String[] args) {  
    List<Integer> list = List.of(32, 1, 992, 33);
  
    List<Integer> collect = list.stream().filter((Integer i) -> {  
        return i > 1;  
    }).collect(Collectors.toList());
  
    System.out.println(collect);  
}

[32, 992, 33]
```

### toMap
- `Collectors.toMap(new Function<>(){} ,new Function<>(){})` 将 Stream 流收集成 Map 集合
```java
String arr[] = {"陈冠希,14", "吴彦祖,66", "刘德华,2"};  
Map<String, Integer> collect = Stream.of(arr)
    .filter(s -> {
        // 过滤掉年龄大于2的，并生成流
        return Integer.parseInt(s.split(",")[1]) > 2;
    })
    .collect(Collectors.toMap(
        s -> s.split(",")[0],  // keyMapper: 分割字符串并取第一部分作为键
        s -> Integer.parseInt(s.split(",")[1])  // valueMapper: 分割字符串并解析第二部分为整数作为值
    ));

System.out.println(collect);  


{陈冠希=14, 吴彦祖=66}
```

- `Collectors.toMap(lambda ,lambda, 保留哪个)` 将 Stream 流收集成 Map 集合，如果出现重复键，保留哪个
```java
// 这里是为了去除重复
maps.stream()
    .peek(item -> { …… })
    .collect(Collectors.toMap(
            item -> item.get("department_name"),
            item -> item,
            (existing, replace) -> existing
    ))
    .values()
    .stream()
    .toList();
```


### joining
- `Collectors.joining(间隔字符，开始字符，结束字符)` 将字符串类型的 Stream 收集成一个 String

```java
List<String> words = List.of("apple", "banana", "cherry", "date");
String result = words.stream()
		.collect(Collectors.joining(", ", "[", "]"));

System.out.println(result);

---
[apple, banana, cherry, date]
```

### groupingBy
- `groupingBy(分组条件)` 根据某个属性，对流中的元素进行分组，生成一个 Map

```java
List<Person> people = Arrays.asList(
	new Person("Alice", 30),
	new Person("Bob", 20),
	new Person("Charlie", 30),
	new Person("David", 20)
);

// 将根据年龄进行分组
Map<Integer, List<Person>> peopleByAge = people.stream()
	.collect(Collectors.groupingBy(Person::getAge));
```

- `groupingBy(分组条件，对分组后的元素处理的操作)` 根据某个属性，对流中的元素进行分组，再对分组后的元素进行操作，生成一个 Map
```java
// 根据年龄进行分组，对分组后的元素进行计数
Map<Integer, Long> countByAge = people.stream()  
        .collect(Collectors.groupingBy(Person::getAge, Collectors.counting()));  
countByAge.forEach((age, count) -> {  
    System.out.println("Age: " + age);  
    System.out.println("Count: " + count);  
    System.out.println();  
});

---
Age: 20
Count: 2

Age: 30
Count: 2
```

```java
// 根据年龄进行分组，对分组后的元素进行拿取属性，再组成集合
Map<Integer, List<String>> collect3 = people.stream()  
        .collect(Collectors.groupingBy(Person::getAge, Collectors.mapping(Person::getName, Collectors.toList())));  
collect3.forEach((age, names) -> {  
    System.out.println("Age: " + age);  
    System.out.println("Name: " + names);  
    System.out.println();  
});

---
Age: 20
Name: [Bob, David]

Age: 30
Name: [Alice, Charlie]
```


# ❤ 流的静态方法
- `iterate(流的初始值，针对于初始值的操作)` 

```java
// 针对一个LocalDate，每次迭代都plusDays，然后最终限制7个元素
List<LocalDate> nowDateList = Stream.iterate(  
        LocalDate.now(),  
        date -> date.plusDays(1)  
).limit(7).toList();
```

# ❤ 并行流
>[!quote] 并行流
>并行流 是指将数据分成多个部分，然后并行处理流中的每个元素
>
>- **优点**
>	- 利用了多核处理器的优势
>	- 对海量数据的处理效率更高
>- **缺点**
>	- 但是由于是多线程的，要考虑并发问题
>	- 如果是少量数据，使用并行流反而没优势，因为并行流要创建线程，销毁线程，这些都要时间
>	- 并行流处理流元素是无序的

---

- `parallelStream()` 将集合转为并行流
- `parallel()` 将顺序流转为并行流

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

// 创建并行流
Stream<Integer> parallelStream = numbers.parallelStream();
```

# ❤ 循环处理技术对比
- **数据 < 1 万** ，for 循环 > foreach / 增强 for / 迭代器 > Stream
- **1 万 < 数据量 < 100 万** ，Stream > foreach / 增强 for / 迭代器 > for
- **数据 > 100 万** ，parallelStream 最高















