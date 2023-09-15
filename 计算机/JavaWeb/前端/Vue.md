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
        <input type="text" v-model="url">  <!--文本框
        <a v-bind:href="url">Go to</a>
    </div>
</body>

<script>
    new Vue({
        el: "#input_1",
        data: {
            url: "https://www.baidu.com"
        }
    })
</script>
</html>
```
### v-on
为标签绑定事件

### v-if，v-else if，v-else
条件性的渲染某元素

### v-show
根据条件展示某元素

### v-for
列表渲染







# 生命周期


































