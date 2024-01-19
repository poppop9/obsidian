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

>[!hint] 定义position的注意点
>- 一般会把父元素定义为 `relative` ，子元素定义为 `absolute` ，这样子元素就会在父元素的里面进行绝对定位，而不是相对于整个文档

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

| 选择器 | 例子 | 例子描述 |
| :--: | :--: | :--: |
| :focus | input:focus | 选择获得焦点的 <input> 元素 |
| :first-child | p:first-child | 匹配\<p\>元素的第一个子元素 |
| :last-child | p:last-child | 选择作为其父的最后一个子元素的每个\<p\>元素 |
| :nth-child(n) | p:nth-child(2) | 选择作为其父的第二个子元素的每个\<p\>元素 |
| :nth-last-child(n) | p:nth-last-child(2) | 选择作为父的第二个子元素的每个\<p\>元素，从最后一个子元素计数 |
| :only-child | p:only-child | 选择作为其父的唯一子元素的\<p\>元素 |
| :lang(language) | p:lang(it) | 选择每个 lang 属性值以 "it" 开头的\<p\>元素 |
| :target | \#news\:target | 选择当前活动的 \#news 元素（单击包含该锚名称的 URL） |
| :root | root | 选择元素的根元素 |
| :checked | input:checked | 选择每个被选中的 <input> 元素 |
| :disabled | input:disabled | 选择每个被禁用的 <input> 元素 |
| :empty | p:empty | 选择没有子元素的每个 \<p\> 元素 |
| :enabled | input:enabled | 选择每个已启用的 <input> 元素 |
| :first-of-type | p:first-of-type | 选择作为其父的首个\<p\>元素的每个\<p\>元素 |
| :in-range | input:in-range | 选择具有指定范围内的值的 <input> 元素 |
| :valid | input:valid | 选择所有具有有效值的 <input> 元素 |
| :invalid | input:invalid | 选择所有具有无效值的 <input> 元素 |
| :last-of-type | p:last-of-type | 选择作为其父的最后一个\<p\>元素的每个 \<p\> 元素 |
| :not(selector) | :not(p) | 选择每个非\<p\>元素的元素 |
| :nth-last-of-type(n) | p:nth-last-of-type(2) | 选择作为父的第二个\<p\>元素的每个\<p\>元素，从最后一个子元素计数 |
| :nth-of-type(n) | p:nth-of-type(2) | 选择作为其父的第二个\<p\>元素的每个\<p\>元素 |
| :only-of-type | p:only-of-type | 选择作为其父的唯一\<p\>元素的每个\<p\>元素 |
| :optional | input:optional | 选择不带 "required" 属性的 <input> 元素 |
| :out-of-range | input:out-of-range | 选择值在指定范围之外的 <input> 元素 |
| :read-only | input:read-only | 选择指定了 "readonly" 属性的 <input> 元素 |
| :read-write | input:read-write | 选择不带 "readonly" 属性的 <input> 元素 |
| :required | input:required | 选择指定了 "required" 属性的 <input> 元素 |

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

# 伪元素
>伪元素用于设置元素指定部分的样式，可以在内容之前或之后插入内容

## ::first-line
>向文本的 ***首行*** 添加特殊样式，==只能应用于块级元素==

```css
<p>您可以使用 ::first-line 伪元素将特殊效果添加到文本的第一行。一些更多的文字。越来越多，越来越多，越来越多，越来越多，越来越多，越来越多，越来越多，越来越多，越来越多，越来越多。</p>

<style>
	p::first-line {
		color: red;
		font-variant: small-caps;
	}
</style>

---
<p>元素太长会换行，则第一行会被设置为红色
```

>[!hint] 适用于`::first-line`的属性
> - 字体，颜色，背景
> - word-spacing
> - letter-spacing
> - text-decoration
> - vertical-align
> - text-transform
> - line-height
> - clear

## ::first-letter
>向文本的 ***首字母*** 添加特殊样式，==只适用于块级元素==

```css
p::first-letter {
    color: red;
    font-size: xx-large;
}
```

>[!hint] 适用于`::first-letter`的属性
> - 字体，颜色，背景
> - 内外边距
> - 边框
> - text-decoration
> - vertical-align（仅当 "float" 为 "none"）
> - text-transform
> - line-height
> - float
> - clear

## ::before
>在元素内容之前插入一些内容

```css
/* 在每个<h1>元素之前插入一幅图像 */
h1::before {
    content: url(/i/photo/smile.gif);
}
```

## ::after
>在元素内容之后插入一些内容

## ::selection
>匹配用户选择的元素部分

```css
/* 会对鼠标选择的文本进行处理 */
::selection {
    color: red;
    background: yellow;
}

/* 针对 Firefox 的代码 */
::-moz-selection { 
    color: red;
    background: yellow;
}
```

