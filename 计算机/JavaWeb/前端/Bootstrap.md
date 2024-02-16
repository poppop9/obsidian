>[!hint] Bootstrap 可以轻松地创建响应式设计，而且提供了丰富的 JavaScript 插件

>[!hint] Bootstrap的核心是***移动优先***，所以为一个较小的视口设置了样式，这个样式会在所有更大的视口中继续适用，除非对更大视口的添加新的样式

# 引入
## CDN
https://v5.bootcss.com/docs/getting-started/introduction/#quick-start

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css">
</head>

<body>
……
</body>

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js"></script>

</html>
```
## npm
https://v5.bootcss.com/docs/getting-started/download/#npm

`npm install bootstrap@5.3.0-alpha1`

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
- `.d-grid` 让其子元素铺满父元素
	- `.gap-数字` 控制子元素之间的间距 
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
# 组件
## 警告框
>在 `class属性` 上添加 `alert`

- 样式
	- `.alert-success`
	- `.alert-info`
	- `.alert-warning`
	- `.alert-danger`
	- `.alert-primary`
	- `.alert-secondary`
	- `.alert-light`
	- `.alert-dark`
- 关闭警告框按钮
	- `.alert-dismissible`
	- `.btn-close`
	- `data-bs-dismiss`
```html
<div class="alert alert-success alert-dismissible">
	<strong>成功！</strong>此警报框表示成功或积极的动作
	<button type="button" class="btn-close" data-bs-dismiss="alert"></button>
</div>
```

## 按钮
>在 `class属性` 上添加 `btn`

### 样式
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402161545012.png)
```html
<button type="button" class="btn">基础</button>
<button type="button" class="btn btn-primary">主要</button>
<button type="button" class="btn btn-secondary">次要</button>
<button type="button" class="btn btn-success">成功</button>
<button type="button" class="btn btn-info">信息</button>
<button type="button" class="btn btn-warning">警告</button>
<button type="button" class="btn btn-danger">危险</button>
<button type="button" class="btn btn-dark">深色</button>
<button type="button" class="btn btn-light">浅色</button>
<button type="button" class="btn btn-link">链接</button>
```

---
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402161554945.png)
```html
<button type="button" class="btn btn-outline-primary">主要</button>
……
```
### 尺寸
```html
<button type="button" class="btn btn-primary btn-lg">大型</button>
<button type="button" class="btn btn-primary">默认</button>
<button type="button" class="btn btn-primary btn-sm">小型</button>
```
### 禁用
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402161619053.png)
- `.active` 活跃
- `disabled` 禁用

```html
<button type="button" class="btn btn-primary">主要按钮</button>
<button type="button" class="btn btn-primary active">活动的主要按钮</button>
<button type="button" class="btn btn-primary" disabled>禁用的主要按钮</button>
```
### xaing'yign

- 杂
	- `.text-nowrap` 按钮内的文字不换行










