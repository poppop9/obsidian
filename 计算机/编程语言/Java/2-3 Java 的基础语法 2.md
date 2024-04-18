# 从控制台获取数据
## 利用Scanner
```java
Scanner sc = new Scanner(System.in);       //首先创建Scanner对象
int i = sc.nextInt();                  //接收数据，nextInt与int对应
```

# 分支语句
## if…else…语句
```java
if(关系表达式1){
	语句体1;             
}else if（关系表达式2){
	语句体2;
}else{
	语句体3;
}
```

## if{…return;}
>如果在 if 语句中加入`return`,会在执行完 if 语句之后不在执行跟 if 同级别【同一缩进】下的语句

```java
if() {
	代码 A;
	…
	return;
}
代码 B
```

## switch语句
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
## for循环
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

## while循环
```java
初始化语句
while(条件判断语句){
	循环体语句;
	条件控制语句;
}
```

## do…while循环
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

## 死循环
### for死循环
```java
for(;;){

}
```

### while死循环
```jaca
while(true){

}
```

### do…while死循环
```java
do{

}while(true);
```


## 跳转控制语句
### continue
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

### break
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

>[!hint] 数组初始化时的默认值
>
>| **数据类型** | **默认值** |
> | -------- | ------- |
> | 整数       | 0       |
> | 浮点数      | 0.0     |
> | 布尔值      | false   |
> | 字符       | 空字符     |
> | 引用数类     | null    |

## 初始化
- 动态初始化
![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403022043058.png)

- 静态初始化
```java
int arr[] = {1, 2, 3};
```

## 操作
### 访问数组
```java
System.out.println(arr);          //会输出一个内存地址
```

### 访问数组的元素
```java
System.out.println(arr[0]);      //通过索引，访问数组元素
```

### 获取数组长度
```java
int l = arr.length;
```

>[!hint] 多个数组指向相同
>>如果修改arr2的元素值，arr1的元素值也会相应改变
> ```java
> int arr1[] = new int[3];      //假设arr1的内存地址为001
> int arr2[] = arr1;            //那么arr2的内存地址也为001
> ```

