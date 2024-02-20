# 组件
## 卡片
>卡片是一种灵活且可扩展的内容容器

- `.card` 父容器卡片元素
- `.card-header` 卡片页眉
- `.card-body` 卡片主体
- `.card-footer` 卡片页脚
- `.card-text` ***用于去除页眉，主题，页脚内最后一个子元素的底边距***


---
- ***全宽图片卡片***
```html
<div class="card" style="width:400px">
	<!-- img在card-body的外面 -->
	<img class="card-img-top" src="https://img0.baidu.com/it/u=3505745567,4189381360&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500" style="width:100%">
	<div class="card-body">
		<h4 class="card-title">Bill Gates</h4>
		<p class="card-text">Bill Gates 是一位程序员和工程师。一些示例文本。一些示例文本。</p>
		<a href="#" class="btn btn-primary">查看个人资料</a>
	</div>
</div>
```

- ***外边距图片卡片***
```html
<div class="card" style="width:400px">
	<div class="card-body">
		<!-- img在card-body的里面 -->
		<img class="card-img-top" src="https://img0.baidu.com/it/u=3505745567,4189381360&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500" style="width:100%">
		<h4 class="card-title">Bill Gates</h4>
		<p class="card-text">Bill Gates 是一位程序员和工程师。一些示例文本。一些示例文本。</p>
		<a href="#" class="btn btn-primary">查看个人资料</a>
	</div>
</div>
```

- ***导航卡片***
```html
<div class="card text-center">
  <div class="card-header">
    <ul class="nav nav-tabs card-header-tabs">
      <li class="nav-item">
		<button type="button" class="nav-link btn">Active</button>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Link</a>
      </li>
      <li class="nav-item">
        <a class="nav-link disabled">Disabled</a>
      </li>
    </ul>
  </div>
  <!-- 内容 -->
  <div class="card-body">
    <p class="card-text">内容</p>
  </div>
</div>
```

- ***水平卡片***
```html
<div class="card">
	<div class="row">
		<div class="col-md-4">
			<img src="https://img0.baidu.com/it/u=3505745567,4189381360&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500"
				class="img-fluid">
		</div>
		<div class="col-md-8">
			<div class="card-body">
				<p class="card-text">Last updated 3 mins ago</p>
			</div>
		</div>
	</div>
</div>
```

### 卡片组
>使用 `.card-group` 包含多个 `card`
>![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402182338798.png)


```html
```html
<div class="card-group">
  <div class="card">
    <img src="..." class="card-img-top" alt="...">
    <div class="card-body">
      <h5 class="card-title">Card title</h5>
      <p class="card-text">This is a wider card</p>
      <p class="card-text">Last updated 3 mins ago</p>
    </div>
  </div>
  <div class="card">
    <img src="..." class="card-img-top" alt="...">
    <div class="card-body">
      <h5 class="card-title">Card title</h5>
      <p class="card-text">This card</p>
      <p class="card-text">Last updated 3 mins ago</p>
    </div>
  </div>
  <div class="card">
    <img src="..." class="card-img-top" alt="...">
    <div class="card-body">
      <p class="card-text">This is a wider card</p>
    </div>
  </div>
</div>
```

### 网格卡
>使用 `.row-cols-*` 控制一行要显示多少列
>![200](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402182347837.png)

```html
<!-- 正常一行显示1列，当屏幕超过middle时，一行2列 -->
<div class="row row-cols-1 row-cols-md-2 g-4">
  <div class="col">
    <div class="card">
      <img src="..." class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">Card title</h5>
        <p class="card-text">This is</p>
      </div>
    </div>
  </div>
  <div class="col">
    <div class="card">
      <img src="..." class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">Card title</h5>
        <p class="card-text">This is</p>
      </div>
    </div>
  </div>
  <div class="col">
    <div class="card">
      <img src="..." class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">Card title</h5>
        <p class="card-text">This is</p>
      </div>
    </div>
  </div>
  <div class="col">
    <div class="card">
      <img src="..." class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">Card title</h5>
        <p class="card-text">This is</p>
      </div>
    </div>
  </div>
</div>
```

### 砌筑
>由于有副作用，BootStrap不直接支持，可以使用插件 [Masonry](https://masonry.desandro.com/)，这是[例子](https://v5.bootcss.com/docs/examples/masonry/)

## 下拉菜单
- `.dropdown` 用于下拉列表父元素
	- 在 `<button>` 上放置 `.dropdown-toggle` ***显示下箭头logo***
	- 在 `<button>` 上放置 `data-bs-toggle="dropdown"` ***指定了按钮的点击行为，点击时，它将触发下拉菜单的显示或隐藏***
	- `.dropdown-menu` 下拉列表菜单
		- `.dropdown-item` 下拉列表子项目
		- `.dropdown-divider` 分割线

```html
<div class="dropdown">
	<button class="btn dropdown-toggle" type="button" data-bs-toggle="dropdown">
	Dropdown button
	</button>
	<ul class="dropdown-menu">
		<li><a class="dropdown-item" href="#">Action</a></li>
		<li><a class="dropdown-item" href="#">Another action</a></li>
		<li><hr class="dropdown-divider"></li>
		<li><a class="dropdown-item" href="#">Something else here</a></li>
	</ul>
</div>
```













