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
# 分割线
- `.vr` 竖直的分割线【~~对标 `<hr>`~~】

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

# Display
- `d-none` 隐藏元素，在任何屏幕尺寸下都不可见
- `d-md-block` 中等屏幕尺寸及以上时显示元素，而在较小的屏幕尺寸下隐藏元素
- `d-md-flex` display-middle-flex，表示***当屏幕宽度达到中等及以上时，设置弹性容器***

# Position
- `.mx-auto` 相当于 `margin-left: auto; margin-right: auto;`
---
- `.fixed-top` 相对于视口将元素定位在顶上
- `.fixed-bottom` 相对于视口将元素定位在底部
- `.sticky-top` 根据用户滚动位置，将元素定位在顶上
	- `sticky-sm-top` 当视口是 sm 或更宽尺寸时，黏着在视口的顶部
- `.sticky-bottom`

# Float
- `.float-start` 使元素向左浮动
- `.float-end` 使元素向右浮动
	- `float-sm-end` 在小型屏幕或更宽的屏幕上向右浮动

# Flexbox
- `.d-flex` 设置弹性容器
	- `.d-md-flex`
	- ……

![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403162112918.png)
- `d-inline-flex` 创建行内弹性容器【~~内容多少占多少~~】
![300](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403162112488.png)
---

- **方向**
	- `.flex-column` 让其子元素垂直排列
	- `.flex-column-reverse` 让其子元素反向垂直排列
	- `.flex-row` 让其子元素水平排列
	- `.flex-row` 让其子元素反向水平排列

---

- **对齐**
	- 水平对齐
		- `justify-content-center` 子元素水平居中
		- `justify-content-md-end` 在中等以上屏幕宽度时将子元素水平右对齐
		- `justify-content-around` 在每个 flex 子项目的两侧都添加空间
		- `justify-content-between` 第一个 flex 子项目的左侧不添加空间，最后一个 flex 子项目的右侧不添加空间，其他都类似 `around`
	- 自我水平对齐
		- `ms-auto` 让元素居右对齐
		- `me-auto` 让元素居左对齐
	- 单行时的垂直对齐
		- `.align-items-start`
		- `.align-items-end`
		- `.align-items-center`
		- `.align-items-baseline`
		- `.align-items-stretch`【默认】
	- 多行时的垂直对齐
		- `.align-content-end` 堆叠到下面
		- `.align-content-center` 堆叠到中间
		- `.align-content-between` 平均堆叠，上下无空间
		- `.align-content-around` 平均堆叠，上下有空间
		- `.align-content-stretch` 拉伸平均堆叠满父容器
	- 自我垂直对齐【**用于 flex 子项目，会覆盖父容器的垂直对齐**】
		- `.align-self-start`
		- `.align-self-end`
		- `.align-self-center`
		- `.align-self-baseline`
		- `.align-self-stretch`【默认】
		- `mt-auto` 让元素居下
		- `mb-auto` 让元素居上

```html
<div class="d-flex">
	<div class="p-2 bg-info">弹性项目 1</div>
	<div class="p-2 bg-warning ms-auto">弹性项目 2</div>
	<div class="p-2 bg-primary">弹性项目 3</div>
</div>
```
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403162149327.png)

---

- **占比**
	- `.flex-fill` 强制拉伸能拉伸到的最大宽度

```html
<div class="d-flex">
	<div class="p-2 bg-info flex-fill">弹性项目 1</div>
	<div class="p-2 bg-warning flex-fill">弹性项目 2</div>
	<div class="p-2 bg-primary flex-fill">弹性项目 3</div>
</div>
```

---

- **换行**【默认不换行】
	- `.flex-wrap` 对 flex 子项目进行换行

---