>[!hint] 适用于`::selection`的属性
> - `color`
> - `background`
> - `cursor`
> - `outline`

# 导航栏
>导航栏基本上是链接列表

>[!hint] 设置导航时的注意点
> - `display: block;` 将链接显示为块元素***可以使整个链接区域都可以被单击***，我们还可以指定更多的参数
> - `width: 60px;` 默认情况下，块元素会占用全部可用宽度，我们需要指定合适的 width
> - `position: fixed;` 固定导航栏

## 垂直导航栏
>列表本身就是垂直的，相对简单些

## 水平导航栏
>使用 ***行内*** 或 ***浮动***

```css
<ul>
  <li><a href="#home">Home</a></li>
  <li><a href="#news">News</a></li>
  <li><a href="#contact">Contact</a></li>
  <li><a href="#about">About</a></li>
</ul>

/* 使用行内---------------------- */
ul {
	list-style-type: none;
	margin: 0;
	padding: 0;
}

li {
	display: inline;
}

/* 使用浮动------------------- */
li {
	float: left;
}

a {
	display: block;
	padding: 8px;
	background-color: #dddddd;
}
```

## 响应式顶部导航栏
```css
/* 在屏幕尺寸小于或等于600像素时垂直堆叠导航栏 */
@media screen and (max-width: 600px) {
	ul.topnav li {
		float: none;
	}
}
```

## 悬浮下拉菜单
>基本思路：
>1. 先把下拉菜单创建好
>2. 再将其设置为`display: none;` 
>3. 设置悬浮`:hover` 时 `display: block;`

```css
<li><a href="#home">Home</a></li>
<li><a href="#news">News</a></li>
<li class="dropdown">
	<a href="javascript:void(0)" class="dropbtn">Dropdown</a>
	<div class="dropdown-content">
		<a href="#">Link 1</a>
		<a href="#">Link 2</a>
		<a href="#">Link 3</a>
	</div>
</li>

.dropdown-content {
	display: none;
	position: absolute;
	background-color: #f9f9f9;
	min-width: 160px;
	box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);  /* 一般下拉菜单会设置阴影 */
	z-index: 1;
}

.dropdown:hover .dropdown-content {
	display: block;
}
```

# 计数器
>计数器使您可以根据内容在文档中的位置来调整其外观

- `counter-reset`  创建或重置计数器
- `counter-increment`  递增计数器值
- `content`  插入生成的内容
- `counter()` /`counters()`  将计数器的值添加到元素

---

```css
<h2>HTML 教程</h2>
<h2>CSS 教程</h2>
<h2>JavaScript 教程</h2>

<style>
	body {
		counter-reset: index;   /* 创建 */
	}
	
	h2::before {
		counter-increment: index;      /* 递增 */
		content: "Section " counter(index) ": ";    /* 插入内容 */
	}
</style>
```
![[Excalidraw/计算机/JavaWeb Draw.md#^group=FEjVXHLN|300]]

---

```css
/* 嵌套计数器 */
body {
	counter-reset: section;
}

h1 {
	counter-reset: subsection;
}

h1::before {
	counter-increment: section;
	content: "Section " counter(section) ". ";
}

h2::before {
	counter-increment: subsection;
	content: counter(section) "." counter(subsection) " ";
}
```

# 单位
## 绝对单位
>绝对长度表示的长度都将恰好显示为这个尺寸，==不建议在屏幕上使用绝对长度单位，因为屏幕尺寸变化很大==

| 单位   | 描述                       |
|------|--------------------------|
| cm   | 厘米                       |
| mm   | 毫米                       |
| in   | 英寸 (1in = 96px = 2.54cm) |
| px | 像素 (1px = 1/96th of 1in) |
| pt   | 点 (1pt = 1/72 of 1in)    |
| pc   | 派卡 (1pc = 12 pt)         |


## 相对单位
>相对长度规定相对于另一个长度属性的长度，相对长度单位在不同渲染介质之间缩放表现得更好

| 单位   | 描述                                       |
|------|------------------------------------------|
| em   | 相对于元素的字体大小（2em 表示当前字体大小的 2 倍） |
| ex   | 相对于当前字体的 x-height(极少使用)                  |
| ch   | 相对于 "0"（零）的宽度                            |
| rem  | 相对于根元素的字体大小                   |
| vw   | 相对于视口*宽度的 1%                             |
| vh   | 相对于视口*高度的 1%                             |
| vmin | 相对于视口*较小尺寸的 1％                           |
| vmax | 相对于视口*较大尺寸的 1％                           |
| %    | 相对于父元素                                   |

>[!hint] em 和 rem 可用于创建完美的可扩展布局！

视口 = 浏览器窗口的尺寸。如果视口为50厘米宽，则 1vw = 0.5 厘米。






























