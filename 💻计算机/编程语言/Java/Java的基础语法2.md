#计算机/编程语言/Java 
# 从控制台获取数据
### 利用Scanner
```java
Scanner sc = new Scanner(System.in);       //首先创建Scanner对象
int i = sc.nextInt();                  //接收数据，nextInt与int对应
```

# 分支语句
### if…else…语句
```java
if(关系表达式1){
	语句体1;             
}else if（关系表达式2){
	语句体2;
}else{
	语句体3;
}
```
>如果在if语句中加入return;***会在执行完if语句之后不在向下执行***[^1]

[^1]:就是不在执行根if同级别（同一缩进）下的语句

### switch语句
>用表达式的值和case的值做比较，相等就输出对应语句体的内容，然后break结束；不相等就继续向下比较
```java
public static void main(String[] args) {  
    switch (1) {  
        case 2:  
            System.out.println(2);  
            break;               //结束switch语句
        case 3:  
        case 1:  
            System.out.println("1或3");  
            break;  
        default:               //当所有情况都不匹配时，就执行此处的内容。
            System.out.println("没有");  //即使情况符合，没有break，也会执行default
    }  
}


1或3
```

***如果有一步没有加break，那么下一步不会判断case，而是直接执行语句体，直到遇见break或default***
```java
switch (1) {  
    case 1:  
        System.out.println(2);  
    case 3:  
    case 4:  
        System.out.println("1或3");  
        break;  
    default:  
        System.out.println("没有");  
}


2
1或3
```

# 循环语句
### for循环
```java
for (初始化语句;条件判断语句;条件控制语句){
	循环体语句;
}

执行初始化语句，
执行条件判断语句
	false，循环结束
	true，执行循环体语句
执行条件控制语句
执行条件判断语句……
```

### while循环
```java
初始化语句
while(条件判断语句){
	循环体语句;
	条件控制语句;
}
```

### do…while循环
```java
初始化语句
do{
	循环体语句;
	条件控制语句;
}while(条件判断语句);

执行初始化语句
执行循环体语句
执行条件控制语句
执行条件判断语句
	false，循环结束
	true，执行循环体语句……
```

### 死循环
##### for死循环
```java
for(;;){

}
```

##### while死循环
```jaca
while(true){

}
```

##### do…while死循环
```java
do{

}while(true);
```


### 跳转控制语句
##### continue
>基于条件控制，跳过某次循环体内容的执行，继续下一次执行
```java
for (int i = 1; i <= 5; i++) {  
    if (i % 2 == 0) {  
        continue;               //if正确则执行continue，则会跳过这次的sout
    }  
    System.out.print(i);  
}


135
```

##### break
>基于条件控制，中止循环体内容的执行
```java
for (int i = 1; i <= 5; i++) {  
    if (i % 2 == 0) {  
        break;                 
    }  
    System.out.print(i);  
}


1
```


# 数组
>用于定义***多个相同类型***的数据

### 数组初始化时的默认值

| **数据类型**          | **默认值**          |
| -------------- | -------------- | 
| 整数 | 0 | 
| 浮点数 | 0.0 |
| 布尔值 | false | 
| 字符 | 空字符 |
| 引用数类 | null | 

### 动态初始化
>![[Excalidraw/计算机/编程语言/Java/Java的基础语法2 Draw.md#^group=C5QuaRNn|600]]

### 静态初始化
```java
int arr[] = {1, 2, 3};
```

### 访问
##### 访问数组
```java
System.out.println(arr);          //会输出一个内存地址
```

##### 访问数组的元素
```java
System.out.println(arr[0]);      //通过索引，访问数组元素
```


### 多个数组指向相同
```java
int arr1[] = new int[3];      //假设arr1的内存地址为001
int arr2[] = arr1;            //那么arr2的内存地址也为001
```
>如果修改arr2的元素值，arr1的元素值也会相应改变


# 字符串
>是一种特殊的数据类型，不属于基本数类

***字符串的值在创建之后不能修改***

### 创建字符串
##### 利用char数组创建
```java
public static void main(String[] args) {  
    char c[] = {94, 94, 43};  
    String s = new String(c);  
    System.out.println(s);  
}


^^+
```
##### 直接创建
```java
public static void main(String[] args) {  
    String s = "^^+";  
    System.out.println(s);  
}


^^+
```

### 字符串的比较
>由于”`==`“比较的是地址值，所以字符串的内容比较要使用equals()方法
```java
public static void main(String[] args) {  
    String s1 = new String(new char[]{'a', 'b'});  
    String s2 = new String(new char[]{'a', 'b'});  
    System.out.println(s1.equals(s2));  
}


true
```

### 逐个遍历字符串
```java
public static void main(String[] args) {  
    String s = "green";  
    for (int i = 0; i < s.length(); i++) {  
        System.out.print(s.charAt(i) + " ");  
    }  
}


g r e e n 
```

### String
```
public final class String extends Object
implements Serializable,Comparable<StringBuilder>,CharSequence,Constable,ConstantDesc
```

>[!summary] ***Method Summary***
>String[] split(String regex)  ------以regex为标志分离字符串

```java
public static void main(String[] args) {  
    String s1 = new String("12,23,3,4");  
    String[] ss = s1.split(",");  
    for (String s : ss) {  
        System.out.print(s);  
    }  
}


122334
```

### StringBuilder
```
public final class StringBuilder extends Object
implements Serializable,Comparable<StringBuilder>,CharSequence
```

>[!summary] ***Method Summary***
>StringBuilder()  ------构造方法1
>StringBuilder(String s)  ------构造方法2
>
>StringBuilder append(T t)  ------给字符串添加数据
>String toString(StringBuilder sb)  ------把StringBuilder转成String
>StringBuilder reverse()  ------翻转StringBuilder

```java
public static void main(String[] args) {  
    StringBuilder sb = new StringBuilder("green");  
    sb.append("te").append("ck");  
    sb.reverse();  
    String s = sb.toString();              //转换为String
    System.out.println(s);  
}


kcetneerg
```

##### String与StringBuilder的区别
- [x] String做拼接的时候会在堆内存那里再创建一个地址，这样会增加缓存；StringBuilder不会增加缓存
- [x] String创建字符串的值不会改变，要改变只能拼接生成具有新的地址值的字符串；StringBuilder可以在不改变地址值的情况下改变内容

***StringBuffer[^2]是StringBuilder的线程安全类***

[^2]:可以多个线程之间共享可变字符序列，运行起来比StringBuilder慢





