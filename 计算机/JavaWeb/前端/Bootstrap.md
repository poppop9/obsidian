>[!hint] Bootstrap 可以轻松地创建响应式设计，而且提供了丰富的 JavaScript 插件

>[!hint] Bootstrap的核心是***移动优先***，所以为一个较小的视口设置了样式，这个样式会在所有更大的视口中继续适用，除非对更大视口的添加新的样式

# 布局
## 容器
![800](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402051731979.png)
### .container 固定宽度容器
>提供了一个响应式的***固定宽度容器***【`max-width`会在不同的屏幕尺寸变化】

| 类 | Extra small  <br><576px | Small  <br>≥576px | Medium  <br>≥768px | Large  <br>≥992px | Extra large  <br>≥1200px | XXL  <br>≥1400px |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| `.container` | 100% | 540px | 720px | 960px | 1140px | 1320px |
| `.container-md` | 100% | 100% | 720px | 960px | 1140px | 1320px |
| `.container-lg` | 100% | 100% | 100% | 960px | 1140px | 1320px |
| `.container-xl` | 100% | 100% | 100% | 100% | 1140px | 1320px |
| `.container-xxl` | 100% | 100% | 100% | 100% | 100% | 1320px |
### .container-fluid 全宽容器
>提供了一个***全宽容器***【`width` 总是 `100%`】
## 网格布局
>利用 `flexbox` ，共有12列【会根据屏幕大小，自动重排】
>![800](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402051753353.png)

网格系统有六个类：
- `.col-` (超小型设备 - 屏幕宽度小于 576px)
- `.col-sm-` (小型设备 - 屏幕宽度等于或大于 576px)
- `.col-md-` (中型设备 - 屏幕宽度等于或大于 768 像素)
- `.col-lg-` (大型设备 - 屏幕宽度等于或大于 992 像素)
- `.col-xl-` (xlarge 设备 - 屏幕宽度等于或大于 1200px)
- `.col-xxl-` (xxlarge 设备 - 屏幕宽度等于或大于 1400px)

### 自定义列宽
```html
/* 第一颗星 (*) 代表响应度：sm、md、lg、xl 或 xxl */
/* 第二颗星代表占用列数，所有列加起来不超过12 */
<div class="row">
	<div class="col-*-*"></div>
	<div class="col-*-*"></div>
	<div class="col-*-*"></div>
</div>
------

/* 当屏幕小于576px时，每一列会占据宽度的100%，并向下堆叠 */
<div class="row">
	<div class="col-sm-4">.col-sm-4</div>
	<div class="col-sm-4">.col-sm-4</div>
	<div class="col-sm-4">.col-sm-4</div>
</div>
```

### 自动均分列宽
```html
/* 有三个col，所以每列会占用33.3% */
<div class="row">
	<div class="col"></div>
	<div class="col"></div>
	<div class="col"></div>
</div>
```
## 排版
- `font-size` ：1rem
- `line-height` ：1.5
- `<p>` ：`margin-top: 0` ，`margin-bottom: 1rem` 
- `<h1>~<h6>` ：更粗的 `font-weight`，响应式的 `font-size`
- `<table>` 
	- `.table-responsive` 需要时向表格添加滚动条
- `<img>`
	- `.float-start` 图片左对齐
	- `.float-end` 图片右对齐
	- `.mx-auto` + `.d-block` 图片居中
	- `.img-fluid` 响应式图像


















