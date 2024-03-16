# 深色模式
在容器添加 `data-bs-theme="dark"`

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

---

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

---

- ***导航卡片***
![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403152236751.png)
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

---

- ***水平卡片***
![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403152242833.png)
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
- 下拉列表父容器
	- `.dropdown` 用于创建下拉列表父容器【~~可以省略~~】
	- `.dropdown-center` 用于创建下拉列表父容器，使下拉列表居中
	- `.dropup` 上拉列表
	- `.dropstart` 前拉列表
	- `.dropend` 后拉列表
- 下拉按钮
	- `.dropdown-toggle` ***显示下箭头按钮***
	- `data-bs-toggle="dropdown"` ***指定了按钮的点击行为，点击时，它将触发下拉菜单的显示或隐藏***
	- `data-bs-auto-close="inside"` 下拉列表出现后，只有单击列表子项目，列表才会消失
	- `data-bs-auto-close="outside"` 下拉列表出现后，只有单击外部，列表才会消失
	- `data-bs-auto-close="false"` 下拉列表出现后，只有单击按钮，列表才会消失
- 下拉列表菜单 
	- `.dropdown-menu` 下拉列表
	- `.dropdown-menu-end` 下拉列表右对齐
- 下拉列表子项目
	- `.dropdown-item` 可交互的子项目
	- `.dropdown-item-text` 文本子项目【不可点击】
	- 在 `<hr>`里添加 `.dropdown-divider` 分割线
		```html
		<ul class="dropdown-menu">
			<li><a class="dropdown-item" href="#">Another action</a></li>
			<li>
				<hr class="dropdown-divider">
			</li>
			<li><a class="dropdown-item" href="#">Separated link</a></li>
		</ul>
		```
	- `.dropdown-header` 小标题
		```html
		<ul class="dropdown-menu">
			<li><h6 class="dropdown-header">Dropdown header</h6></li>
			<li><a class="dropdown-item" href="#">Action</a></li>
			<li><a class="dropdown-item" href="#">Another action</a></li>
		</ul>
		```

---
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
### 按钮下拉分离
- `.dropdown-toggle-split` 让<u>下拉按钮</u>与<u>按钮</u>更近

```html
<!-- btn-group 让两个按钮组合在一起没有间隙 -->
<div class="btn-group">
	<button type="button" class="btn btn-danger">Action</button>
	<button type="button" class="btn btn-danger dropdown-toggle dropdown-toggle-split" data-bs-toggle="dropdown"></button>
	<ul class="dropdown-menu">
		<li><a class="dropdown-item" href="#">Another action</a></li>
		<li><a class="dropdown-item" href="#">Separated link</a></li>
	</ul>
</div>
```
### 将表单放入下拉列表中
```html
<div class="dropdown">
  <button type="button" class="btn btn-primary dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false" data-bs-auto-close="outside">
    Dropdown form
  </button>
  <form class="dropdown-menu p-4">
    <div class="mb-3">
      <label for="exampleDropdownFormEmail2" class="form-label">Email address</label>
      <input type="email" class="form-control" id="exampleDropdownFormEmail2" placeholder="email@example.com">
    </div>
    <div class="mb-3">
      <label for="exampleDropdownFormPassword2" class="form-label">Password</label>
      <input type="password" class="form-control" id="exampleDropdownFormPassword2" placeholder="Password">
    </div>
    <div class="mb-3">
      <div class="form-check">
        <input type="checkbox" class="form-check-input" id="dropdownCheck2">
        <label class="form-check-label" for="dropdownCheck2">
          Remember me
        </label>
      </div>
    </div>
    <button type="submit" class="btn btn-primary">Sign in</button>
  </form>
</div>
```

## 折叠
- 父容器 `.accordion` 
	- `.accordion-flush` 五边框的手风琴
- 单个手风琴 `.accordion-item` 
	- `.accordion-header` 标题
	- `.accordion-button` 触发折叠的按钮
	- `.accordion-collapse` 折叠的隐藏内容容器
		- `.accordion-body` 折叠的隐藏内容
		- `.show` ***表示自动展示该手风琴隐藏的内容***

