#计算机/编程语言/Java 
# 🌕Lambda表达式
## 🌗标准格式
>() -> {……}
```
()：小括号里面没有内容，表示该方法没有参数。如果有多个参数，用逗号隔开
->：表示指向要做的事情
{}：大括号里的内容表示需要做的事情（方法体内容）
```
## 🌗有什么用？
#####🌑简化代码
- 使用匿名内部类实现多线程时
	```java
	public static void main(String[] args) {
		new Thread(new Runnable() {
			@Override
			public void run() {
				System.out.println("多线程启动了");
			}
		}).start();
	}
	```
- 使用Lambda表达式实现多线程时
	```java
	public static void main(String[] args) {
	  new Thread(() -> {
		  System.out.println("多线程启动了");
	  }).start();
	}
	```
#####🌑简化字节码文件
- 使用匿名内部类时，会在编译之后，单独产生一个字节码文件[^1]
- 使用Lambda表达式时，编译之后不会单独产生一个字节码文件，而是在运行时动态生成

[^1]:当然在注释相应的匿名内部类代码之后，该字节码文件会消失
## 🌗使用前提
#####🌑这个类要有一个接口
>比如需要的MyRunnable这个类有一个接口Runnable
#####🌑这个接口中有且仅有一个抽象方法
>比如Runnable接口里只有一个抽象方法run方法
## 🌗实现有参数和返回值的抽象方法
```java
public interface Eatable {  
    int add(int a, int b);    //一个接口且有且仅有一个抽象方法
}
```
```java
public class EatableDemo {  
    public static void main(String[] args) {  
        useEatable((int a, int b) -> {  
            return a + b;                 //方法的具体实现
        });  
    }  
  
    public static void useEatable(Eatable e) {  //通过接口的实现类对象调用add方法  
        int sum = e.add(1, 2);  
        System.out.println(sum);  
    }  
	int a = 2;
}


3
```
## 🌗还能怎么省略
- 小括号里的参数类型可以省略
- 如果参数只有一个，那么小括号可以省略
- 如果大括号里的语句只有一条，那么可以省略大括号和分号和return
	```java
	useEatable((int a, int b) -> {      --------->
		return a + b;                   --------->   useEatable((a, b) -> a + b);
	});                                 --------->
	```
# 🌕方法引用
## 🌗概述
>方法引用符”::“
## 🌗引用类的静态方法
```java
public interface parseInt {  
    int convert(String s);  
}
```
```java
public class Demo {  
    public static void main(String[] args) {  
        useParseInt(Integer::parseInt);          //Integer这个接口里面有个静态的parseInt方法
    }  
  
    public static void useParseInt(parseInt p) {  
        System.out.println(p.convert("123"));  
    }  
}
```
## 🌗引用对象的实例方法
```java
public interface Printable {  
    void printString(String s);  
}
```
```java
public class Demo {  
    public static void main(String[] args) {  
        //usePrintable(s -> System.out.println(s));  
        usePrintable(System.out::println);        //自动把参数String s传递给println方法  
    }                                             //out是PrintStream的实例对象，里面有println方法
  
    public static void usePrintable(Printable p) {  
        p.printString("Hello Java");  
    }
}


Hello Java
```
## 🌗引用类的实例方法
```java
public interface SubString {  
    String sub(String s, int x, int y);  
}
```
```java
public class Demo {  
    public static void main(String[] args) {  
        useSubString(String::substring);  
    }  
  
    public static void useSubString(SubString p) {  
        System.out.println(p.sub("Hello Java", 2, 5));  
    }  
}
```
## 🌗引用构造方法
```java
public class student {  
    private int age;  
    private String name;  
  
    public student(int age, String name) {  
        this.age = age;  
        this.name = name;  
    }  
  
    public int getAge() {return age;}  
    public void setAge(int age) {this.age = age;}  
  
    public String getName() {return name;}  
    public void setName(String name) {this.name = name;}  
}
```
```java
public interface studentBuilder {  
    student build(int age, String name);  
}
```
```java
public class Demo3 {  
    public static void main(String[] args) {  
//        useStudentBuilder(new studentBuilder() {  
//            @Override  
//            public student build(int age, String name) {         //匿名内部类
//                return new student(age, name);  
//            }  
//        });  
  
//        useStudentBuilder((int age, String name) -> {           //Lambda表达式
//            return new student(age, name);  
//        });  
  
        useStudentBuilder(student::new);                    //new代表了构造方法
    }  
  
    public static void useStudentBuilder(studentBuilder sb) {  
        student s = sb.build(12, "吴彦祖");  
        System.out.println(s.getAge() + "," + s.getName());  
    }  
}
```
## 🌗作用
- 使得代码更加简洁
# 🌕函数式接口
>有且仅有一个抽象方法的接口[^2]

