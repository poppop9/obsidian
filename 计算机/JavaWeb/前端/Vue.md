Vue 是一种流行的JavaScript前端框架，提供了一种响应式的双向数据绑定
# 常用指令
### v-bind
为标签绑定属性值
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="JS/vue.js"></script>    <!--引入vue.js文件-->
</head>

<body>
    <div id="img_1">
        <img id="img_1" v-bind:src="url">  <!--输入v-bind指令绑定src属性-->
    </div>
</body>

<script>
    new Vue({
        el: "#img_1",       //指定vue生效的对象，此处是id为img_1的标签
        data: {
            url: "https://1b2a.net/img/tv/kp2d.avif"  //定义url的数值
        }
    })
</script>
</html>
```
### v-model
为***表单元素***创建双向数据绑定
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="JS/vue.js"></script>
</head>

<body>
    <div id="input_1">
        <input type="text" v-model="url">  <!--使用v-model指令，绑定文本框里的内容-->
        <a v-bind:href="url">Go to</a>  <!--绑定a链接里的href属性-->
    </div>
</body>

<script>
    new Vue({
        el: "#input_1",
        data: {
            url: "https://www.baidu.com"  //此处的url一修改，会影响以上的所有url变量
        }
    })
</script>
</html>


文本框里的链接一改变，那么<a>标签里的也会跟着变
```
### v-on
为标签绑定***事件***
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>v-on</title>
    <script src="JS/vue.js"></script>
</head>

<body>
    <div id="input_1">
		<input type="button" value="点击一下" v-on:click="handle"> //绑定handle方法
    </div>
</body>

<script>
    new Vue({
        el: "#input_1",
        methods: {    //声明方法结构体
            handle: function () {    //声明某个方法
                alert("我被点击了")
            }
        }
    })
</script>
</html>


点击按钮就会跳出警告框
```
### v-if，v-else if，v-else
条件性的渲染某元素
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>v-if测试</title>
    <script src="JS/vue.js"></script>
</head>

<body>
    <div>
        请输入你的年龄：<input type="text" v-model="age">
        <p>经判定你的年龄是：
            <span v-if="age<=35"><b>年轻人</b></span>
            <span v-else-if="age>35&&age<=60"><b>中年人</b></span>  //三个条件判断
            <span v-else="age>60"><b>老年人</b></span>
        </p>             //三个span只渲染一个
    </div>
</body>
<script>
    new Vue({
        el: "div",
        data: {
            age: 0
        }
    })
</script>
</html>


请输入你的年龄：age
经判定你的年龄是：年轻人
```
### v-show
不管条件成立与否都渲染，只是不成立的使用`display`来将其不显示
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>v-show</title>
    <script src="JS/vue.js"></script>
</head>

<body>
    <div id="age">
        <p>
            请输入你的年龄： <input type="text" v-model="age">
        </p>

        <p>
            经判定你的年龄是：
            <span v-show="age<=35"><b>年轻人</b></span>
            <span v-show="age>35&&age<=60"><b>中年人</b></span>
            <span v-show="age>60"><b>老年人</b></span>
        </p>               //三个span都渲染，通过display来指定显不显示
    </div>

</body>
<script>
    new Vue({
        el: "#age",
        data: {
            age: 0
        }
    })
</script>
</html>


<span><b>年轻人</b></span>
<span style="display: none;"><b>中年人</b></span>
<span style="display: none;"><b>老年人</b></span>
```
### v-for
列表渲染







# 生命周期


































