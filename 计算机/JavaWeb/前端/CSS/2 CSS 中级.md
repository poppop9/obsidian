# 布局
## display
每个HTML元素都有一个默认的 display 值【具体取决于它的元素类型，大多数元素为`block`或`inline`】

### 块级元素 block
>总是从新行开始，并占据可用的全部宽度

>[!hint] 常见的块级元素标签
> - `<div>`
> - `<h1>` - `<h6>`
> - `<p>`
> - `<form>`
> - `<header>`
> - `<footer>`
> - `<section>`

#### 水平居中，左对齐，右对齐
```css
某个需要居中的块级元素 {
    display: block;
    margin: auto auto;
    width: 30%;       /* 设置时需要设置宽度 */    
}

某个需要左对齐的块级元素 {
	position: absolute;    /* 使用绝对定位 */ 
	right: 0px;
}

某个需要左对齐的块级元素 {
	float: left;   /* 使用左浮动 */ 
}
```

### 行内元素 inline
>不从新行开始，仅占用所需的宽度
>
>- ***不允许在元素上设置宽度和高度***
>- 不保留上下内外边距

>[!hint] 常见的行内元素
> - `<span>`
> - `<a>`
> - `<img>`

```css
/* 可以将列表项横向展示 */
li {
  display: inline;
}
```

### 隐藏元素 none
默认情况下`<script>元素`使用`display: none;`

```css
/* 元素被隐藏，不会占用空间 */
h1.hidden {
  display: none;
}

/* 元素被隐藏，但仍然占用空间 */
h1.hidden {
  visibility: hidden;
}
```