```html
<div class="accordion" id="accordionExample">
	// 第一个卡片
	<div class="accordion-item">
		<h2 class="accordion-header" id="headingOne">
			<button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne">
				Item 1
			</button>
		</h2>
		<!-- show 表示自动展示 -->
		<div id="collapseOne" class="accordion-collapse collapse show"
			data-bs-parent="#accordionExample">
			<div class="accordion-body">
				the transition does limit overflow.
			</div>
		</div>
	</div>

	// 第二个卡片
	<div class="accordion-item">
		<h2 class="accordion-header" id="headingTwo">
			<button class="accordion-button collapsed" type="button" data-bs-toggle="collapse"
				data-bs-target="#collapseTwo">
				Item 2
			</button>
		</h2>
		<div id="collapseTwo" class="accordion-collapse collapse" data-bs-parent="#accordionExample">
			<div class="accordion-body">
				the transition does limit overflow
			</div>
		</div>
	</div>

	// 第三个卡片
	<div class="accordion-item">
		<h2 class="accordion-header" id="headingThree">
			<button class="accordion-button collapsed" type="button" data-bs-toggle="collapse"
				data-bs-target="#collapseThree">
				Item 3
			</button>
		</h2>
		<div id="collapseThree" class="accordion-collapse collapse" data-bs-parent="#accordionExample">
			<div class="accordion-body">
				overflow
			</div>
		</div>
	</div>
</div>
```

## 导航
>将 `.nav` 添加到 `<ul>`，然后为每个 `<li>` 添加 `.nav-item`，并将 `.nav-link` 添加到它们的链接

- 父容器
	- `.nav` ***必须***
	- `.nav-tabs` 可以将导航项显示成标签页【~~类似浏览器~~】
	- `.nav-pills` 将导航项显示成按钮形式
	- `.nav-fill` 强制将导航项铺满整个宽度，但是每个导航项宽度不同
	- `.nav-justified` 强制将导航项铺满整个宽度，每个导航项宽度相同
- 导航项子容器
	- `.nav-item` 
	- `.nav-link` 用于 `<a>` 内，表示导航项【***必须***】

```html
<ul class="nav nav-pills nav-fill flex-xxl-row flex-column">
	<li class="nav-item">
		<a class="nav-link active" aria-current="page" href="#">Active</a>
	</li>
	<li class="nav-item">
		<a class="nav-link" href="#">Much longer nav link</a>
	</li>
	<li class="nav-item">
		<a class="nav-link" href="#">Link</a>
	</li>
	<li class="nav-item">
		<a class="nav-link disabled">Disabled</a>
	</li>
</ul>
```

### 导航栏
- 父容器
	- `.navbar` **必须**
	- `.navbar-expand-xxl|xl|lg|md|sm` 设置响应式堆叠，**如果不设置，则导航栏默认垂直堆叠**
- 子容器
	- `.navbar-nav` 常见于添加到 `<ul>`，`<div>`
- 孙子容器
	- `.nav-item` 
	- `.nav-link` 用于 `<a>` 内，表示导航项【***必须***】
	- `.navbar-brand` 用于突出显示网站 LOGO
	- `.navbar-text` 导航栏内文本

```html
<nav class="navbar navbar-expand-sm text-bg-dark">
	<div class="container-fluid">
		<a class="navbar-brand" href="#">
			<img src="https://img1.baidu.com/it/u=1621616811,1488147250&fm=253&fmt=auto&app=138&f=JPEG?w=683&h=697"
				alt="Avatar Logo" style="width:40px;" class="rounded-pill">
		</a>
	</div>
</nav>
```

#### 归类导航栏
![100](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403152318948.png)

- 归类按钮
	- `navbar-toggler`
	- `.data-bs-toggle="collapse"`
	- `data-bs-target="#collapsibleNavbar"`
- 被归类的导航 `<div>`
	- `collapse`
	- `navbar-collapse`
	- `id="collapsibleNavbar"`

```html
<nav class="navbar navbar-expand-lg bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown">
            Dropdown
          </a>
          <ul class="dropdown-menu">
            <li><a class="dropdown-item" href="#">Action</a></li>
            <li><a class="dropdown-item" href="#">Another action</a></li>
            <li><hr class="dropdown-divider"></li>
            <li><a class="dropdown-item" href="#">Something else here</a></li>
          </ul>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled">Disabled</a>
        </li>
      </ul>
      <form class="d-flex" role="search">
        <input class="form-control me-2" type="search" placeholder="Search">
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
```

