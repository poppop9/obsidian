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
==优先级：id选择器 > 类选择器 > 元素选择器==
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
### 颜色 color
- 颜色名`color: red;`
- RGB`color: rgb(255, 0, 0);`
- 十六进制表示法`color: #ff0000;`
### 大小 font-size
### 文本修饰
`initial` 默认值
`inherit` 从其父元素继承属性
##### line
`text-decoration-line: none;` 无
`text-decoration-line: overline;` 上划线
`text-decoration-line: underline;` 下划线
`text-decoration-line: line-through;` 删除线
`text-decoration-line: overline underline;` 叠加属性
##### style
`text-decoration-style: solid;` 单线
`text-decoration-style: wavy;` 波浪线
`text-decoration-style: double;` 双线
`text-decoration-style: dotted;` 点线
`text-decoration-style: dashed;` 虚线
##### thickness
`text-decoration-thickness: auto;` 浏览器选择装饰线的粗细
`text-decoration-thickness: 5;` 5像素
`text-decoration-thickness: 50%;` 百分比值










