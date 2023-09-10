# 网页的结构
![[Excalidraw/计算机/JavaWeb.md#^group=QUadQUqX|900]]
# 骨架标签
`<!doctype html>` 告诉浏览器使用HTML版本来显示网页
`<html lang="en">` 设置网页的语言。中文为“zh-CN”
`<meta charset="UTF-8">` 设置字符集合

```html
<!DOCTYPE html>   
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我是HTML 5</title>
</head>
</html>
```

# 常用标签
### 注释
`<!--注释内容-->`
### 标题
`<h1>标题名称</h1>`
一个标题独占一行，有6个等级的标题可以选择

```
<h1>我是一级标题</h1>
<h2>我是一级标题</h2>
…………
<h6>我是一级标题</h6>
```
### 段落\<p\>
段落之间会在网页显示时会有空隙

```html
<p>你好，我是HTML 5</p>
<p>你好，我是HTML 5</p>

你好，我是HTML 5

你好，我是HTML 5
```
### 换行
`<br/>`
一个段落中的文字会从左到右排列，直到浏览器窗口的右端才会自动换行，***而换行标签可以对文本进行强制换行***

```html
<p>你好，我是HTML 5 你好，我是HTML 5
	你好，我是HTML 5 你好，我是HTML 5
	你好，我是HTML 5 你好，我是HTML 5 <br/>
	你好，我是HTML 5 你好，我是HTML 5
	你好，我是HTML 5 你好，我是HTML 5
	你好，我是HTML 5 你好，我是HTML 5
	你好，我是HTML 5 你好，我是HTML 5
	你好，我是HTML 5 你好，我是HTML 5
</p>
```
### 文本格式
`<b></b>` 加粗
`<i></i>` 倾斜
`<del></del>` 删除线
`<u></u>` 下划线
### 无语义
这两个标签都是没有具体意思的，它们就是一个***盒子***【用来装文字，图片，超链接】
##### \<div\>
一个`<div>`独占一行
##### \<span\>
多个`<span>`标签占一行
### 分割线
`<hr>`
### 图片\<img\>
***属性之间要有空格***
`src` 指定图片路径

`alt` 当图片因为某些原因无法显示时，显示该文字
`title` 提示文本【鼠标悬浮时显示该文本】

`width` 图像的宽度【单位可以是像素`px`，也可以是百分比`%`(百分比是相对于父元素的)】
`height` 图像的高度
`border` 图像的边框粗细

```html
<img src="https://1b2a.net/img/tv/PwGW.avif" width="300" title="装腔启示录" />
```
### 超链接\<a\>
`href` 指定的URL
`target` 以哪种方式打开超链接【在当前页面打开`_self`，在新页面打开`_blank`】

```html
<a id="h002" href="https://www.zjxu.edu.cn/" target="_blank">嘉兴学院</a>
```
##### 锚点链接
就像是PDF的目录一样
```html
<h4 id="live">个人生活</h4>

<a herf="#live">个人生活</a>
```
### 视频\<video\>

### 音频\<audio\>

# 快捷键
`!` 生成骨架标签
`ctrl+shift+/` 注释
`ctrl+alt+l` 格式化代码

`img` 生成图片标签






