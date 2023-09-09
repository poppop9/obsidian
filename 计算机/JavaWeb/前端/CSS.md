# 引入方式
### 行内样式
***只作用于当前标签***
`<h1 style="xxx:yyy; xxx:yyy;">HTML 5</h1>`
### 内嵌样式
***写在\<head\>标签里***，***作用于整个html文件***
```html
<style>
	选择器 {
		xxx:yyy;
		xxx:yyy;
	}
</style>
```
##### 选择器
- 元素选择器
```html
<style>
	h1 {
		xxx:yyy;
		xxx:yyy;
	}
	span {
		xxx:yyy;
		xxx:yyy;
	}
</style>
```
- id选择器
```html
<h1 id>我是一级标题</h1>
```
```html
<style>
	h1 {
		xxx:yyy;
		xxx:yyy;
	}
	span {
		xxx:yyy;
		xxx:yyy;
	}
</style>
```

- 类选择器
### 外联样式
```html
h1 {
	xxx:yyy;
	xxx:yyy;
}
```
```html
<link rel="stylesheet" href="路径">
```
# 文本
### 颜色color
- 颜色名`color: red;`
- RGB`color: rgb(255, 0, 0);`
- 十六进制表示法`color: #ff0000;`