[^2]:函数式接口完全就是为了Lambda表达式而打造的，它的概念就是Lambda表达式的使用前提
## 🌗函数式接口用作局部变量
```java
@FunctionalInterface               //这是一个注解，告诉别人这是函数式接口。
public interface MyInterface {     //加上注解之后，再在该接口中添加方法会报错
    void show();  
}
```
```java
public class Demo {  
    public static void main(String[] args) {  
        MyInterface mif = () -> System.out.println("函数式接口");  
        mif.show();  
    }                     //其实Lambda表达式代表的还是MyInterface的一个实现类对象
}


函数式接口
```
## 🌗函数式接口作为方法参数
>上述已经写了很多了
## 🌗函数式接口作为方法的返回值
```java
public class ComparatorDemo {  
    public static void main(String[] args) {  
        TreeSet<String> ts = new TreeSet<String>(getComparator());    //传入这个比较器
  
        String s1 = "刘德华";  
        String s2 = "黎明";  
        String s3 = "欧阳娜娜";  
  
        ts.add(s1);  
        ts.add(s2);  
        ts.add(s3);  
  
        for (String s : ts) {  
            System.out.println(s);  
        }  
    }  
  
    public static Comparator<String> getComparator() {  
//        Comparator<String> cp = new Comparator<String>() {  
//            @Override  
//            public int compare(String s1, String s2) {             //匿名内部类
//                return s1.length() - s2.length();  
//            }  
//        };  
//        return cp;  
  
        Comparator<String> cp = (String s1, String s2) -> {  
            return s1.length() - s2.length();  
        };  
  
        return cp;  
    }  
}


黎明
刘德华
欧阳娜娜
```
## 🌗常用的函数式接口
#####🌑Supplier
```
@FunctionalInterface 
public interface Supplier<T>
```
***是一个生产型接口，get()方法不用参数，而且还返回（生产）一个泛型***
>[!summary]
>T get()  ------返回一个泛型T

```java
public class SupplierDemo {  
    public static void main(String[] args) {  
        int arr[] = {4, 2, 55, 33, 88};                  //定义数组
  
        int Max = getMax(new Supplier<Integer>() {       //接收最大值
            @Override  
            public Integer get() {                  //重写get()方法
                int max = arr[0];  
  
                for (int i = 1; i < arr.length; i++) {  
                    if (arr[i] > max) {  
                        max = arr[i];  
                    }  
                }  
                return max;  
            }  
        });  
        System.out.println(Max);                    //输出数组的最大值
    }  
  
    public static int getMax(Supplier<Integer> sup) {  
        return sup.get();  
    }  
}


88
```
#####🌑Consumer
```
@FunctionalInterface 
public interface Consumer<T>
```
***是一个消费型接口，接收一个参数，做一系列操作，无返回值***
>[!summary]
>void accept(T  t)  ------对给定的参数T进行操作