### 行内块元素 inline-block
>`inline-block` 结合了 `inline` 和 `block` 的优点
![[Excalidraw/计算机/JavaWeb Draw.md#^group=tsmJGJs5|500]]













## max-width
>`width` 当浏览器窗口小于元素的宽度时，浏览器会将水平滚动条添加到页面
>`max-width` 可以改善浏览器对小窗口的处理，当浏览器窗口小于元素的宽度时，会自动换行

## position
>[!hint] 属性值
> - `static`【默认】：不受 top、bottom、left 和 right 属性的影响，始终根据页面的正常流进行定位
> - `relative`：相对于其正常位置进行定位
> - `fixed`：相对于视口定位【意味着即使滚动页面，也始终位于同一位置】
> - `absolute`：相对于<u>最近的定位祖先元素</u>【除`static`】进行定位，如果没有祖先则祖先为整个文档主体`body`，==会从正常流中删除，意味着会出现重叠==
> - `sticky`：根据用户的滚动位置进行定位【起先会被`relative`，而后为`fixed`】

```css
div.static {
  position: static;
  border: 3px solid #73AD21;
}

/* 左留30px，上留50px */
div.relative {
  position: relative;
  left: 30px;
  top: 50px;
  border: 3px solid #73AD21;
}

/* 始终位于右下角 */
div.fixed {
  position: fixed;
  bottom: 0;
  right: 0;
  width: 300px;
  border: 3px solid #73AD21;
}

div.absolute {
  position: absolute;
  top: 80px;
  right: 0;
  width: 200px;
  height: 100px;
  border: 3px solid #73AD21;
}

div.sticky {
  position: -webkit-sticky;    /* 为了匹配safari */
  position: sticky;
  top: 0;                /* 页面向下滚动时，将粘在页面的上方 */
  background-color: #cae8ca;
  border: 2px solid #4CAF50;
}
```

## 重叠
```css
/* 由于所有元素都设置了absolute，所以会重叠 */
<style>
h1 {
	position: absolute;
	color: red;
	z-index: 1;       /* h1的z-index最大，所以图层在最上面 */
}

p {                       /* p 和 img 未指定z-index，所以按照html的标签顺序自动指定，后面的元素后渲染 */
	position: absolute;
	color: red;                 
}

img {
	position: absolute;
}
</style>

<h1>这是标题</h1> 
<p>p1111111111111111111111111111111111111111111111</p> 
<img src="/i/logo/w3logo-1.png" width="188" height="267" /> 
<p>p2222222222222222222222222222222222222222222222</p>   
```

## 溢出 overflow
- `overflow` 元素内容太大而无法放入指定区域时是***剪裁内容***还是***添加滚动条***，==仅适用于具有指定高度的块元素==
	- `visible` ***默认***，溢出没有被剪裁，==内容在元素框外渲染==
	- `hidden` 溢出被剪裁，其余内容将不可见
	- `scroll` 溢出被剪裁，同时在水平竖直都添加滚动条以查看其余内容
	- `auto` 与 `scroll` 类似，但仅在必要时添加滚动条

>[!hint] 可以单独设置 `overflow-x` 和 `overflow-y`

```css
div {
  width: 200px;
  height: 50px;
  border: 1px dotted black;
  background-color: #eee;

  overflow: visible;
  overflow: hidden;
  overflow: scroll;
  overflow: auto;
}
```

![[Excalidraw/计算机/JavaWeb Draw.md#^group=b8rxkPi3|800]]

## 浮动 float
>[!hint] 属性值
> - `left`  元素浮动到其容器的左侧，==碰到边框就会停下==
> - `right`  元素浮动在其容器的右侧
> - `none`  【默认值】，元素不会浮动（将显示在文本中刚出现的位置）
> - `inherit`  元素继承其父级的 float 值

```css
<p><img src="/i/logo/w3logo-3.png" alt="W3School" style="width:170px;height:170px;margin-left:15px;">
领先的 Web 技术教程 - 全部免费。在 W3School，你可以找到你所需要的所有的网站建设教程。从基础的 HTML 到 CSS，乃至进阶的 XML、SQL、JS、PHP。
我们的参考手册涵盖了网站技术的方方面面。其中包括W3C标准技术：HTML、CSS、XML 。以及其他技术，诸如 JavaScript、PHP、SQL 等。
在 W3School，我们提供上千个实例。通过使用我们的在线编辑器，你可以编辑这些例子，并对代码进行实验。</p>

---
/* 图像会浮动在文字的左侧 */
img {
  float: left;
}

/* 图像会浮动在文字的右侧 */
img {
  float: right;
}
```

>[!attention] 被设置为浮动的元素 不在文档的普通流中，所以文档的普通流中的块框表现得就像浮动框不存在一样
>![[Excalidraw/计算机/JavaWeb Draw.md#^group=vCuuJ0iq|700]]
>==要解决这个问题，可以对==`div2`==使用==`clear`==属性==

## 清除 clear
>[!hint] 属性值
> - `none`  【默认值】允许两侧都有浮动元素
> - `left`  左侧不允许浮动元素
> - `right` 右侧不允许浮动元素
> - `both`  左侧或右侧均不允许浮动元素
> - `inherit`  元素继承其父级的 clear 值

```css
.div1 {
  float: left;
  width: 100px;
  height: 50px;
  margin: 10px;
  border: 3px solid #73AD21;
}

.div2 {
  border: 1px solid red;
  clear: left;            /* 清除div2左边的浮动元素 */
}
```
![[Excalidraw/计算机/JavaWeb Draw.md#^group=sgLQHiif|700]]
# 伪类 - 状态选择器
>伪类用于定义元素的***特殊状态***

根据元素处于什么状态来设置不同样式：
- `:link`  未访问过的链接
- `:visited`  访问过的链接
- `:hover`  鼠标悬停时
- `:active`  被点击时

>[!attention] 
>- a:hover 必须定义在 a:link 和 a:visited 之后，以确保鼠标悬停时的优先级高
>- a:active 必须定义在 a:hover 之后，以确保点击时的优先级高于悬停时

- `:first-child` 匹配某个元素的第一个子元素
	```css
	/* 选择所有<P>元素的第一个<p>元素 */
	p:first-child {
		color: blue;
	}

	/* 选择第一个<p>元素中的所有<i>元素 */
	p:first-child i {
	    color: blue;
	}
	```

---

- 链接的设置
```css
/* 未访问过的链接 */
a:link {
  color: red;
}

/* 访问过的链接 */
a:visited {
  color: green;
}

/* 鼠标悬停时 */
a:hover {
  color: hotpink;
}

/* 被点击时 */
a:active {
  color: blue;
}
```

>[!attention]  链接的状态属性不是html的属性，所以不能使用行内样式

- 提示悬停
```css
p {
	display: none;
	background-color: yellow;
	padding: 20px;
}

/* 数鼠标悬浮在div时，把<p>元素设置为显示 */
div:hover p {
	display: block;
}
```


































