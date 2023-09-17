Ajax是异步的JavaScript和XML。
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

# XMLHttpRequest
>[!summary] 属性
>***readyState***  保存 XMLHttpRequest 的状态【0：请求未初始化；1：服务器连接已建立；2：请求已收到；3：正在处理请求；4：请求已完成且响应已就绪】
>***status***  返回请求的状态号【200: "OK"；403: "Forbidden"；404: "Not Found"】
>***responseText***	以字符串形式返回响应数据


```
Function loadDoc()

function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
     document.getElementById("demo").innerHTML = this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
}
```
# Axios
Axios 对原生的 Ajax 进行了封装，简化了书写
### get请求
![[Excalidraw/计算机/JavaWeb.md#^group=MCFLFBbf|600]]
### post请求
![[Excalidraw/计算机/JavaWeb.md#^group=jnhZ6xju|600]]

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











