```java
public class ConsumerDemo {  
    public static void main(String[] args) {  
        OpString("吴彦祖", (String s) -> System.out.println(s.length()));  
    }  
  
    public static void OpString(String s, Consumer<String> con) {  
        con.accept(s);  
    }  
}


3
```
#####🌑Predicate
```
@FunctionalInterface 
public interface Predicate<T>
```
***是一个评估型接口，接收一个参数进行评估，返回一个boolean值***
>[!summary]
>boolean test(T t)  ------接收泛型，评估后，返回boolean值
>default Predicate<\T> negate()  ------返回一个逻辑的否定（逻辑非）
>default Predicate<\T> and(Predicate other)  ------返回一个组合判断（逻辑与）
>default Predicate<\T> or(Predicate other)  ------返回一个组合判断（逻辑或）
######🌙test()
```java
public static void main(String[] args) {  
	Boolean b = CheckString("吴彦祖", (String s) -> {  
		return s.equals("吴彦祖");  
	});  
  
	System.out.println(b);  
}  
  
public static boolean CheckString(String s, Predicate<String> pre) {  
	return pre.test(s);         
}


true
```
######🌙negate()
```java
public static void main(String[] args) {  
	Boolean b = CheckString("吴彦祖", (String s) -> {  
		return s.equals("吴彦祖");  
	});  
  
	System.out.println(b);  
}  
  
public static boolean CheckString(String s, Predicate<String> pre) {  
	return pre.negate().test(s);              //先对pre进行negate操作，然后调用test()
}


false
```
>[!faq] 为什么不直接return !pre.test(s)，而是return pre.negate().test(s)？
>结果虽然相同但是理念不同
>>前者表达的是，返回一个predicate对象调用test方法之后结果的非
>>后者表达的是，返回一个predicate对象的逻辑非后，再调用test方法的结果
######🌙and()，or()
```java
public static void main(String[] args) {  
	Boolean b = CheckString("吴彦祖", (String s) -> {  
		return s.equals("吴彦祖");  
	}, (String s) -> {  
		return s.equals("陈冠希");  
	});  

	System.out.println(b);  
}  

public static boolean CheckString(String s, Predicate<String> pre1, Predicate<String> pre2)     {  
	//boolean b1 = pre1.test(s);  
	//boolean b2 = pre2.test(s);              //可用这三条语句代替，但是表意不同
	//return b3 = b1 && b2;  
	return pre1.and(pre2).test(s);  
}


false
```
#####🌑Function
```
@FunctionalInterface
public interface Function<T,R>
```
***是一个转唤型接口，接收一个参数将其转换为另一个参数***
>[!summary]
>R apply(T t)  ------
>default<\V> Function<\T,\V> andThen(Function after)  ------

```java
public class FunctionDemo {  
    public static void main(String[] args) {  
        convert("100", (String s) -> {  
            return Integer.parseInt(s);  
        });  
    }  
  
    public static void convert(String s, Function<String, Integer> fun) {  
        int i = fun.apply(s);  
        System.out.println(i);  
    }  
}


100
```
# 🌕接口的组成更新
## 🌗概述
>***Java 8之前***，接口中只有<u>常量</u>和<u>抽象方法</u>
>***Java 8 之后***，接口中加入了<u>默认方法</u>和<u>静态方法</u>
>***Java 9之后***，接口中加入了<u>私有方法</u>
## 🌗接口中的默认方法
>public default ……
#####🌑注意事项
- ***默认方法中可以有方法体***
- ==接口中的默认方法不会让实现类去强制重写==
- ==而且就算实现类不重写，测试类也可以直接调用==
	```java
	public interface MyInterface {  
	    void show1();  
	  
	    public default void show3() {  
	        System.out.println("show3");  
	    }  
	}
	```
	```java
	public class mitfImp1 implements MyInterface{  
	    public void show1() {  
	        System.out.println("111show1");  
	    }  
	}
	```
	```java
	public class Demo {  
	    public static void main(String[] args) {  
	        MyInterface m1 = new mitfImp1();  
	        m1.show1();  
	        m1.show3();  
	    }  
	}
	
	
	111show1
	show3
	```
- ==不过需要注意：当一个实现类实现了多个接口且这多个接口中有同名的默认方法时，那么在实现类中也必须重写该默认方法==
	```java
	public interface MyInterface1 {  
	    void show1();  
	  
	    public default void show3() {  
	        System.out.println("我是1接口中的默认方法");  
	    }  
	}
	```
	```java
	public interface MyInterface2 {  
	    void show1();  
	  
	    public default void show3() {  
	        System.out.println("我是2接口中的默认方法");  
	    }  
	}
	```
	```java
	public class mitfImp1 implements MyInterface1,MyInterface2 {  
	    public void show1() {  
	        System.out.println("111show1");  
	    }  
	
	    public void show3() {  
	        MyInterface1.super.show3();   //MyInterface代表实现哪个接口的show3方法，super代表实现默认方法，show3代表对应方法
	    }  
	}
	```
	```java
	public class Demo {  
	    public static void main(String[] args) {  
	        MyInterface1 m1 = new mitfImp1();  
	        m1.show1();  
	        m1.show3();  
	    }  
	}
	
	
	111show1
	我是1接口中的默认方法
	```
#####🌑作用
>让你更加灵活地在接口中加入新的方法，而不破坏现有代码

>可以减少代码量（比如牛类，羊类，马类都实现了动物接口。但是它们的eat()方法都是吃草。那我没有使用默认方法时，我要在三个类里都实现eat()方法并且写上相同的内容；使用默认方法后，这三个类中就不需要重写eat()方法了）

