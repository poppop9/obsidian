# 颜色
>BootStrap 用8种颜色表示了文字的重要性

- `primary` 重要蓝
- `secondary` 次要灰
- `success` 成功绿
- `info` 信息青
- `warning` 警告黄
- `danger` 危险红
- `dark` 深色
- `light` 浅色

---
- 文本色
	- `.text-primary`
	- `.text-danger`
	- ……
- 背景色
	- `.bg-primary`
	- `.bg-danger`
	- ……
- 文本背景对比色：***用于设置背景色，并且把文本色设置成背景色的对比色【黑/白】***
	- `.text-bg-primary`
	- `.text-bg-danger`
	- ……
- 链接色【**可以有 `:hover`，`:focus` 效果**】
	- `.link-*`
- 边框色
	- `.border-primary`
	- ……

# 文本
| 类                       | 描述        |
| ----------------------- | --------- |
| `.text-left`            | 左对齐文本     |
| `.text-center`          | 居中对齐的文本   |
| `.text-end`             | 右对齐文本     |
| `.text-break`           | 防止长文本破坏布局 |
| `.text-decoration-none` | 删除链接中的下划线 |
| `.text-nowrap`          | 文本不换行     |

# 表格，图片
- `<table>` 
	- `.table-responsive` 需要时向表格添加滚动条
- `<img>`
	- `.float-start` 图片左对齐
	- `.float-end` 图片右对齐
	- `.mx-auto` + `.d-block` 图片居中
	- `.img-fluid` 响应式图像

# 纵横比
>根据父容器的宽度，响应式处理子容器的视频或幻灯片
>![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403161650391.png)

- `ratio` 设置 ratio 父容器
- `ratio-1x1` 父容器的比率为 1:1，子容器会响应式的适应父容器
- `ratio-4x3`
- `ratio-16x9`
- `ratio-21x9`

```html
<div class="ratio ratio-1x1">
	<iframe src="//player.bilibili.com/player.html?aid=1951552392&bvid=BV12C411a7eV&cid=1468271866&p=1"
		scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>
```

# display
- `d-none` 隐藏元素，在任何屏幕尺寸下都不可见
- `d-md-block` 中等屏幕尺寸及以上时显示元素，而在较小的屏幕尺寸下隐藏元素
- `d-md-flex` display-middle-flex，表示***当屏幕宽度达到中等及以上时，设置弹性容器***

# position
- `.mx-auto` 相当于 `margin-left: auto; margin-right: auto;`
---
- `.fixed-top` 相对于视口将元素定位在顶上
- `.fixed-bottom` 相对于视口将元素定位在底部
- `.sticky-top` 根据用户滚动位置，将元素定位在顶上
	- `sticky-sm-top` 当视口是 sm 或更宽尺寸时，黏着在视口的顶部
- `.sticky-bottom`

# float
- `.float-start` 使元素向左浮动
- `.float-end` 使元素向右浮动
	- `float-sm-end` 在小型屏幕或更宽的屏幕上向右浮动


# Flexbox
- `.flex-column` 让其子元素垂直排列
- `.flex-row` 让其子元素水平排列
- `justify-content-center` 子元素水平居中
- `justify-content-md-end` 在中等以上屏幕宽度时将子元素水平右对齐
- `justify-content-between` 让子元素分布在容器的左右两端
- `align-items-center` 让子元素垂直居中于父元素
- `align-self-center` 自己居中于父元素

```html
<!-- 实现了按钮堆叠右对齐 -->
<div class="gap-2 d-md-flex justify-content-md-end">
	<button class="btn btn-primary" type="button">第一</button>
	<button class="btn btn-primary" type="button">第二</button>
</div>
```

# 杂
## 全宽响应式
- `.gap-数字` 规定子元素之间的间隔

