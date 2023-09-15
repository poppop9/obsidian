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
```
### v-on
为标签绑定***事件***
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vue版本的切换图片</title>
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
```
### v-if，v-else if，v-else
条件性的渲染某元素

### v-show
根据条件展示某元素

### v-for
列表渲染







# 生命周期


































