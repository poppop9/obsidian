# Random
```java
Random r = new Random();
int number = r.nextInt(10);   //代表的数据范围是0-9
```

# Arrays
> `Arrays` 里面包含了操作<u>数组</u>的多种方法

```
public class Arrays extends Object
```

>[!summary]
>`String toString(arr)`  返回指定数组内容的字符串表示形式
>`sort(arr)`  将数组从小到大排列
>`List<\T> asList(T…a)`  将多个参数转成一个固定大小的List集合【这个集合无法做增删操作】
> `int binarySearch(数组, 数组元素);` 根据数组元素，返回该元素在数组中的索引

# Math
>其中集合了基本的数学运算方法

>[!hint] 属性
>`Math.PI`  圆周率

>[!hint] 方法
> `public static int abs(int a)`  返回参数的绝对值
> `public static double ceil(double a)`  返回大于或等于参数的最小double值，等于一个整数
> `public static double floor(double a)`  返回小于或等于参数的最大double值，等于一个整数
> `public static int round(float a)`  按照四舍五入返回最接近参数的int
> `public static int max(int a,int b)`  返回两个int值中的较大值
> `public static int min(int a,int b)`  返回两个int值中的较小值
> `public static double pow(double a,double b)`  返回a的b次幂的值
> `public static double random()`  返回值为double的正值，\[0.0，1.0）

# System
>[!hint] 方法
>`System.exit(0)` 可以终止java虚拟机的运行
>`System。CurrentTimeMillis()`  计算1970年，1月1日与当前时间的差值，单位为 `ms`

# Object
>[!hint] 方法
>`toString()`  在类中创建此方法，可以在打印对象名称时更加的简明
>`equals()`  用来比较两个对象【包含字符串】的<u>内容</u>【而不是地址】，在比较对象的内容时，需要在对象所属类里重写 `equals()`，`hashcode()`






