#### 点击后侧边导航栏
```html
<nav class="navbar bg-body-tertiary fixed-top">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Offcanvas navbar</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasNavbar" aria-controls="offcanvasNavbar">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="offcanvas offcanvas-end" tabindex="-1" id="offcanvasNavbar" aria-labelledby="offcanvasNavbarLabel">
      <div class="offcanvas-header">
        <h5 class="offcanvas-title" id="offcanvasNavbarLabel">Offcanvas</h5>
        <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
      </div>
      <div class="offcanvas-body">
        <ul class="navbar-nav justify-content-end flex-grow-1 pe-3">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="#">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Link</a>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
              Dropdown
            </a>
            <ul class="dropdown-menu">
              <li><a class="dropdown-item" href="#">Action</a></li>
              <li><a class="dropdown-item" href="#">Another action</a></li>
              <li>
                <hr class="dropdown-divider">
              </li>
              <li><a class="dropdown-item" href="#">Something else here</a></li>
            </ul>
          </li>
        </ul>
        <form class="d-flex mt-3" role="search">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
          <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
      </div>
    </div>
  </div>
</nav>
```

## 轮播
- 父容器
	- `.carousel` 创建轮播
	- `.slide` 项目滑动时的过渡动画效果
	- `.carousel-fade` 过渡动画效果为淡入淡出
	- ` data-bs-ride="carousel"` 自动轮播
	- `data-bs-ride="true"` 会在用户第一次点击轮播后，自动轮播
	- `data-bs-touch="false"` 禁用在触摸屏幕上的左右滑动
- 子容器
	- 指示器
		- `.carousel-indicators` 下方的指示器【幻灯片数量……】
	- 幻灯片
		- `.carousel-inner` 幻灯片父容器
	- 左右切换按钮
		- `.carousel-control-prev` 向轮播添加一个向左按钮
		- `.carousel-control-next` 向轮播添加一个向右按钮
- 孙子容器
	- `.carousel-item` 幻灯片子容器
		- `.carousel-caption` 作为幻灯片标题
	- `data-bs-interval="数值"` 规定幻灯片的延迟时间
	- `.carousel-control-prev-icon` 创建“上一个”按钮
	- `.carousel-control-next-icon` 创建“下一个”按钮

>[!warning] 必须将 `.active` 添加到其中一张幻灯片中，否则轮播界面将不可见

>[!warning] 确保在可选控件上 `.carousel` 设置唯一 `id` 值，尤其是在单个页面上使用多个轮播界面时。左右控件和指示器的 `data-bs-target` 的属性值必须与该 `id` 匹配

```html
<!-- 轮播 -->
<div id="demo" class="carousel slide carousel-fade" data-bs-ride="carousel">
	<!-- 指标/点 -->
	<div class="carousel-indicators">
		<button type="button" data-bs-target="#demo" data-bs-slide-to="0" class="active"></button>
		<button type="button" data-bs-target="#demo" data-bs-slide-to="1"></button>
		<button type="button" data-bs-target="#demo" data-bs-slide-to="2"></button>
	</div>

	<!-- 幻灯片/轮播 -->
	<div class="carousel-inner">
		<div class="carousel-item active">
			<img src="https://img0.baidu.com/it/u=654488740,3936603920&fm=253&fmt=auto&app=120&f=JPEG?w=500&h=500"
				alt="Los Angeles" class="d-block w-100">
			<div class="carousel-caption">
				<h3>beautiful</h3>
				<p>beautiful</p>
			</div>
		</div>
		<div class="carousel-item" data-bs-interval="200">
			<img src="https://img2.baidu.com/it/u=1252757541,3049039935&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500"
				alt="Chicago" class="d-block w-100">
		</div>
		<div class="carousel-item">
			<img src="https://img1.baidu.com/it/u=3010889845,4227116112&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500"
				alt="New York" class="d-block w-100">
		</div>
	</div>

	<!-- 左右控件/图标 -->
	<button class="carousel-control-prev" type="button" data-bs-target="#demo" data-bs-slide="prev">
		<span class="carousel-control-prev-icon"></span>
	</button>
	<button class="carousel-control-next" type="button" data-bs-target="#demo" data-bs-slide="next">
		<span class="carousel-control-next-icon"></span>
	</button>
</div>
```

