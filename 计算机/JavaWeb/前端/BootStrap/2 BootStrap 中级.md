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






















