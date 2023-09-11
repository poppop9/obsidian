# 引入方式

### 定义在HTML文件中
```html
<script>
	…………
</script>
```
***一般放置在\<body\>的底部***
### 定义在外部的.js文件中
```html
<script src="demo.js"></script>
```
```js
…………
```

# 基础语法

### 注释
与Java相同
### 输出语句
- `alert` 
  ***会在浏览器弹出警告框***
  ```js
  alert("hello javascript");
  ```
  ![[Excalidraw/计算机/JavaWeb.md#^group=L84gWEf4]]
- `document.write` 
  ***会把内容直接写入到浏览器里显示***
- `console.log` 
  ***写入浏览器的控制台***
### 变量
##### var
```js
var a = 20;
a = "张三"；
```

- ***var可以存放不同类型的值***
- var不管在哪里定义，都是全局变量
  ```js
{
  var a = 10;
}
alert(a);
  ```
- var可以重复定义
  ```js
{
  var a = 10;
  var a = "js";
}
  ```
##### let
- ***定义的是局部变量***
- 不可以重复声明
##### const
- 定义常量，不可修改

