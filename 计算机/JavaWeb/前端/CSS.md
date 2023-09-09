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