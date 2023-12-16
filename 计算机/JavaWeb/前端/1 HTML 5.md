# 🌕网页的结构
![[JavaWeb Draw#^group=QUadQUqX|900]]
# 🌕特殊字符
`&nbsp;` 空格符
`&lt;` <
`&gt;` >
`&amp;` &
`&yen;` ￥
`&copy;` ©
`&reg;` ®
`&deg;` ℃
`plusmn;` 正负号
`&times;` 乘号
`&divide;` 除号
`&sup2;` 平方²
`&sup3;` 立方³
# 🌕骨架标签
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
# 🌕常用标签
>[!hint] 内联元素 和 块级元素
>
> - 对于内联元素，属性只能影响其内部的文本内容，并不能改变整个元素在父容器中的状态。如果需要改变可以将内联元素放在块级元素中 / 使用其他布局技术【Flexbox 或 Grid】
> 
> - 对于块级元素，属性可以改变内部内容和整个状态
> 	- 常见：div，h，table，form
> 
> 例如：想让一个链接位于水平居中，必须
> ![[Excalidraw/计算机/JavaWeb Draw.md#^group=7TskywFx|600]]
### 🌗注释
`<!--注释内容-->`
### 🌗标题\<h\>
> 一个标题独占一行，有6个等级的标题可以选择

```
<h1>我是一级标题</h1>
<h2>我是一级标题</h2>
…………
<h6>我是一级标题</h6>
```
### 🌗段落\<p\>
> 段落之间会在网页显示时会有空隙

```html
<p>你好，我是HTML 5</p>
<p>你好，我是HTML 5</p>

你好，我是HTML 5

你好，我是HTML 5
```
### 🌗换行\<br/\>
> 一个段落中的文字会从左到右排列，直到浏览器窗口的右端才会自动换行，***而换行标签可以对文本进行强制换行***

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
### 🌗文本格式
`<b></b>` 加粗
`<i></i>` 倾斜
`<del></del>` 删除线
`<u></u>` 下划线
### 🌗无语义盒子
>这两个标签都是没有具体意思的，它们就是一个***盒子***【用来装文字，图片，超链接】
>![[JavaWeb Draw#^group=jLK9MAUa|600]]
##### 🌑\<div\>
> 一个`<div>`独占一行
##### 🌑\<span\>
> 多个`<span>`标签占一行

***\<span\>标签无法设置width和height，宽度和高度由内容默认撑开***
### 🌗分割线\<hr\>
```html
<span id="h001">2023年9月9日 20:38:00</span>
<hr>
```
### 🌗超链接\<a\>
`href` 指定的URL
`target` 以哪种方式打开超链接【在当前页面打开`_self`，在新页面打开`_blank`】

```html
<a id="h002" href="https://www.zjxu.edu.cn/" target="_blank">嘉兴学院</a>
```
##### 🌑锚点链接
就像是PDF的目录一样
```html
<h4 id="live">个人生活</h4>

<a herf="#live">个人生活</a>
```
### 🌗图片\<img\>
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
### 🌗视频\<video\>
`autoplay` 视频就绪后自动播放
`controls` 视频的控制按钮【暂停，音量调节等】
`width` 视频的宽度
`height` 视频的高度
`loop` 视频播放完成后再次播放
`muted` 视频播放默认静音
`poster` 视频未播放时显示的图片

```html
<video src="D:\Overthink｜时光代理人ED原创舞蹈【Figo × 王一大只】.mp4" poster="https://img0.baidu.com/it/u=1802578230,1841279071&fm=253&fmt=auto&app=120&f=JPEG?w=800&h=500" controls loop width="700"></video>
```
### 🌗音频\<audio\>
```html
<audio src="E:\迅雷下载\就是爱你-陶喆.flac" controls>流沙</audio>
```
### 🌗表格\<table\>
`<tr>` 一行
`<th>` 表头
`<td>` 表格单元格元素

`align` 表格相对周围元素的对齐方式
`border` 表格边框宽度
`width` 表格整体宽度
`height` 表格整体高度
`cellspacing` 边框之间的空间

```html
<table border="1px" cellspacing="0" width="300px" align="center">
	<tr>
		<th>姓名</th>
		<th>性别</th>
		<th>年龄</th>
	</tr>
	<tr>
		<td>吴彦祖</td>
		<td>男</td>
		<td>48</td>
	</tr>
	<tr>
		<td>刘德华</td>
		<td>男</td>
		<td>58</td>
	</tr>
	<tr>
		<td>张学友</td>
		<td>男</td>
		<td>59</td>
	</tr>
</table>
```
![[JavaWeb Draw#^group=h6qa99MH|370]]
### 🌗表单\<form\>
- `action` 指定表单提交时去往的URL地址
- `method` 表单数据的提交方式。
	- `get` 会在URL后面拼接表单数据。【当表单数据很长时不推荐】
	  ```html
	  <form action="" method="get">        //action不写默认提交到当前页面
	  </form>
	  
	  
	  file:///E:/VScode/html/9_9.html?username=123&password=456  //URL后面会出现表单数据
	  ```
	- `post` 在消息体中传递【表单数据大小无限制】
- `enctype`  指定表单数据提交的格式
	- `默认`  
	- `multipart/form-data`  ***用于提交文件的格式***【其他格式提交文件会只提交文件名】
##### 🌑\<input\>
  - `type` 
    - `text` 单行输入字段
    - `password` 密码字段
    - `radio` 单选按钮
    - `checkbox` 复选框
    - `file` 文件上传按钮
    - `date` 日期
    - `time` 时间
    - `datetime-local` 日期＋时间
    - `number` 数字输入框
    - `email` 邮件输入框
    - `hidden` 隐藏域
    - `按钮` 
      - `submit` 提交按钮
      - `reset` 重置按钮【重置表单数据】
      - `button` 可点击按钮
  - `name` ***name相同表示是同一个表单项***
  - `value` ***提交表单时真正提交的值***

```html
<form action="" method="get">
    用户名: <input type="text" name="username"><br><br>
    密码: <input type="password" name="password"><br><br>
    性别:
    <input type="radio" name="gender" value="男">男
    <input type="radio" name="gender" value="女">女<br><br>
    爱好:
    <input type="checkbox" name="hobby" value="java">java
    <input type="checkbox" name="hobby" value="c">c
    <input type="checkbox" name="hobby" value="python">python<br><br>
    图像: <input type="file" name="image"><br><br>
    生日: <input type="date" name="birthday"><br><br>
    时间: <input type="time" name="time"><br><br>
    日期时间: <input type="datetime-local" name="datatime"><br><br>
    邮箱: <input type="email" name="email"><br><br>
    年龄: <input type="number" name="age"><br><br>

	<input type="hidden" name="id" value="1">
    <input type="submit" value="提交">
    <input type="reset" value="重置">
    <input type="button" value="按钮">
</form>
```
<form action="" method="get">
    用户名: <input type="text" name="username"><br><br>
    密码: <input type="password" name="password"><br><br>
    性别:
    <input type="radio" name="gender" value="男">男
    <input type="radio" name="gender" value="女">女<br><br>
    爱好:
    <input type="checkbox" name="hobby" value="java">java
    <input type="checkbox" name="hobby" value="c">c
    <input type="checkbox" name="hobby" value="python">python<br><br>
    图像: <input type="file" name="image"><br><br>
    生日: <input type="date" name="birthday"><br><br>
    时间: <input type="time" name="time"><br><br>
    日期时间: <input type="datetime-local" name="datatime"><br><br>
    邮箱: <input type="email" name="email"><br><br>
    年龄: <input type="number" name="age"><br><br>

	<input type="hidden" name="id" value="1">
    <input type="submit" value="提交">
    <input type="reset" value="重置">
    <input type="button" value="按钮">
</form>


###### 🌙file
>如果要提交的表单里有 `file` 类型的数据，则要设置指定的编码格式

```html
<form action="" method="get" enctype="multipart/form-data"> //需要指定编码格式enctype
    图像: <input type="file" name="image"><br><br>
</form>
```
##### 🌑\<select\>
  - `option` 

```html
<form action="" method="get">
    <select name="degree">
        <option value="0">请选择</option>
        <option value="1">小学</option>
        <option value="2">高中</option>
        <option value="3">大学</option>
        <option value="4">博士</option>
    </select><br><br>
</form>
```
<form action="" method="get">
    <select name="degree">
        <option value="0">请选择</option>
        <option value="1">小学</option>
        <option value="2">高中</option>
        <option value="3">大学</option>
        <option value="4">博士</option>
    </select><br><br>
</form>

##### 🌑\<textarea\>
```html
<form action="" method="get">
    描述:<textarea name="description" cols="30" rows="10"></textarea><br><br>
</form>
```
<form action="" method="get">
    描述:<textarea name="description" cols="30" rows="10"></textarea><br><br>
</form>

### 🌗图标\<i\>

```html
<!DOCTYPE html>
<html>
	<head>
		<title>Google Icons</title>
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">         <!--引入谷歌icon库-->
	</head>
	<body>
		<i class="material-icons">cloud</i>
		<i class="material-icons">favorite</i>
		<i class="material-icons">attachment</i>   <!--指定class，再指定icon名-->
		<i class="material-icons">computer</i>
		<i class="material-icons">traffic</i>
		<br>

		<!--可以通过css更改icon的样式-->
		<i class="material-icons" style="font-size:24px;">cloud</i>
		<i class="material-icons" style="font-size:48px;color:red;">cloud</i>
	</body>
</html>
```







# 🌕快捷键
`!` 生成骨架标签
`ctrl+shift+/` 注释
`ctrl+alt+l` 格式化代码

`img` 生成图片标签





