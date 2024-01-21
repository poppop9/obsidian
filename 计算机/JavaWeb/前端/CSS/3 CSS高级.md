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
| 函数 | 描述 |
| ---- | ---- |
| translate3d(_x_,y,z) | 定义 3D 转化 |
| scale3d(x,y,z) | 定义 3D 缩放转换 |
| rotate3d(x,y,z,angle) | 定义 3D 旋转 |
| perspective(n) | 定义 3D 转换元素的透视视图 |












