# 常用标签
## 表单\<form\>
- `action` 指定表单提交时去往的URL地址
- `method` 表单数据的提交方式
	- **get** 会在URL后面拼接表单数据。【当表单数据很长时不推荐】
	  ```html
	  <form action="去往的url" method="get">        //action不写默认提交到当前页面
	  </form>
	  
	  
	  file:///E:/VScode/html/9_9.html?username=123&password=456  //URL后面会出现表单数据
	  ```
	- **post** 在消息体中传递【表单数据大小无限制】
- `enctype`  指定表单数据提交的格式
	- **默认**  
	- **multipart/form-data**  用于提交文件的格式【其他格式提交文件会只提交文件名】
- `<fieldset>` 组合表单数据
	- `<legend>` 为 `<fieldset>` 定义标题
- `autocomplete` 是否记录用户上次填写的数据
	- **on** 可以在下一次填写时，记忆上次填写的内容
	- **off**

```html
<form action="action_page.php">
	<fieldset>
		<legend>Personal information:</legend>
		First name:
		<input type="text" name="firstname" value="Mickey">
		<br>
		Last name:
		<input type="text" name="lastname" value="Mouse">
		<br>
		<input type="submit" value="Submit">
	</fieldset>
</form>
```
<form action="action_page.php">
	<fieldset>
		<legend>Personal information:</legend>
		First name:
		<input type="text" name="firstname" value="Mickey">
		<br>
		Last name:
		<input type="text" name="lastname" value="Mouse">
		<br>
		<input type="submit" value="Submit">
	</fieldset>
</form>

### \<input>
- `type` 
	- `text` 单行输入字段
	- `password` 密码字段
	- `radio` 单选按钮
	- `checkbox` 复选框
	- `file` 文件上传按钮
		>需要设置指定的编码格式

		```html
		<form action="" method="get" enctype="multipart/form-data"> //需要指定编码格式enctype
		    图像: <input type="file" name="image"><br><br>
		</form>
		```

	- `date` 日期
	- `time` 时间
	- `datetime-local` 日期＋时间
	- `number` 数字输入框，***可以设置允许输入数字的最大最小值***
		```html
		<input type="number" name="quantity" min="1" max="5">
		```
	- `email` 邮件输入框
	- `hidden` 隐藏域
	- `按钮` 
		- `submit` 提交按钮
		- `reset` 重置按钮【重置表单数据】
		- `button` 可点击按钮
- `name` ***name相同表示是同一个表单项***，必须指定
- `value` ***提交表单时真正提交的值***

---
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

#### \<datalist>
>为input设置预选值

```html
<form action="/demo/demo_form.asp">
	<input list="browsers" name="browser">
	<datalist id="browsers">
		<option value="Internet Explorer">
		<option value="Firefox">
		<option value="Chrome">
		<option value="Opera">
		<option value="Safari">
	</datalist>
	<input type="submit">
</form>
```
<form action="/demo/demo_form.asp">
	<input list="browsers" name="browser">
	<datalist id="browsers">
		<option value="Internet Explorer">
		<option value="Firefox">
		<option value="Chrome">
		<option value="Opera">
		<option value="Safari">
	</datalist>
	<input type="submit">
</form>

### 下拉表单\<select>
#### \<option>
>定义选项

  - `selected` 可以指定预选项，不指定则默认第一个

```html
<form action="" method="get">
    <select name="degree">
        <option value="0">请选择</option>
        <option value="1" selected>小学</option>
        <option value="2">高中</option>
        <option value="3">大学</option>
        <option value="4">博士</option>
    </select><br><br>
</form>
```
<form action="" method="get">
    <select name="degree">
        <option value="0">请选择</option>
        <option value="1" selected>小学</option>
        <option value="2">高中</option>
        <option value="3">大学</option>
        <option value="4">博士</option>
    </select><br><br>
</form>

### \<textarea>
```html
<form action="" method="get">
    描述:<textarea name="description" cols="30" rows="10">aaa</textarea><br><br>
</form>
```
<form action="" method="get">
    描述:<textarea name="description" cols="30" rows="10">aaa</textarea><br><br>
</form>

## 网页内网页\<ifame>
```html
/* 单击链接，会iframe里的内容就会跳转到b站 */
<iframe src="https://www.baidu.com/" name="baidu" width="700" height="200"></iframe>
<a href="https://www.bilibili.com/" target="baidu">点我</a>
```


































