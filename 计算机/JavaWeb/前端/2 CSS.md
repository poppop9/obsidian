---
tags:
  - 计算机/JavaWeb/前端
---
# 🌕语法注意事项
- 注释：`/* 我是注释 */`

- 使用多个引号时，注意双引号里要使用单引号
# 🌕选择器
>[!hint] 优先级：id选择器 > 类选择器 > 元素选择器
### 🌗元素选择器
```css
<style>
	h1,h2,h3 {          /*可以一次性选取多个元素*/
		xxx:yyy;
	}
	span {
		xxx:yyy;
	}
</style>
```
### 🌗类选择器
- 类名相当于是一个标签，可以被多个元素重用
- 一个元素也可以贴多个标签【多个类】
- ***类名不能以数字开头***

```css
<style>
	.001 {
		xxx:yyy;
	}
	.002 {
		xxx:yyy;
	}
</style>
```

```html
<h1 class="001">我是一级标题</h1>
<span class="001 002">我是正文</span>  <!-- 这个元素引用了两个类 -->
```
### 🌗id选择器
- id不能重用
- id不能以数字开头

```css
<style>
	#001 {
		xxx:yyy;
	}
	#002 {
		xxx:yyy;
	}
</style>
```

```html
<h1 id="001">我是一级标题</h1>
<span id="002">我是正文</span>
```

>[!hint] 选择器的组合使用
>
> ```css
> /* 只有具有 class="center" 的 <p\> 元素会居中对齐 */ 
> p.center {
>   text-align: center;
>   color: red;
> }
> ```

### 🌗通用选择器
>通用选择器会影响页面上的每个 HTML 元素

```css
* {
  text-align: center;
  color: blue;
}
```
# 🌕引入方式
### 🌗行内样式
***只作用于当前标签***
`<h1 style="xxx:yyy; xxx:yyy;">HTML 5</h1>`

>[!attention] 不推荐采用，会降低可读性
### 🌗内嵌样式
```html
<!DOCTYPE html>
<html>

<head>
<style>
	选择器 {
		CSS属性名1: 值A;
		CSS属性名2: 值B;
	}
</style>
</head>

<body>
……
</body>

</html>
```
### 🌗外联样式
```css
h1 {
	xxx:yyy;
}
```

```html
<!DOCTYPE html>
<html>
<head>
<link rel="stylesheet" href="路径">  <!-- 在head标签中指定css文件的路径 -->
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>
在·
</body>
</html>
```

>[!hint] 引入方式的优先级
>行内样式 > 在 `head标签` 里内嵌样式和外联样式的顺序【靠后优先】
# 🌕文本
>[!summary] 属性
>- `color`  指定文本的颜色
>- `font-size`  指定文本的大小

```css
<p style="color:Tomato;">China</p>
```
<p style="color:Tomato;">China</p>

##### 🌑指定颜色的 6 种方式
<h1 style="background-color:Tomato;">Tomato</h1>
<h1 style="background-color:rgb(255, 99, 71);">rgb(255, 99, 71)</h1>
<h1 style="background-color:#ff6347;">#ff6347</h1>
<h1 style="background-color:hsl(9, 100%, 64%);">hsl(9, 100%, 64%)</h1>
<h1 style="background-color:rgba(255, 99, 71, 0.5);">rgba(255, 99, 71, 0.5)</h1>
<h1 style="background-color:hsla(9, 100%, 64%, 0.5);">hsla(9, 100%, 64%, 0.5)</h1>

### 🌗文本修饰
`initial` 默认值
`inherit` 从其父元素继承属性
##### 🌑line
`text-decoration-line: none;` 无
`text-decoration-line: overline;` 上划线
`text-decoration-line: underline;` 下划线
`text-decoration-line: line-through;` 删除线
`text-decoration-line: overline underline;` 叠加属性
##### 🌑style
`text-decoration-style: solid;` 单线
`text-decoration-style: wavy;` 波浪线
`text-decoration-style: double;` 双线
`text-decoration-style: dotted;` 点线
`text-decoration-style: dashed;` 虚线
##### 🌑thickness
`text-decoration-thickness: auto;` 浏览器选择装饰线的粗细
`text-decoration-thickness: 5;` 5像素
`text-decoration-thickness: 50%;` 百分比值
### 🌗缩进
`text-indent:像素值`
### 🌗行高
`line-height:像素值`
### 🌗对齐
`text-align:属性值`
属性值可以是`left`，`center`，`right`
# 🌕背景
>[!summary] 属性
> - `background-color`  指定背景色【可以为任何HTML元素设置背景颜色】
> 	- `opacity`  指定透明度【会影响子元素，***使用RGBa不会***】
> - `background-image`   指定背景图像
> - `background-repeat`  指定背景内容是否重复显示
> - `background-attachment`  指定背景滚动 / 固定
> - `background-position`  指定背景的位置
> - `background-clip`
> - `background-origin`
> - `background-size`

