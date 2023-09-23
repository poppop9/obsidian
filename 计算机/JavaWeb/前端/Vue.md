Vue 是一种流行的JavaScript前端框架，提供了一种响应式的双向数据绑定，***简化了DOM操作***
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
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>v-for</title>
    <script src="JS/vue.js"></script>
</head>

<body>
    <div id="list">
        <span v-for="e in list">{{e}}</span>  //第一种写法
        <br>
        <span v-for="(e, index) in list">{{index}}:{{e}}</span>
    </div>                      //第二种写法【加索引的】
</body>

<script>
    new Vue({
        el: "#list",
        data: {
            list: ["吴彦祖 ", "陈冠希 ", "郭富城"],
        }
    })
</script>
</html>
```
# 生命周期
生命周期：vue对象从创建到销毁的过程
### beforeCreate 创建前


### created 创建后

### beforeMount 载入前

### mounted 挂载完成
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>mounted</title>
    <script src="JS/vue.js"></script>
</head>

<body>
    <div id="div_1">

    </div>
</body>
<script>
    new Vue({
        el: "#div_1",
        mounted() {
            alert("Vue挂载完毕，发送请求到服务器获取数据")  
        }              //只要挂载div_1完成则执行mounted方法
    })
</script>
</html>


弹出警告框：Vue挂载完毕，发送请求到服务器获取数据
```
### beforeUpdate 更新前
### updated 更新后

### beforeDestroy 销毁前

### destroyed 销毁后
# 脚手架
### 安装前端环境Node.js
- 官网安装Node.js
- 验证Node.js环境变量
  - `node -v`
- 配置npm的全局安装路径
  - 以管理员身份运行cmd
  - 运行`npm config set prefix "安装目录"` 例如`npm config set prefix "D:\node.js"`。【成功不做任何操作】
  - 验证是否设置成功`npm config get prefix`。【成功则返回Node.js安装目录】
- 切换npm的淘宝镜像
  - `npm config set registry https://registry.npm.taobao.org`。【成功不做任何操作】
### 安装Vue的脚手架工具 vue-cli
- 在cmd中运行 `npm install -g @vue/cli`
- 确认是否安装成功
	- `vue --version`。【成功则返回版本号】
### 创建Vue项目
- 在cmd中输入`vue ui`
- 在UI界面中创建项目
### Vue项目的目录结构
- `node_modules` 整个项目的依赖包
- `public` 项目的静态文件
- `src` 项目的源代码
  - `assets` 静态资源
  - `components` 可重用组件
  - `router` 路由配置
  - `views` 视图组件
  - `App.vue` 入口页面【根组件】
    ```vue
    <template>          <!-- 模板代码，在此处定义原生HTML页面 -->
      <div id="app">
        <h1>{{ message }}</h1>
      </div>
    </template>
    
    <script>            //此处控制页面的行为
    export default {
      data() {
        return {
          message: "Hello Vue!"
        }
      }
    }
    </script>
    
    <style></style>
    ```
  - `main.js` 入口js文件
- `.gitignore`
- `babel.config.js`
- `jsconfig.json`
- `package-lock.json`
- `package.json` 基本信息，版本信息
- `vue.config.js` vue的配置文件【端口】
### 启动Vue项目
![[Excalidraw/计算机/JavaWeb.md#^group=KQ8yyjCW|400]]
### 修改端口号
```js
const { defineConfig } = require('@vue/cli-service')
module.exports = defineConfig({
  transpileDependencies: true,
  devServer: {
    port: 7000
  }
})
```
# Vue路由
>Vue路由可以使用户在应用程序中进行导航时，可以根据URL路径加载相应的组件
### 准备工作
##### 安装Vue Router
- 在安装Vue脚手架时勾选即可
- 如果没有勾选，则运行`npm install vue-router@3.5.1`
### VueRouter
>VueRouter是路由器类，里面维护了一张路由表【记录了URL的哈希片段与组件的对应关系】。它可以根据路由请求在路由视图中渲染出对应的组件
### \<router-link\>
>\<router-link\>是请求链接组件。它可以指定我们要访问的URL哈希片段
### \<router-view\>
>\<router-view\>是动态视图组件。在想要展示组件的地方放置标签即可




### 具体操作
##### 定义路由表
- 在`router`文件夹下的`index.js`文件中定义
```js
import Vue from 'vue'
import VueRouter from 'vue-router'

import HomeView from '../views/HomeView.vue'
import StaffView from '../views/root/StaffView.vue'  //导入组件
import AppView from '../App.vue'

Vue.use(VueRouter)

const routes = [
  {
    path: '/',
    redirect: '/staff'  //使用重定向，表示访问根目录时，把页面交给/staff
  },
  {
    path: '/staff',      //表示URL路径名
    name: 'staff',       //表示路由名
    component: StaffView     //表示上面导入的StaffView视图组件
  },
  {
    path: '/app',
    name: 'app',
    component: AppView
  }
]
```
##### 在片段组件中定义\<router-link\>
```vue
<el-menu-item index="1-1">
	<router-link to="/staff">员工页面</router-link>  //点击则跳转到/staff页面
</el-menu-item>
<el-menu-item index="1-2">
	<router-link to="/form_1">表单页面</router-link>
</el-menu-item>
```
##### 在App.vue中声明\<router-view\>
```vue
<template>
  <div id="app">
    <router-view />       <!--会根据路由请求自动切换页面组件-->
  </div>
</template>

<script>
export default {
  components: {}       //无需导入任何文件
};
</script>

<style></style>
```

