>[!hint] 看不懂思密达
> 出于性能原因，必须使用轮播构造函数方法手动初始化轮播。如果不进行初始化，则在用户显式激活控件或指示器之前，不会注册某些事件侦听器（特别是需要触摸/轻扫支持的事件）。唯一的例外是带有该属性的 `data-bs-ride="carousel"` 自动播放轮播，因为这些轮播是在页面加载时自动初始化的。如果使用带有 data 属性的自动播放轮播，请不要使用 constructor 方法显式初始化相同的轮播

## 模态
>模态是一种弹出窗口，显示在当前页面的最上层

- 父容器
	- `.fade` 在 `.modal` 添加淡入淡出效果
	- `data-bs-backdrop="static"` 规定点击外部不会关闭模态
- 子容器
	- `.modal-sm/lg/xl` 在 `.modal-dialog` 里设置大小
	- `modal-fullscreen` 在 `.modal-dialog` 里设置弹出窗口为全屏
		- `.modal-fullscreen-sm-down` 576px 以下全屏
		- `.modal-fullscreen-xxl-down` 1400px 以下全屏
	- `modal-dialog-scrollable` 在 `.modal-dialog` 里设置溢出时的滚动条
	- `modal-dialog-centered` 在 `.modal-dialog` 里设置模态垂直居中

```html
<!-- 打开模态的按钮 -->
<button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#myModal">
  Open modal
</button>

<!-- 模态 -->
<div class="modal fade" id="myModal">
  <div class="modal-dialog modal-sm">
    <div class="modal-content">
    
      <!-- 模态标题 -->
      <div class="modal-header">
        <h4 class="modal-title">Modal Heading</h4>
        <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
      </div>

      <!-- 模态主体 -->
      <div class="modal-body">
        模态主体 ..
      </div>

      <!-- 模态页脚 -->
      <div class="modal-footer">
        <button type="button" class="btn btn-danger" data-bs-dismiss="modal">关闭</button>
      </div>
    </div>
  </div>
</div>
```

### 模态的切换
```html
<div class="modal fade" id="exampleModalToggle" tabindex="-1">
  <div class="modal-dialog modal-dialog-centered">
    <div class="modal-content">
      <div class="modal-header">
        <h1 class="modal-title fs-5" id="exampleModalToggleLabel">Modal 1</h1>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        Show a second modal and hide this one with the button below.
      </div>
      <div class="modal-footer">
        <button class="btn btn-primary" data-bs-target="#exampleModalToggle2" data-bs-toggle="modal">Open second modal</button>
      </div>
    </div>
  </div>
</div>
<div class="modal fade" id="exampleModalToggle2" tabindex="-1">
  <div class="modal-dialog modal-dialog-centered">
    <div class="modal-content">
      <div class="modal-header">
        <h1 class="modal-title fs-5" id="exampleModalToggleLabel2">Modal 2</h1>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        Hide this modal and show the first with the button below.
      </div>
      <div class="modal-footer">
        <button class="btn btn-primary" data-bs-target="#exampleModalToggle" data-bs-toggle="modal">Back to first</button>
      </div>
    </div>
  </div>
</div>
<button class="btn btn-primary" data-bs-target="#exampleModalToggle" data-bs-toggle="modal">Open first modal</button>
```

## 弹出框
### 悬停提示
>将 `data-bs-toggle="tooltip"` 添加到元素，并使用 `title` 属性指定提示内显示的文本

>[!warning] 提示必须用 JavaScript 初始化才能工作

- `data-bs-placement="top/bottom/left/right"` 设置提示的位置

```html
<button type="button" class="btn btn-primary" data-bs-toggle="tooltip" title="太棒了！">请悬停在我上面！</button>
<a href="#" data-bs-toggle="tooltip" data-bs-placement="right" title="太棒了！">Hover</a>

<script>
const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]')
const tooltipList = [...tooltipTriggerList].map(tooltipTriggerEl => new bootstrap.Tooltip(tooltipTriggerEl))
</script>
```

When triggered from hyperlinks that span multiple lines, tooltips will be centered. Use `white-space: nowrap;` on your `<a>`s to avoid this behavior.












### 点击提示














