> Ajax是异步的JavaScript和XML
- ***Ajax可以发送请求到服务器，并获取服务器的响应***
- ***Ajax还可以在不加载网页的情况下，实现实时更新网页的数据***

---

1. 网页中发生一个事件（页面加载、按钮点击）
2. 由 JavaScript 创建 XMLHttpRequest 对象
3. XMLHttpRequest 对象向 web 服务器发送请求
4. 服务器处理该请求
5. 服务器将响应发送回网页
6. 由 JavaScript 读取响应
7. 由 JavaScript 执行正确的动作（比如更新页面）

# 🌕XMLHttpRequest
>[!summary] 属性
>***readyState***  保存 XMLHttpRequest 的状态【0：请求未初始化；1：服务器连接已建立；2：请求已收到；3：正在处理请求；4：请求已完成且响应已就绪】
>
>***status***  返回请求的状态号【200: "OK"；403: "Forbidden"；404: "Not Found"】
>
>***responseText***	以字符串形式返回响应数据
# 🌕Axios
> Axios 对原生的 Ajax 进行了封装，简化了书写
### 🌗安装Axios
##### 🌑在Vue项目中使用Axios
- 在项目目录下的cmd输入`npm install axios`
- 需要Axios时，在`script标签`中导入`import axios from 'axios'`
- 然后就可以在`script标签`中使用axios了
##### 🌑在HTML文件中使用Axios
- 在`head标签`中导入`axios.js`文件
	```html
	<head>
	    <script src="JS/axios.js"></script>         <!--引入axios.js文件-->
	</head>
	```
- 然后就可以在`script标签`中使用axios了
### 🌗方法

##### 🌑get请求
![[JavaWeb Draw#^group=MCFLFBbf|600]]
##### 🌑post请求
![[JavaWeb Draw#^group=jnhZ6xju|600]]
##### 🌑delete

##### 🌑put

### 🌗示例1 - 用get，post获取提交数据
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Axios</title>
    <script src="JS/axios.js"></script>         <!--引入axios.js文件-->
</head>

<body>
    <input type="button" value="获取数据" onclick="get()">
    <input type="button" value="提交数据" onclick="post()">
</body>
<script>
    function get() {
        axios.get("data.json").then(result => {
            console.log(result.data);
        })
    }

    function post() {
        axios.post("http://127.0.0.1:10088", "id=1").then(result => {
            console.log(result.data);
        })
    }
</script>
</html>
```
### 🌗示例2 - 用异步请求填充表格
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Axios案例</title>
    <script src="JS/axios.js"></script>
    <script src="JS/vue.js"></script>

</head>

<body>
    <div id="app">
        <table border="1px" cellspacing="0" width="300px">
            <tr>
                <th>编号</th>
                <th>姓名</th>
                <th>年龄</th>
                <th>性别</th>
                <th>地址</th>
            </tr>
            <tr v-for="(element, index) in arr" align="center">  //数组元素为element
                <td>{{index+1}}</td>
                <td>{{element.name}}</td>
                <td>{{element.age}}</td>
                <td>
                    <span v-if="element.gender==1">男</span>
                    <span v-else="element.gender==2">女</span>
                </td>
                <td>{{element.address}}</td>
            </tr>
        </table>
    </div>

</body>
<script>
    new Vue({
        el: "#app",
        data: {
            arr: []  //定义了一个数组
        },
        mounted() {
            axios.get("data.json").then(result => {
                this.arr = result.data.data; 
            })          //result.data表示拿到了对象的数据，再加.data表示data键的值
        }
    })
</script>
</html>


以下为data.json的结构
{
    "code": 1,
    "msg": "success",
    "data": [
        {……},{……}
    ]
}
```










































