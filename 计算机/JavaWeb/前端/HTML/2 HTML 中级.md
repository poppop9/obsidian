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
	- `month` 月份，年份
	- `week` 周，年
	- `color` 颜色
	- `range` 一个范围
	- `datetime-local` 日期＋时间
	- `number` 数字输入框
	- `email` 邮件输入框
	- `hidden` 隐藏域
	- `按钮` 
		- `submit` 提交按钮
		- `reset` 重置按钮【重置表单数据】
		- `button` 可点击按钮
- `name` ***name相同表示是同一个表单项***，必须指定
- `value` ***规定输入字段的初始值***
- `autocomplete` 是否记录用户上次填写的数据
	- **on** 可以在下一次填写时，记忆上次填写的内容
	- **off**
- `autofocus` 当页面加载完成后，某个 `input` 自动获得焦点
- `multiple` 允许输入多个值【适用于 `file`，`email`】
- `placeholder` 输入值时的提示

- `formaction` 指定按钮的提交地址，***会覆盖 `<form>` 表单的 `action`***
- `formenctype` 指定按钮的提交编码，***会覆盖 `<form>` 的 `enctype`***
- `formmethod` 指定按钮的提交方式，***会覆盖 `<form>` 的 `method`***

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
    月份年份：<input type="month" name="bdaymonth"><br><br>
    周，年：<input type="week" name="week_year"><br><br>
	颜色:<input type="color" name="favcolor"><br><br>
	范围：<input type="range" name="points" min="0" max="10"><br><br>
    日期时间: <input type="datetime-local" name="datatime"><br><br>
    邮箱: <input type="email" name="email"><br><br>
    年龄: <input type="number" name="age" placeholder="写年轻点"><br><br>
	<input type="hidden" name="id" value="1">
    <input type="submit" value="提交">
	<input type="submit" value="提交给管理员" formaction="" formenctype="multipart/form-data">
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
	月份年份：<input type="month" name="bdaymonth"><br><br>
    周，年：<input type="week" name="week_year"><br><br>
	颜色:<input type="color" name="favcolor"><br><br>
	范围：<input type="range" name="points" min="0" max="10"><br><br>
    日期时间: <input type="datetime-local" name="datatime"><br><br>
    邮箱: <input type="email" name="email"><br><br>
    年龄: <input type="number" name="age" placeholder="写年轻点"><br><br>
	<input type="hidden" name="id" value="1">
    <input type="submit" value="提交">
	<input type="submit" value="提交给管理员" formaction="" formenctype="multipart/form-data">
    <input type="reset" value="重置">
    <input type="button" value="按钮">
</form>

>[!hint] 可以使用以下属性对 `type` 进行数据的限制
>
> | 属性 | 描述 |
> | ---- | ---- |
> | max | 规定输入字段的最大值 |
> | maxlength | 规定输入字段的最大字符数 |
> | min | 规定输入字段的最小值 |
> | pattern | 规定检查输入值的正则表达式 |
> | ***readonly*** | 规定输入字段为只读（无法修改），可提交 |
> | ***disabled*** | 规定输入字段被禁用，不可修改，不可提交 |
> | required | 规定输入字段是必需的 |
> | size | 规定输入字段的宽度（以字符计） |
> | step | 规定输入字段的合法数字间隔 |

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

# 图像
## 画布\<Canvas>
>`<canvas>` 元素使用 `JavaScript` 绘制图像

1. 规定id，高度，宽度
	```html
	<canvas id="myCanvas" width="200" height="100"></canvas>
	```
2. JavaScript 通过 `id` 找到 `<canvas>`
3. 创建 context 对象
4. ……
```js
var c=document.getElementById("myCanvas");
var cxt=c.getContext("2d");
cxt.fillStyle="#FF0000";
cxt.fillRect(0,0,150,75);
```

>[!hint] 优缺点
>- 由于基于像素绘制，依赖分辨率
>- 由于基于像素绘制，不支持事件处理
>- 适合需要频繁重绘场景【因为只需要修改部分像素】

https://www.w3school.com.cn/graphics/canvas_intro.asp
## 矢量图\<SVG>
>SVG 指可伸缩矢量图形，使用 XML 格式定义图形

>[!hint] SVG 的优点
> - 支持事件处理
> - SVG 图像可通过文本编辑器来创建和修改
> - SVG 图像可被脚本化【利用JavaScript实现交互性，动态效果】
> - ***SVG放大，其图形质量不会有损失***
> - 不如 `canvas` 快

==<svg xmlns="http://www.w3.org/2000/svg" version="1.1" height="190">
  <polygon points="100,10 40,180 190,60 10,60 160,180"
  style="fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;" />
</svg>==

https://www.w3school.com.cn/graphics/svg_intro.asp

































