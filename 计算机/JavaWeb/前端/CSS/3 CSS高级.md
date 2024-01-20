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

/* 重复线性渐变 */

```



## 径向渐变
>由中心向外扩散



