***比如，现在要求要在mitfImp1中加入一个show3()方法，在mitfImp2中不加入***
- [x] 不使用默认方法时
	- 你需要新建一个MyInterfaceSon接口来继承MyInterface接口，然后创建show3()方法，再让mitfImp1类从MyInterface接口转到实现MyInterfaceSon接口
	  ```java
	  public interface MyInterface {  
	      void show1();  
	      void show2();
	  }
	  ```
	  ```java
	  public interface MyInterfaceSon extends MyInterface{
	  	void show3();
	  }
	  ```
	  ```java
	  public class mitfImp1 implements MyInterfaceSon{
	      public void show1() {
	          System.out.println("111show1");
	      }
	      public void show2() {
	          System.out.println("111show2");
	      }
	      public void show3() {
	  	    System.out.println("111show3");
	      }
	  }
	  ```
	  ```java
	  public class mitfImp2 implements MyInterface {  
	      public void show1() {  
	          System.out.println("222show1");  
	      } 
	      public void show2() {  
	          System.out.println("222show2");  
	      }  
	  }
	  ```
	  
	- 或者你在MyInterface接口中直接加入show3()方法，然后在***所有***实现过它的实现类里面重写（很麻烦很麻烦）
		```java
		public interface MyInterface {  
		    void show1();  
		    void show2();
		    void show3();
		}
		```
		```java
		public class mitfImp1 implements MyInterfaceSon{
		    public void show1() {
		        System.out.println("111show1");
		    }
		    public void show2() {
		        System.out.println("111show2");
		    }
		    public void show3() {
			    System.out.println("111show3");
		    }
		}
		```
		```java
		public class mitfImp2 implements MyInterface {  
		    public void show1() {  
		        System.out.println("222show1");  
		    } 
		    public void show2() {  
		        System.out.println("222show2");  
		    }
		    public void show3(){}
		}
		```

- [x] 使用默认方法
	- 你只需要在MyInterface里加入默认方法show3()，再在要实现show3()功能的实现类里重写即可，不需要show3()功能的类则不管
		```java
		public interface MyInterface {  
		    void show1();
		    void show2();
		  
		    public default void show3() {  
		        System.out.println("show3");  
		    }  
		}
		```
		```java
		public class mitfImp1 implements MyInterface{  
		    public void show1() {  
		        System.out.println("111show1");  
		    }  
		    public void show2() {  
		        System.out.println("111show2");  
		    }  
			public void show3() {
				System.out.println("111show3");
			}
		}
		```
		```java
		public class mitfImp2 implements MyInterface {  
		    public void show1() {  
		        System.out.println("222show1");  
		    }   
		    public void show2() {  
		        System.out.println("222show2");  
		    }  
		}
		```
## 🌗接口中的静态方法
>public static ……
#####🌑注意事项
- <mark style="background: #D2B3FFA6;">静态方法只能通过接口名调用，不能通过实现类名调用</mark>（***所以与默认方法不同，就算有一个实现类同时实现了两个接口，且这两个接口有同名的静态方法，也不会强制重写***）
	```java
	public interface MyInterface1 {  
	    public static void show4(){  
	        System.out.println("我是1接口中的静态方法");  
	    }  
	}
	```
	```java
	public interface MyInterface2 {  
	    public static void show4(){  
	        System.out.println("我是2接口中的静态方法");  
	    }  
	}
	```
	```java
	public class mitfImp1 implements MyInterface1,MyInterface2 {
	
	}
	```
	```java
	public class Demo {  
	    public static void main(String[] args) { 
	        MyInterface1.show4();         //遥控器是MyInterface1，而不是mitfImp1
	        MyInterface2.show4();  
	    }  
	}
	```



#####🌑作用
- [x] 使得代码更加简洁，增加可读性，易于管理
	>比如我在测试类中需要到MyInterface中的show方法。
	>- 在show()方法不是静态方法时，我需要先创建一个实现类Imp，然后通过Imp来调用show方法（***可是我只是需要show()方法而已，我不需要Imp类啊，这样就使得代码变得复杂了，可读性也降低了***）；
	>- 在show()方法是静态方法时，我只需要MyInterface.show()即可，***不需要创建一个没有用的Imp类***



## 🌗接口中的私有方法
>private ……
>private static ……