### 🌗内容
##### 🌑颜色
```css
/*background-color，opacity*/
<h1 style="background-color:DodgerBlue; opacity: 0.3;">Hello World</h1>
```
<h1 style="background-color:DodgerBlue; opacity: 0.3; ">Hello World</h1>

##### 🌑图像
```css
/*background-image*/
<h1 style="background-image: url('https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87%2F20230805115646.png');">Hello</h1>
```
<h1 style="background-image: url('https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87%2F20230805115646.png');">Hello</h1>

### 🌗参数
##### 🌑重复
默认情况下，`background-image` 属性在水平和垂直方向上都重复显示图像，直到铺满整个指定元素

```css
body {
  background-image: url("……");
  
  background-repeat: repeat-x;  /* 在水平方向重复 */
  background-repeat: repeat-y;   /* 在垂直方向重复 */
  background-repeat: no-repeat;   /* 不重复 */
}
```
##### 🌑位置
```css
body {
  background-image: url("tree.png");

  background-position: right top;  /* 右上角 */
}
```
##### 🌑附着
```css
body {
  background-image: url("tree.png");

  background-attachment: fixed;  /* 固定 */
  background-attachment: scroll;  /* 滚动 */
}
```
# 🌕边框
>[!summary] 属性
>- `border-style`  边框的样式
>- `border-width`  宽度
>- `border-color`
>- `border-radius`  添加圆角

>[!hint] 简写
> `border: width style color;`
### 🌗样式
```css
<p style="border-style: dotted;">hello</p>
<p style="border-style: dashed;">hello</p>
<p style="border-style: solid;">hello</p>
<p style="border-style: double;">hello</p>
<p style="border-style: groove;">hello</p>
<p style="border-style: ridge;">hello</p>
<p style="border-style: inset;">hello</p>
<p style="border-style: outset;">hello</p>
<p style="border-style: none;">hello</p>   /* 无边框 */
<p style="border-style: hidden;">hello</p>   /* 隐藏边框 */
<p style="border-style: dotted dashed solid double;">hello</p>   /* 混合边框 */

/* 单独指定样式 */
p {
  border-top-style: dotted;
  border-right-style: solid;
  border-bottom-style: dotted;
  border-left-style: solid;
}
```
<p style="border-style: dotted;">hello</p>
<p style="border-style: dashed;">hello</p>
<p style="border-style: solid;">hello</p>
<p style="border-style: double;">hello</p>
<p style="border-style: groove;">hello</p>
<p style="border-style: ridge;">hello</p>
<p style="border-style: inset;">hello</p>
<p style="border-style: outset;">hello</p>
<p style="border-style: none;">hello</p>
<p style="border-style: hidden;">hello</p>
<p style="border-style: dotted dashed solid double;">hello</p>

### 🌗参数
##### 🌑宽度
```css
/* 直接指定数值 */
<p style="border-style: groove; border-width: 10px;">hello</p>

/* 指定预定义值 */
<p style="border-style: groove; border-width: thin;">hello</p>
<p style="border-style: groove; border-width: medium;">hello</p>
<p style="border-style: groove; border-width: thick;">hello</p>

/* 上边框 25px，右边框 10px，下边框 4px，左边框 35px */
<p style="border-style: groove; border-width: 25px 10px 4px 35px;">hello</p>
```
<p style="border-style: groove; border-width: 10px;">hello</p>
<p style="border-style: groove; border-width: thin;">hello</p>
<p style="border-style: groove; border-width: medium;">hello</p>
<p style="border-style: groove; border-width: thick;">hello</p>
<p style="border-style: groove; border-width: 25px 10px 4px 35px;">hello</p>

##### 🌑颜色
```css
<p style="border-style: groove; border-color: red;">hello</p>

/* 上红、右绿、下蓝、左黄 */
<p style="border-style: groove; border-color: red green blue yellow;">hello</p>
```
<p style="border-style: groove; border-color: red;">hello</p>
<p style="border-style: groove; border-color: red green blue yellow;">hello</p>

##### 🌑圆角





# 🌕盒子修饰
`width`
`height`
`box-sizing` 设定width和height指的是哪个盒子
`background-color` 指定背景颜色
`border` 边框
`padding` 内边距
`margin` 外边距

```css
div{
	width: 200px;
	height: 200px;
	box-sizing: border-box; <!--设置width和height指的是哪个盒子，这里指的是边框以内的部分-->
	background-color: #4278d5;  <!--背景色-->

	border: 2px solid red;  <!--粗细 线条类型 颜色-->
	padding: 20px 10px 20px 10px;  <!--上右下左-->
	margin: 20px;  <!--上右下左，如果每个方位都一样可以简写为一个值-->
}
```
```html
<div>AAAAAAAAAAAAA  AAA AAAA</div>
```
>[!blank|grid]
>![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230910155942.png)
>![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20230910160003.png)














