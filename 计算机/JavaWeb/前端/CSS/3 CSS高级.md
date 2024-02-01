# 图像边框
>`border-image` 接受图像，将其***切成九部分***【井字】，将拐角放置在拐角处，并 <u>重复/拉伸</u> 中间部分

| 属性 | 描述 |
| ---- | ---- |
| [border-image-source](https://www.w3school.com.cn/cssref/pr_border-image-source.asp "CSS border-image-source Property") | 边框图像的路径 |
| [border-image-slice](https://www.w3school.com.cn/cssref/pr_border-image-slice.asp "CSS border-image-slice Property") | 如何裁切边框图像 |
| [border-image-width](https://www.w3school.com.cn/cssref/pr_border-image-width.asp "CSS border-image-width Property") | 边框图像的宽度 |
| [border-image-outset](https://www.w3school.com.cn/cssref/pr_border-image-outset.asp "CSS border-image-outset Property") | 边框图像区域超出边框盒的量 |
| [border-image-repeat](https://www.w3school.com.cn/cssref/pr_border-image-repeat.asp "CSS border-image-repeat Property") | 边框图像应重复、圆角、还是拉伸 |

```html
<head>
	<style>
		span {
			display: inline-block;
			border: 10px solid transparent;
			padding: 2px 8px;
		}
		
		.round20 {
			border-image: url(https://www.w3school.com.cn/i/css/border.png) 20% round;
		}
		
		.round33 {
			border-image: url(https://www.w3school.com.cn/i/css/border.png) 33% round;
		}
		
		.round49 {
			border-image: url(https://www.w3school.com.cn/i/css/border.png) 49% round;
		}
		
		.stretch {
			border-image: url(https://www.w3school.com.cn/i/css/border.png) 30 stretch;
		}
	</style>
</head>

<body>
	<span class="round20">图像的拉伸方式为 round 20%</span>
	<span class="round33">图像的拉伸方式为 round 33%</span>
	<span class="round49">图像的拉伸方式为 round 49%</span>
	<span class="stretch">图像的拉伸方式为 stretch</span>
</body>
```

# 渐变
## 线性渐变
>`linear-gradient` 向下 / 向上 / 向左 / 向右 / 对角线

语法：`background-image: linear-gradient(direction/angle, color-stop1, color-stop2, ...);`

```css
/* 从上到下，红色到黄色的渐变 */
background-image: linear-gradient(red, yellow);
background-image: linear-gradient(red, yellow, green);

/* 从左到右 */
background-image: linear-gradient(to right, red , yellow);

/* 左上角到右下角 */
background-image: linear-gradient(to bottom right, red, yellow);

/* 0deg 向上，90deg 向右，180deg 向下 */
background-image: linear-gradient(2700deg, red, yellow);

/* 重复线性渐变，渐变的起始颜色为红色，在距离起始位置10%的地方，渐变到黄色，在距离起始位置50%的地方，渐变到绿色 */
background-image: repeating-linear-gradient(red, yellow 10%, green 50%);
```

## 径向渐变
>由中心向外扩散

语法：`background-image: radial-gradient(shape, start-color, ..., last-color);`

```css
/* 中心为red，向外扩散 */
background-image: radial-gradient(red, yellow, green);

/* 中心red占据5% */
background-image: radial-gradient(red 5%, yellow 15%, green 60%);

/* shape为椭圆或者圆 */
background-image: radial-gradient(circle, red, yellow, green);    /* 圆 */
background-image: radial-gradient(ellipse, red, yellow, green);    /* 默认为椭圆 */

/* 重复径向渐变 */
background-image: repeating-radial-gradient(red, yellow 10%, green 15%);
```

# 阴影
- `text-shadow` 文本阴影
- `box-shadow` 元素阴影

```css
/* 水平阴影 2px，垂直阴影 2px */
h1 {
	text-shadow: 2px 2px;
}

/* 阴影的颜色 */
text-shadow: 2px 2px red;

/* 阴影的模糊扩散效果 */
text-shadow: 2px 2px 5px red;

/* 多个阴影用逗号分隔 */
text-shadow: 0 0 3px #FF0000, 0 0 5px #0000FF;
```

>[!hint] 阴影可以制造出围绕文本的效果
>上下左右都偏移出阴影
> ```css
> text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
> ```
<p style="color: yellow; font-size: 30px; text-align: center; text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;">围绕</p>

# 文本效果
- `text-overflow` <u>未显示出的溢出</u>【`overflow: hidden;`】的呈现方式

```css
p.test1 {
	white-space: nowrap;    /* 表示不换行 */
	overflow: hidden;
	width: 200px; 
	border: 1px solid #000000;

	text-overflow: clip;     /* 被裁剪 */
	text-overflow: ellipsis;       /* 呈现为省略号... */
}
```
![[Excalidraw/计算机/JavaWeb Draw.md#^group=wsbAlVNe|300]]

---
- `word-wrap` 是否允许长单词换行

```css
p.test {
	width: 11em; 
	border: 1px solid #000000;
	word-wrap: break-word;   /* 强制换行 */
}
```
![[Excalidraw/计算机/JavaWeb Draw.md#^group=38Wunzyo|440]]

---
- `word-break` 指定换行规则

```css
p.test1 {
	word-break: keep-all;    /* 以单词为单位打断 */
}

p.test2 {
	word-break: break-all;    /* 以字符为单位打断 */
}
```
![[Excalidraw/计算机/JavaWeb Draw.md#^group=PrpPRQ2b]]

---
- `writing-mode` 文本行放置是 <u>水平/垂直</u>

```css
/* 水平放置 */
writing-mode: horizontal-tb;

/* 竖直放置 */
writing-mode: vertical-rl;
```

# 空间移动
## 2D
>使用 `transform` 属性下的各种方法实现，可以使用 `transform-origin` 调整位置

- `translate()` 从其当前位置移动元素
- `rotate()` 根据角度旋转元素
- `scale()` <u>增加/减少</u>元素的大小
- `skew()` 使元素沿 X 和 Y 轴倾斜给定角度

```css
div {
/* 把<div>元素向右移动 50 个像素，向下移动 100 个像素 */
transform: translate(50px, 100px);

/* 以中心点顺时针旋转 20 度 */
transform: rotate(20deg);

/* 把<div>元素的宽度的增大两倍，原始高度增大三倍 */
transform: scale(2, 3);

/* 沿X轴倾斜 20度 */
transform: skew(20deg,0deg); 
/* 沿Y轴倾斜 20度 */
transform: skew(0deg,20deg); 
```

![[Excalidraw/计算机/JavaWeb Draw.md#^group=YnDnv7xz|330]]

## 3D
|所有属性 |描述|
|---|---|
|[transform](https://www.w3school.com.cn/cssref/pr_transform.asp "CSS3 transform 属性")|向元素应用 2D 或 3D 转换 |
|[transform-origin](https://www.w3school.com.cn/cssref/pr_transform-origin.asp "CSS3 transform-origin 属性")|允许你改变被转换元素的位置 |
|[transform-style](https://www.w3school.com.cn/cssref/pr_transform-style.asp "CSS3 transform-style 属性")|规定被嵌套元素如何在 3D 空间中显示 |
|[perspective](https://www.w3school.com.cn/cssref/pr_perspective.asp "CSS3 perspective 属性")|规定 3D 元素的透视效果 |
|[perspective-origin](https://www.w3school.com.cn/cssref/pr_perspective-origin.asp "CSS3 perspective-origin 属性")|规定 3D 元素的底部位置 |
|[backface-visibility](https://www.w3school.com.cn/cssref/pr_backface-visibility.asp "CSS3 backface-visibility 属性")|定义元素在不面对屏幕时是否可见 |

| transform的函数 | 描述 |
| ---- | ---- |
| translate3d(_x_,y,z) | 定义 3D 转化 |
| scale3d(x,y,z) | 定义 3D 缩放转换 |
| rotate3d(x,y,z,angle) | 以3D方式旋转 |
| perspective(n) | 定义 3D 转换元素的透视视图 |
```css
/* 看不到了 */
transform: rotate3d(150deg, 0, 0);
/* 就是顺时针转了90度 */
transform: rotate3d(0deg, 0, 90deg);
```

# 过渡
- `transition` 指定需要过渡效果的属性，过渡时间
- `transition-delay` 延迟
- `transition-timing-function` 过渡效果的速度曲线
	- `ease`  【默认】慢-快-慢
	- `linear`  匀速
	- `ease-in` 慢开始
	- `ease-out`  慢结束
	- `ease-in-out`  慢开始-慢结束
	- `cubic-bezier(n,n,n,n)`  在三次贝塞尔函数中定义自己的值

```css
div {
	width: 100px;
	height: 100px;
	background: red;
	transition: width 2s;     /* 指定需要添加过渡效果的属性为width，过渡时间为2s */
	transition-delay: 1s;     /* 悬浮后会等待1s */
	transition-timing-function: linear;
}

div:hover {
	width: 300px;    /* 悬浮时会增加宽度 */
}
```

```css
/* 过渡+转换 */
div {
	width: 100px;
	height: 100px;
	background: red;
	transition: width 2s, height 2s, transform 2s, background 2s;
}

div:hover {
	width: 300px;
	height: 300px;
	background: black;
	transform: rotate(180deg);
}
```

# 动画
>动画使元素逐渐从一种样式变为另一种样式，***而不使用 JavaScript 或 Flash***
>
>- 编写动画代码
>- 将动画代码绑定到需要产生效果的元素上


- `@keyframes`
	- 使用`from to`
	- 使用百分比
- `animation-name` 用于元素指定动画名
- `animation-duration` 动画持续时间
- `animation-delay` 动画延迟时间
- `animation-iteration-count` 动画运行的次数
	- `infinite` 表示永远运行下去
- `animation-direction`
	- `normal` 【默认】动画正常播放（0%-100%）
	- `reverse` 动画以反方向播放（100%-0%）
	- `alternate` 动画先向前播放，然后向后
	- `alternate-reverse` 动画先向后播放，然后向前
- `animation-timing-function` 动画速度曲线
	- `ease`  【默认】慢-快-极慢
	- `linear`  匀速
	- `ease-in` 慢开始
	- `ease-out`  慢结束
	- `ease-in-out`  慢开始-慢结束
	- `cubic-bezier(n,n,n,n)`  在三次贝塞尔函数中定义自己的值
- `animation-fill-mode`
	- `none` 【默认】动画执行之后保持原样
	- `forwards` 元素会保留动画执行之后最后一个关键帧的样式值
	- `backwards` 在动画延迟期间元素将应用第一个关键帧的样式值
	- `both` 结合了`forward` + `backwards`

```css
/* 动画代码 */
@keyframes example {     /* 定义动画名 */
	from {background-color: red;}
	to {background-color: yellow;}
-------------------------------------------------
	0%   {background-color:red; left:0px; top:0px;}
	25%  {background-color:yellow; left:200px; top:0px;}
	50%  {background-color:blue; left:200px; top:200px;}
	75%  {background-color:green; left:0px; top:200px;}
	100% {background-color:red; left:0px; top:0px;}
}

div {
	width: 100px;
	height: 100px;
	background-color: red;
	animation-name: example;    /* 将对应的动画名绑定到该元素 */
	animation-duration: 4s;          /* 指定动画持续时间 */
	animation-iteration-count: 3;   /* 动画运行3次 */
}
```

>[!hint] 过渡 和 动画
>过渡 是从一个状态过渡到另一个状态，而不是连续的动画
>动画 用于创建更复杂的效果【播放次数，动画方向】

# 提示
>提示 通常用于***提供某内容的额外信息***
>![[Excalidraw/计算机/JavaWeb Draw.md#^group=MOa3PP06|200]]

>[!hint] 提示的思路
>- 在<u>父元素</u>里包含<u>提示元素</u>
>	- 一般将父元素设置为`position: relative;` ，<u>提示元素</u>设置为`position: absolute;`
>	- <u>提示元素</u>的层级一般高于<u>父元素</u>【`z-index: 1;`】
>- 将<u>提示元素</u>设置为隐藏 `display: none;`
>- 悬浮<u>父元素</u>时，将<u>提示元素</u>设置为显示 `display: inline-block;`

## 提示框的位置
>提示框的位置可以上下左右

```css
/* 上------------------------------------------------- */
.tooltip .tooltiptext {
	width: 120px;
	bottom: 100%;       /* 底部有100%空间，说明位置到顶了 */
	left: 50%;            /* 左侧留有50%，让提示框的左侧居中 */
	margin-left: -60px;   /* 根据宽度再向左移动60px，是的文本框的中心与父元素居中 */
}

/* 下------------------------------------------------- */
.tooltip .tooltiptext {
	width: 120px;
	top: 100%;
	left: 50%;
	margin-left: -60px;
}

/* 左------------------------------------------------- */
.tooltip .tooltiptext {
	top: -5px;   /* 平衡内边距 */
	right: 100%; 
}

/* 右------------------------------------------------- */
.tooltip .tooltiptext {
	top: -5px;
	left: 100%; 
}
```

## 提示框箭头
>边框的上下左右其中***只有一边有颜色，并且没有内容，就会变成一个箭头***

```css
.tooltip .tooltiptext {
	……
}

.tooltip .tooltiptext::after {    /* 添加一个伪元素 */
	content: "";       /* 指定内容为空 */
	position: absolute;
	top: 100%;       
	left: 50%;
	margin-left: -5px;
	border-width: 5px;
	border-style: solid;
	border-color: black transparent transparent transparent;   /* 只有上边框有颜色 */
}
```

# 图像视频容器
>`object-fit`指定应如何调整 \<img\> 或 \<video\> 的大小以适合其容器

>[!hint] 属性值
> - `fill` 【默认】如有必要，将拉伸或挤压物体以适应该对象
> - `contain` 保持宽高比，不会剪裁。将图像的width缩放至恰好适合容器
> - `cover` 保证图像不会变形，***但是会裁剪并填满***【即使窗口大小发生变化】
> - `none` 不会变形，会裁切。不对内容进行任何操作，图像将按照其原始尺寸显示在原始容器，多的裁切，少的也不填充
> - `scale-down` 保持宽高比，不会剪裁。如果图像的尺寸>容器的尺寸，就为`cover` ；如果图像尺寸<容器尺寸，则按原尺寸显示，不会放大图像

实例： https://www.w3school.com.cn/tiy/t.asp?f=css3_object-fit_all
# 按钮
>[!hint] 设置按钮的基本原则
>- 悬停时出现<u>字体颜色</u>与<u>背景颜色</u>的反转
>- 悬停时出现<u>同色系的阴影效果</u>/<u>黑白灰色系的阴影效果</u>
>- 禁用某个按钮时，***降低***`opacity`透明度
>- 点击时，出现涟漪效果
>- 点击时，出现按钮被按下的效果

```css
/* 对于涟漪效果的解析 */
.button:after {
	content: "";
	background: #f1f1f1;
	display: block;
	position: absolute;
	padding-top: 300%;
	padding-left: 350%;
	margin-left: -20px !important;
	margin-top: -120%;
	opacity: 0;
	transition: all 0.8s  /* 点击操作完成后，那就会以0.8s回到原始状态 */
}               /* ::after会慢慢变大，但是会越来越透明 */

.button:active:after {
	padding: 0;
	margin: 0;
	opacity: 1;
	transition: 0s   /* 按钮被点击，会以0s将::after伪元素设置为一个不透明的看不见的点 */
}     /* ::after在button的后面，所以点击后，::after会出现在button的左下角 */
```

```css
.button {
	display: inline-block;
	padding: 15px 25px;
	font-size: 24px;
	cursor: pointer;
	text-align: center;
	text-decoration: none;
	outline: none;
	color: #fff;
	background-color: #4CAF50;
	border: none;
	border-radius: 15px;
	box-shadow: 0 9px #999;    /* 先设置一个长的阴影 */
}

.button:active {
	background-color: #3e8e41;
	transform: translateY(4px);      /* 被点击时，按钮向下移动Y */
	box-shadow: 0 5px #666;   /* 阴影相应减少Y */
}
```
# 导航，分页
>- 使用`<div>`中包含`<a>`
>- 使用`<ul>`无序列表
## 分页
```css
<div class="pagination">
	<a href="#">«</a>
	<a href="#">1</a>
	<a class="active" href="#">2</a>
	<a href="#">3</a>
	<a href="#">»</a>
</div>
```
<div class="pagination">
	<a href="#">«</a>
	<a href="#">1</a>
	<a class="active" href="#">2</a>
	<a href="#">3</a>
	<a href="#">4</a>
	<a href="#">5</a>
	<a href="#">6</a>
	<a href="#">»</a>
</div>

## 面包屑导航
```css
ul.breadcrumb {
	padding: 8px 16px;
	list-style: none;
	background-color: #eee;
}

ul.breadcrumb li {display: inline;}

ul.breadcrumb li+li:before {
	padding: 8px;
	color: black;
	content: "/\00a0";
}

/* html */
<ul class="breadcrumb">
	<li><a href="#">Home</a></li>
	<li><a href="#">Pictures</a></li>
	<li><a href="#">Summer 15</a></li>
	<li>Italy</li>
</ul>
```
# 多列
- `column-count` 规定元素应被划分的列数
- `column-gap` 规定列之间的间隔大小
- `column-rule` ***类比为border***
	- `column-rule-style` 规定列之间的分隔样式
	- `column-rule-width` 规定列之间的分隔样式的宽度
	- `column-rule-color` 规定列之间的分隔样式的颜色
- `column-span` 规定元素应跨越多少列，<u>属性值为阿拉伯数字</u>
![[Excalidraw/计算机/JavaWeb Draw.md#^group=ePvyGHSk|900]]
- `column-width` 为每一列指定最佳宽度
```css
div {
	column-count: 3;   /* div将被划分为3列 */
	column-gap: 40px;
	column-rule: 1px solid lightblue;
	column-width: 100px;
}

h2 {
	column-span: all;
}

/* html */
<div class="newspaper">
<h2>第一回 宴桃园豪杰三结义 斩黄巾英雄首立功</h2>
…………………………………………
</div>
```

# 响应式
## 自由调整大小
>`resize` 规定元素应如何被用户调整大小
>![[Excalidraw/计算机/JavaWeb Draw.md#^group=L6YLgDod]]

```css
resize: horizontal;   /* 只允许用户调整宽度 */
resize: vertical;    /* 只允许用户调整高度 */
resize: both;     /* 允许用户调整 高度 和 宽度 */
resize: none;    /* 禁止用户调整 */
```
## 媒体查询
>[!hint] 媒体查询可用于检查
> - 视口的宽度和高度
> - 设备的宽度和高度
> - 方向【平板电脑/手机处于<u>横向/纵向模式</u>】
> - 分辨率

```css
/* 语法 */
@media not|only mediatype and (expressions) {
	……
}

/* 例子 */
/* 在视口宽度为480px以及更宽时，将背景颜色更改为浅绿色 */
@media screen and (min-width: 480px) {
	body {
		background-color: lightgreen;
	}
}
```
- `mediatype`
	- `all` 所有媒体类型设备
	- `print` 打印机
	- `screen` 计算机屏幕、平板电脑、智能手机等等
	- `speech` 大声“读出”页面的屏幕阅读器
- `expressions` 表达式的值可以为<u>true</u> / <u>false</u>
## 例子
- 响应式菜单
```css
#leftsidebar {
	float: none;   /* 窗口小时菜单占一行 */
	width: auto;
}
……

/* 窗口大时，将菜单左侧浮动 */
@media screen and (min-width: 480px) { 
	#leftsidebar {width: 200px; float: left;}
}

/* html */
<div class="wrapper">
	<div id="leftsidebar">
		<ul id="menulist">
			<li class="menuitem">Menu-item 1</li>
			<li class="menuitem">Menu-item 2</li>
			<li class="menuitem">Menu-item 3</li>
			<li class="menuitem">Menu-item 4</li>
			<li class="menuitem">Menu-item 5</li>
		</ul>
	</div>
  
	<div id="main">
		<h1>请调整浏览器窗口大小来查看效果！</h1>
		<p>本例显示了一个菜单，如果视口为 480 像素或更宽，它将向页面左侧浮动。如果视口小于 480 像素，则菜单将位于内容的顶部。</p>
	</div>
</div>
```






# CSS 变量
> `var(name, [value])`，`name` 必须以两个破折号“--”开头，且区分大小写
> 
>***CSS 变量可以访问 DOM，所以可以使用 JavaScript 来修改变量，以及基于媒体查询来修改变量***

- 创建具有全局作用域的变量，在 `:root选择器` 中声明
- 创建具有局部作用域的变量，在<u>将要使用它的选择器</u>中声明它

```css
:root {
	--blue: #1e90ff;
	--white: #ffffff;
}

body {
	--white: #fffff0;    /* 重新声明覆盖全局变量 */
	background-color: var(--blue); 
}
```

>[!hint] 变量在媒体查询时用的很多
# 问题
```html
<div>
  <h2>Title</h2>
</div>
<div>
  <h3>Subtitle</h3>
</div>

如何选择到 有包含h2标签的div元素 后的有包含h3标签的div元素的h3标签呢

好像css不支持选择某个标签的父标签
```


---
可学习的网站：
https://toyou.club/






















