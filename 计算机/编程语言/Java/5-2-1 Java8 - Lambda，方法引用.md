
# Lambda 表达式
>[!quote] Lambda 表达式
>`() -> {……}`
> ```
> ()：小括号里面没有内容，表示该方法没有参数。如果有多个参数，用逗号隔开
> ->：表示指向要做的事情
> {}：大括号里的内容表示需要做的事情（方法体内容）
> ```

>[!hint] 作用
>- **简化代码**
> ```java
> // 使用匿名内部类实现多线程时
> public static void main(String[] args) {
> 	new Thread(new Runnable() {
> 		@Override
> 		public void run() {
> 			System.out.println("多线程启动了");
> 		}
> 	}).start();
> }
> ```
> 
> ```java
> // 使用Lambda表达式实现多线程时
> public static void main(String[] args) {
>   new Thread(() -> {
> 	  System.out.println("多线程启动了");
>   }).start();
> }
> ```
> 
> - **简化字节码文件**
> 	- 使用匿名内部类时，会在编译之后，单独产生一个字节码文件
> 	- 使用 Lambda 表达式时，编译之后不会单独产生一个字节码文件，而是在运行时动态生成

---

>[!hint] 使用前提
>- **这个类要有一个接口**：比如需要的 MyRunnable 这个类有一个接口 Runnable
>- **这个接口中有且仅有一个抽象方法**：比如 Runnable 接口里只有一个抽象方法 run

```java
public interface Eatable {  
    int add(int a, int b);    //一个接口且有且仅有一个抽象方法
}
```

```java
public class EatableDemo {  
    public static void main(String[] args) {  
        useEatable((int a, int b) -> {   // 书写Eatable的实现内部类
            return a + b;                 //方法的具体实现
        });  
    }  
  
    public static void useEatable(Eatable e) {  //通过接口的实现类对象调用add方法  
        int sum = e.add(1, 2);  
        System.out.println(sum);  
    }  
}

---
3
```

>[!hint] 简写 Lambda 表达式
> - 小括号里的参数类型可以省略
> - 如果参数只有一个，那么小括号可以省略
> - 如果大括号里的语句只有一条，那么可以省略大括号和分号和 return
> 
> ```java
> useEatable((int a, int b) -> {   
> 	return a + b;                 
> });   
> 
> // 改写为
> useEatable((a, b) -> a + b);                           
> ```

# 方法引用
>[!quote] 方法引用
>方法引用 `::` 简化了 Lambda 的书写

>[!hint]+ 引用类的静态方法
> ```java
> public interface parseInt {  
>     int convert(String s);  
> }
> 
> public class Demo {  
>     psvm {  
> 	    //Integer这个接口里面有个静态的parseInt方法
>         useParseInt(Integer::parseInt);  
>     }  
>   
>     public static void useParseInt(parseInt p) {  
>         System.out.println(p.convert("123"));  
>     }  
> }
> ```

>[!hint]+ 引用对象的实例方法
> ```java
> public interface Printable {  
>     void printString(String s);  
> }
> ```
> 
> ```java
> public class Demo {  
>     public static void main(String[] args) {  
>         //usePrintable(s -> System.out.println(s));  
>         usePrintable(System.out::println);        //自动把参数String s传递给println方法  
>     }                                             //out是PrintStream的实例对象，里面有println方法
>   
>     public static void usePrintable(Printable p) {  
>         p.printString("Hello Java");  
>     }
> }
> 
> 
> Hello Java
> ```

>[!hint]+ 引用类的实例方法
> ```java
> public interface SubString {  
>     String sub(String s, int x, int y);  
> }
> ```
> 
> ```java
> public class Demo {  
>     public static void main(String[] args) {  
>         useSubString(String::substring);  
>     }  
>   
>     public static void useSubString(SubString p) {  
>         System.out.println(p.sub("Hello Java", 2, 5));  
>     }  
> }
> ```

>[!hint]+ 引用构造方法
> ```java
> public class student {  
>     private int age;  
>     private String name;  
>   
>     public student(int age, String name) {  
>         this.age = age;  
>         this.name = name;  
>     }  
>   
>     public int getAge() {return age;}  
>     public void setAge(int age) {this.age = age;}  
>   
>     public String getName() {return name;}  
>     public void setName(String name) {this.name = name;}  
> }
> ```
> 
> ```java
> public interface studentBuilder {  
>     student build(int age, String name);  
> }
> ```
> 
> ```java
> public class Demo3 {  
>     public static void main(String[] args) {  
> 	    // 匿名内部类
> 		// useStudentBuilder(new studentBuilder() {  
> 		//     @Override  
> 		//     public student build(int age, String name) {         
> 		//         return new student(age, name);  
> 		//     }  
> 		// });  
> 	
> 		// Lambda表达式
> 		// useStudentBuilder((int age, String name) -> {           
> 		//     return new student(age, name);  
> 		// });  
>   
>         useStudentBuilder(student::new);     // new代表了构造方法
>     }  
>   
>     public static void useStudentBuilder(studentBuilder sb) {  
>         student s = sb.build(12, "吴彦祖");  
>         System.out.println(s.getAge() + "," + s.getName());  
>     }  
> }
> ```

