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
	.a01 {
		xxx:yyy;
	}
	.a02 {
		xxx:yyy;
	}
</style>
```

```html
<h1 class="a01">我是一级标题</h1>
<span class="a01 a02">我是正文</span>  <!-- 这个元素引用了两个类 -->
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
# 🌕框模型
元素总宽度 = width + 左右padding + 左右border + 左右margin + outline
![[Excalidraw/计算机/JavaWeb Draw.md#^group=42TgzTKXcFDmL_5ajKxmy|600]]

>[!summary] 属性
>- `background`  背景
>- `border`  边框
>- `margin`  外边距【允许负值】
>- `padding`  内边距【***呈现元素的背景***，不允许负值】
>- `width`  宽度【只是内容，***不包括padding，margin，border***】
>- `height`  高度
>- `box-sizing`  设定width和height指的是哪个盒子
>	- `content-box`  仅包括内容区域
>	- `border-box`  包括内容，padding，border
>	- `padding-box`  包括内容，padding
>	- `inherit`  继承父元素
>- `outline`  轮廓
### 🌗背景
>背景 = padding + 内容

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

##### 🌑指定颜色的 6 种方式
<h1 style="background-color:Tomato;">Tomato</h1>
<h1 style="background-color:rgb(255, 99, 71);">rgb(255, 99, 71)</h1>
<h1 style="background-color:#ff6347;">#ff6347</h1>
<h1 style="background-color:hsl(9, 100%, 64%);">hsl(9, 100%, 64%)</h1>
<h1 style="background-color:rgba(255, 99, 71, 0.5);">rgba(255, 99, 71, 0.5)</h1>
<h1 style="background-color:hsla(9, 100%, 64%, 0.5);">hsla(9, 100%, 64%, 0.5)</h1>

##### 🌑内容
###### 🌙颜色
```css
/*background-color，opacity*/
<h1 style="background-color:DodgerBlue; opacity: 0.3;">Hello World</h1>
```
<h1 style="background-color:DodgerBlue; opacity: 0.3; ">Hello World</h1>

###### 🌙图像
```css
/*background-image*/
<h1 style="background-image: url('https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87%2F20230805115646.png');">Hello</h1>
```
<h1 style="background-image: url('https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87%2F20230805115646.png');">Hello</h1>

##### 🌑参数
###### 🌙重复
默认情况下，`background-image` 属性在水平和垂直方向上都重复显示图像，直到铺满整个指定元素

```css
body {
  background-image: url("……");
  
  background-repeat: repeat-x;  /* 在水平方向重复 */
  background-repeat: repeat-y;   /* 在垂直方向重复 */
  background-repeat: no-repeat;   /* 不重复 */
}
```
###### 🌙位置
```css
body {
  background-image: url("tree.png");

  background-position: right top;  /* 右上角 */
}
```
###### 🌙附着
```css
body {
  background-image: url("tree.png");

  background-attachment: fixed;  /* 固定 */
  background-attachment: scroll;  /* 滚动 */
}
```
### 🌗边框
>[!summary] 属性
>- `border-style`  边框的样式
>- `border-width`  宽度
>- `border-color`
>- `border-radius`  添加圆角

>[!hint] 简写
> `border: width style color;`
##### 🌑样式
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

##### 🌑参数
###### 🌙宽度
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

###### 🌙颜色
```css
<p style="border-style: groove; border-color: red;">hello</p>

/* 上红、右绿、下蓝、左黄 */
<p style="border-style: groove; border-color: red green blue yellow;">hello</p>
```
<p style="border-style: groove; border-color: red;">hello</p>
<p style="border-style: groove; border-color: red green blue yellow;">hello</p>

###### 🌙圆角
```css
<p style="border-style: groove; border-radius: 12px;">hello</p>
```
<p style="border-style: groove; border-radius: 12px;">hello</p>

### 🌗内外边距
```css
/* 允许指定单个外边距 */
p {
  margin-top: 100px;    /* 指定数值 */
  margin-bottom: auto;   /* 在其容器中水平居中 */
  margin-right: inherit;    /* 继承父元素的外边距 */
  margin-left: 80px;
}
```
### 🌗轮廓
>[!summary] 属性
> - `outline-style`  样式
> 	- `dotted`  点状轮廓
> 	- `dashed`  虚线轮廓
> 	- `solid`   实线轮廓
> 	- `double`   双线轮廓
> 	- `groove`  3D 凹槽轮廓
> 	- `ridge`   3D 凸槽轮廓
> 	- `inset`  3D 凹边轮廓
> 	- `outset`  3D 凸边轮廓
> 	- `none`  无轮廓
> 	- `hidden`  隐藏轮廓
> - `outline-color`  
> - `outline-width`
> - `outline-offset`  轮廓偏移【轮廓与border之间的空间】
# 🌕文本
### 🌗基础属性
##### 🌑颜色，大小，字体，斜粗变体
>[!summary] 属性
>- `color`  指定文本的颜色
>- `font-size`  指定文本的大小【普通文本默认大小为 16px】
>	- `px`
>	- `em`
>	- `vm`
>- `font-family`  指定字体
>	- 有多个字体时，应以逗号分隔
>	- 字体名称不止一个单词，则必须用引号引起来
>- `font-style`  斜体
>- `font-weight`  粗体
>- `font-variant`  变体

```css
/* color, font-size, font-family */
<p style="color:Tomato; font-size:30px; font-family: serif, Times;">China</p>

p {
  font-size: 1em;  /* em允许用户在浏览器菜单中调整文本大小，1em = 16px */
}

p {
  font-size:10vw;  /* vm可以根据浏览器窗口的大小，调整字体大小 */
}               /* 10vm表示为字体占窗口的10% */
```
<p style="color:Tomato; font-size:30px; font-family: serif, Times;">China</p>

```css
p {
  font-style: normal;
  font-style: italic;  /* 斜体 */
}

p {
  font-weight: normal;
  font-weight: bold;  /* 粗体 */
}

p {
  font-variant: normal;
  font-variant: small-caps;  /* 将所有字母大写，但是大写的字母size和小写差不多 */
}
```
### 🌗位置
##### 🌑水平对齐，垂直对齐，方向
>[!summary] 属性
>- `text-align`  水平对齐
>	- `left`
>	- `center`
>	- `right`
>	- `justify`  将文本内容拉伸至每一行都具有相同宽度
>- `vertical-align`  垂直对齐【当文本与其他元素的相对位置】
>	- `top`  其他元素相对于文本位于上部
>	- `middle`  居中
>	- `bottom`
>- `direction`  文本方向
>	- `ltr`   从左到右
>	- `rtl`
>	- `inherit`

```css
/* vertical-align */
<p style = "vertical-align:top;">一幅 <img src="https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87%2F20230805115646.png"> 上对齐的图像</p>

/* direction */
<p style = "direction:rtl;"> hello </p>
```
<p style = "vertical-align:top;">一幅 <img src="https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87%2F20230805115646.png"> 上对齐的图像</p>
<p style="direction:rtl;"> hello </p>

### 🌗其他属性
##### 🌑装饰
>[!summary] 属性
> - `initial` 默认值
> - `inherit` 从其父元素继承属性
>- `text-decoration`  指定线条的位置
>- `text-decoration-style`  指定线条的样式
>	- `solid`  实线
>	- `wavy`  波浪线
>	- `double`  双线
>	- `dotted`  点线
>	- `dashed`  虚线
>- `text-decoration-thickness`  指定线条的粗细
>	- `auto`
>	- `……px`
>	- `……%`
###### 🌙line
```css
/* 删除所有文本装饰【常用于删除超链接的下划线】 */
<p style="text-decoration:none;">hello</p>
/* 上划线 */
<p style="text-decoration:overline;">hello</p>
/* 下划线 */
<p style="text-decoration:underline;">hello</p>
/* 删除线 */
<p style="text-decoration:line-through;">hello</p>
/* 多线 */
<p style="text-decoration:overline underline;">hello</p>
```
<p style="text-decoration:overline;">hello</p>
<p style="text-decoration:underline;">hello</p>
<p style="text-decoration:line-through;">hello</p>
<p style="text-decoration:overline underline;">hello</p>

##### 🌑文本间距
```css
p {
  text-indent: 50px;  /* 指定文本的首行缩进 */
}

h1 {
  letter-spacing: 3px;  /* 指定文本中每个 字符/字母 的间距 */
}

h1 {
  word-spacing: 10px;  /* 指定文本中每个 词语/单词 的间距 */
}

p.small {
  line-height: 0.8;  /* 指定文本行之间的间距 */
}

p {
  white-space: nowrap;  /* 空白处理，防止文本换行 */
}
```
##### 🌑文本转换
```css
p.uppercase {
  text-transform: uppercase;   /* 把文本全部大写 */
}

p.lowercase {
  text-transform: lowercase;   /* 把文本全部小写 */
}

p.capitalize {
  text-transform: capitalize;  /* 把文本首字母大写 */
}
```
##### 🌑文本阴影
```css
h1 {
  text-shadow: 2px 2px;  /* 指定水平阴影，垂直阴影 */
}

h1 {
  text-shadow: 2px 2px red;  /* 指定水平阴影，垂直阴影，颜色 */
}

h1 {
  text-shadow: 2px 2px 5px red;  /* 指定水平阴影，垂直阴影，模糊效果，颜色 */
}
```
<p style="text-shadow: 2px 2px 5px red;">文本阴影效果！</p>

# 🌕链接
根据链接处于什么状态来设置链接的不同样式：
- `a:link`  未访问过的链接
- `a:visited`  访问过的链接
- `a:hover`  鼠标悬停时
- `a:active`  被点击时












