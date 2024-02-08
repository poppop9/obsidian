Vue 是一种流行的JavaScript前端框架，提供了一种响应式的双向数据绑定，***简化了DOM操作***

# Vue路由
>Vue路由可以使用户在应用程序中进行导航时，可以根据URL路径加载相应的组件
## 准备工作
### 安装Vue Router
- 在安装Vue脚手架时勾选即可
- 如果没有勾选，则运行`npm install vue-router@3.5.1`
## 三大核心
### VueRouter
>VueRouter是路由器类，里面维护了一张路由表【记录了URL的哈希片段与组件的对应关系】。它可以根据路由请求在路由视图中渲染出对应的组件
### \<router-link\>
>\<router-link\>是请求链接组件。它可以指定我们要访问的URL哈希片段
### \<router-view\>
>\<router-view\>是动态视图组件。在想要展示组件的地方放置标签即可
## 具体操作
### 定义路由表
- 在`router`文件夹下的`index.js`文件中定义
```js
import Vue from 'vue'
import VueRouter from 'vue-router'

import HomeView from '../views/HomeView.vue'
import StaffView from '../views/root/StaffView.vue'   //导入组件
import form_1View from '../views/Element/form_1.vue'

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
    path: '/form_1',
    name: 'form_1',
    component: form_1View
  }
]
```
### 在组件中定义\<router-link\>
```vue
<el-menu-item index="1-1">
	<router-link to="/staff">员工页面</router-link>  //点击则跳转到/staff页面
</el-menu-item>
<el-menu-item index="1-2">
	<router-link to="/form_1">表单页面</router-link>
</el-menu-item>
```
### 在App.vue中声明\<router-view\>
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
# 打包部署
## 打包
- 运行npm脚本中的`build`
![[JavaWeb Draw#^group=2bfxmrHr]]
- 打包好的文件会出现在`dist`文件夹下

***dist文件夹就是打包后的文件***
## 部署
- 在nginx网站`https://nginx.org/en/download.html`下载稳定版
- 将打包好的`dist`下面的内容放置到`html`文件夹中
- 运行nginx
	- 默认端口号为80，如果端口被占用则在`conf`文件夹下的`nginx.conf`中的`listen 80;`处修改端口号
- 如果在任务管理器中查看到nginx已经启动了，那就表示已经部署成功
- 可以在浏览器输入`localhost:端口号`
### 介绍nginx的安装目录
- `conf` 配置文件
- `contrib` 
- `docs`
- `html` 静态资源文件【放置打包好的文件】
- `logs` 日志文件
- `temp` 临时文件











