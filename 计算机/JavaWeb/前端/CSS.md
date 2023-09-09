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
```css
<style>
	h1 {
		xxx:yyy;
	}
	span {
		xxx:yyy;
	}
</style>
```
- id选择器
***id不能重用***,***不能以数字开头***
```css
<style>
	#001 {
		xxx:yyy;
	}
	#002 {
		xxx:yyy;
	}
</style>
```
```html
<h1 id="001">我是一级标题</h1>
<span id="002">我是正文</span>
```
- 类选择器
***类名可以重用***
```css
<style>
	.001 {
		xxx:yyy;
	}
	.002 {
		xxx:yyy;
	}
</style>
```
```html
<h1 class="001">我是一级标题</h1>
<span class="002">我是正文</span>
```
### 外联样式
```css
h1 {
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















