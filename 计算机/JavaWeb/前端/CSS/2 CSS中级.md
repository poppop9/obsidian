# 布局
## display
每个HTML元素都有一个默认的 display 值【具体取决于它的元素类型，大多数元素为`block`或`inline`】

### 块级元素 block
>总是从新行开始，并占据可用的全部宽度。***HTML会自动地在块级元素前后添加一个额外的空行***

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
>默认情况下`<script>元素`使用`display: none;`

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
### 弹性容器 Flexbox
[[#Flexbox]]
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
# Flexbox
>`Flexbox`可以更轻松地设计灵活的响应式布局结构，而无需使用 `float` 和`position`

```css
.flex-container {
	background-color: DodgerBlue;
	display: flex;      /* 必须将父元素设置为flex */
	flex-direction: row;
	flex-wrap: wrap;
	justify-content: center;
}

.flex-container > div {
	background-color: #f1f1f1;
	margin: 10px;
	padding: 20px;
	font-size: 30px;
}

/* html */
<div class="flex-container">   /* flex容器 */
	<div>1</div>        /* flex项目 */
	<div>2</div>
	<div>3</div>  
</div>
```
## 弹性容器
- `flex-direction` ***定义容器要在哪个方向上堆叠 flex 项目***
	- `column` 在竖直方向上堆叠
	- `column-reverse` 竖直，但是是从下到上
	- `row` 水平
	- `row-reverse`
- `flex-wrap` ***规定是否应该对 flex 项目换行***
	- `wrap` 在必要时进行换行
	- `nowrap` 【默认】，不对flex项目换行
	- `wrap-reverse` 在必要时，flex项目将从下到上换行
- `justify-content` ***用于水平对齐flex项目***
	- `center` 将flex项目在flex容器里居中
	- `flex-start` 【默认】
	- `flex-end` 在末端对齐
	- `space-around` 在每个flex项目的两侧都添加空间
	- `space-between` 第一个flex项目的左侧不添加空间，最后一个flex项目的右侧不添加空间，其他都类似 `space-around`
- `align-items` ***用于垂直对齐flex项目***
	- `center`
	- `flex-start`
	- `flex-end`
	- `stretch` 【默认】，拉伸flex项目填充满整个高度
	- `baseline` 根据文本的底部线居中对齐
- `align-content` ***用于不同行之间的flex项目应该如何垂直对齐***
	- `stretch` 【默认】，拉伸每一行以填充满整个高度
	- `space-around` 在有多行时，每一行的上下都添加相同间距
	- `space-between` 在有多行时，第一行的上面无间距，最后一行的下面无间距，其他行平分间距
	- `center` 每一行的无间距的挤到中间
	- `flex-start` 每一行都挤到上面
	- `flex-end` 每一行都挤到下面
## 弹性项目
- `order` 规定flex项目的顺序
- `flex-grow` 规定某个flex项目相对于其余flex项目将增长多少，***默认值为1，0表示不可增长***， https://www.w3school.com.cn/tiy/t.asp?f=css3_flexbox_flex-grow
- `flex-shrink` 规定某个flex项目相对于其余flex项目将收缩多少，***默认值为1，0表示不可收缩***
- `flex-basis` 规定flex项目的初始长度
- `flex` 是 `flex-grow`，`flex-shrink` ， `flex-basis` 的简写
- `align-self` 覆盖容器的`align-items`的对齐方式

```html
/* order */
<div class="flex-container">
	<div style="order: 3">1</div>   /* 虽然在布局中是第一个，但不是flex项目的第一个 */
	<div style="order: 2">2</div>
	<div style="order: 4">3</div> 
	<div style="order: 1">4</div>
</div>

/* flex-grow */
<div class="flex-container">
	<div style="flex-grow: 1">1</div>
	<div style="flex-grow: 1">2</div>
	<div style="flex-grow: 8">3</div> /* 该flex项目增长速度比其他flex项目8倍*/
</div>

/* flex-shrink，flex-basis */
<div class="flex-container">
	<div>1</div>
	<div style="flex-shrink: 3">2</div>   /* 该flex项目比其他flex项目缩小3倍*/
	<div style="flex-basis: 200px">3</div> /* 该flex项目的初始长度为200px */
</div>

/* align-self */
<div class="flex-container">
	<div>1</div>
	<div style="align-self: flex-start">2</div>
	<div style="align-self: flex-end">3</div>
	<div>4</div>
</div>
```

>[!hint] Flexbox 常用于创建响应式布局
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
| :root | root | 选择元素的根元素 |
| ***:not(selector)*** | ***:not(p)*** | ***选择每个非\<p\>元素的元素*** |
| ***:focus*** | ***input:focus*** | ***选择获得焦点的 \<input> 元素*** |
| ***:first-child*** | ***p:first-child*** | ***选择所有\<p\>元素的第一个*** |
| :last-child | p:last-child | 选择所有\<p\>元素的最后一个 |
| :nth-child(n) | div p:nth-child(2) | 选择\<div\>里面的所有\<p\>的第二个 |
| :nth-last-child(n) | p:nth-last-child(2) | 选择所有\<p\>元素的倒数第二个 |
| :only-child | p:only-child | 选择\<p\>同级里没有其他\<p\>的\<p\> |
| :empty | p:empty | 选择没有子元素的 \<p\> 元素 |
| :first-of-type | p:first-of-type | 选择作为其父的首个\<p\>元素的每个\<p\>元素 |
| :last-of-type | p:last-of-type | 选择作为其父的最后一个\<p\>元素的每个 \<p\> 元素 |
| :nth-of-type(n) | p:nth-of-type(2) |  |
| :nth-last-of-type(n) | p:nth-last-of-type(2) |  |
| :only-of-type | p:only-of-type | 选择作为其父的唯一\<p\>元素的每个\<p\>元素 |
| :lang(language) | p:lang(it) | 选择每个 lang 属性值以 "it" 开头的\<p\>元素 |
| :target | \#news\:target | 选择当前活动的 \#news 元素（单击包含该锚名称的 URL） |
| :checked | input:checked | 选择每个被选中的 \<input\> 元素 |
| :disabled | input:disabled | 选择每个被禁用的 \<input\> 元素 |
| :enabled | input:enabled | 选择每个已启用的 \<input> 元素 |
| :in-range | input:in-range | 选择具有指定范围内的值的 \<input> 元素 |
| :valid | input:valid | 选择所有具有有效值的 \<input> 元素 |
| :invalid | input:invalid | 选择所有具有无效值的 \<input> 元素 |
| :optional | input:optional | 选择不带 "required" 属性的 \<input> 元素 |
| :out-of-range | input:out-of-range | 选择值在指定范围之外的 \<input> 元素 |
| :read-only | input:read-only | 选择指定了 "readonly" 属性的 \<input> 元素 |
| :read-write | input:read-write | 选择不带 "readonly" 属性的 \<input> 元素 |
| :required | input:required | 选择指定了 "required" 属性的 \<input> 元素 |

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

- 对符合要求的类的元素
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

# 冲突
>如果有两条或两条以上指向同一元素的冲突CSS规则，则浏览器将遵循一些原则来确定应用哪一条

>[!hint] 冲突规则
> 
> - 以下优先级***由高到低***
> 	- 行内样式 - 行内（内联）样式直接附加到要设置样式的元素
> 		- `<h1 style="color: #ffffff;">`
> 	- ID
> 		- `#navbar`
> 	- 类，属性，伪类
> 		- `.classes`
> 		- `[attributes]` 
> 		- `:hover`
> 	- 元素名、伪元素
> 		- `div`
> 		- `:before`
> - 在优先级相同的情况下，后定义的规则优先级更高
> - 行内样式 > HTML文内`<style>标签` > 外部CSS
> - 通用选择器，被继承的值 ***优先级最低***



























