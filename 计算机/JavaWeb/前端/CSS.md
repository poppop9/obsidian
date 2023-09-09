# 引入方式
### 行内样式
***只作用于当前标签***
`<h1 style="xxx:yyy; xxx:yyy;">HTML 5</h1>`
### 内嵌样式
***写在\<head\>标签里***，***作用于整个html文件***
```html
<style>
	h1 {
		xxx:yyy;
		xxx:yyy;
	}
</style>
```
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
### 颜色
`color:属性值;`
属性值可以是某个***颜色名***，***RGB***，***十六进制表示法***
```html
<style>
	h1 {
		color: red;
	}
</style>
```