#####🌑作用
- [x] 减少接口中代码的重复性
	- 在不使用接口中的私有方法时
		```java
		public interface MyInterface1 {  
		    default void show1(){  
		        System.out.print("我是show1：");  
		        System.out.print("hello");  
		        System.out.print("world");  
		        System.out.print("java");  
		    }  
		  
		    default void show2(){  
		        System.out.print("我是show2：");  
		        System.out.print("hello");  
		        System.out.print("world");  
		        System.out.print("java");  
		    }  
		}
		```

	- 使用接口中的私有方法时
		```java
		public interface MyInterface1 {  
		    default void show1() {  
		        System.out.print("我是show1：");  
		        show();  
		    }  
		  
		    default void show2() {  
		        System.out.print("我是show2：");  
		        show();  
		    }  
		  
		    private void show() {  
		        System.out.print("hello");  
		        System.out.print("world");  
		        System.out.print("java");  
		    }  
		}
		```


# 🌕Stream流
```
public interface Stream<T> extends BaseStream<T,Stream<T>>
```

## 🌗生成流
>通过数据源【数组，集合等】生成流

#####🌑Collection集合生成流
>直接用集合调用stream()方法
```java
public static void main(String[] args) {  
    List<String> list = new ArrayList<String>();  
    Stream<String> stringStream = list.stream();  
}
```

#####🌑Map集合生成流
>通过使用keySet，values，entrySet等方法生成的集合来调用stream()方法
```java
public static void main(String[] args) {  
    Map<String, Integer> map = new HashMap<>();  
    Stream<String> stream = map.keySet().stream();  //map.keySet()返回的是Set集合
    Stream<Integer> stream1 = map.values().stream();
    Stream<Map.Entry<String, Integer>> stream2 = map.entrySet().stream();
}
```

#####🌑数组生成流
>通过调用Stream.of()方法
```java
public static void main(String[] args) {  
    String arr[] = {"greenteck", "wiggles", "hoan"};  
    Stream<String> ArrStream = Stream.of(arr);  
}
```

#####🌑直接生成流
>通过调用Stream.of()方法
```
public static void main(String[] args) {  
    Stream<String> Stream = Stream.of("greenteck", "wiggles", "hoan");  
}
```

## 🌗中间操作
>打开流，做出数据过滤/映射，然后返回一个新的流

>[!summary] Method Summary
>Stream\<T> filter(Predicate\<T> pre)  ------以Predicate接口为条件，对流进行过滤
>
>Stream\<T> limit(long maxSize)  ------返回一个截取了前maxSize个元素的流
>Stream\<T> skip(long n)  ------跳过n个元素，返回剩下元素的流
>
>static \<T> Stream\<T> concat(Stream a, Stream b) -----合并a和b两个流
>Stream\<T> distinct()  ------去除流中的重复元素，再返回这个流
>
>Stream\<T> sorted()  ------返回一个按自然顺序排序后的流
>Stream\<T> sorted(Comparator c)  ------返回一个根据比较器c排序后的流
>
>Stream\<R> map(Function mapper)  ------返回一个由Function接口处理过的流
>IntStream mapToInt(ToIntFunction mapper)----返回一个由mapper处理过的IntStream

#####🌑filter过滤器
```java
public static void main(String[] args) {  
    List<String> list = new ArrayList<>();  
    list.add("吴彦祖");  
    list.add("陈冠希");  
    list.add("黎明");  
    list.add("吴京");  

       //生成stream流     
    list.stream().filter(new Predicate<String>() {    //调用filter过滤器
        @Override                                   
        public boolean test(String s) {               //重写Predicate接口的test()方法
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

#####🌑limit，skip
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

#####🌑concat，distinct
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

#####🌑sorted
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

#####🌑map，mapToInt
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


## 🌗终结操作
>一个流使用终结操作后，就无法再进行操作了。***这是流的最后一个操作***

>[!summary] Method Summary
>void forEach(Consumer action)  ------对该流的每个元素执行操作
>long count()  ------返回该流中的元素个数

#####🌑forEach
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

#####🌑count
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

## 🌗收集操作
>[!summary] Method Summary
>R collect(Collector collector)  ------按照collector的要求，把元素收集到集合中

#####🌑收集到其他集合
>Collectors.toList()
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

#####🌑收集到Map集合
>Collectors.toMap(new Function<>(){} ,new Function<>(){})
```java
public static void main(String[] args) {  
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
}


{陈冠希=14, 吴彦祖=66}
```























