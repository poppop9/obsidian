# 创建Vue项目
https://cn.vuejs.org/guide/quick-start.html
## npm 工程化
1. 进入打算创建项目的目录，运行 `cmd`
2. `npm create vue@latest`
3. 选择各种功能
4. 命名项目名称
5. `cd <your-project-name>` 进入项目
6. `npm install`
7. `npm run dev`
## CDN 局部化
`<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>`

# 局部使用
>局部使用 表示使用CDN来引入 `Vue`

- 使用 `{{……}}` 来插入数据
- 所有在html里用到的数据都要定义到 `data(){……}` 函数中
- 所有在html里用到的函数都要定义到 `method:{……}` 中
	- 在 `methods` 中要使用到 `data()函数` 中的数据时，***使用 `this` 关键字***

```html
<body>
	<div id="app">
		<h1>{{msg}}</h1>
		<button @click="handle">点击我</button>
	</div>
</body>

<script type="module">
	import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'   /* 导入 */

	createApp({       /* 使用 */
		data() {    /* 定义data函数插入数据 */
			return {      /* 使用return返回数据 */
				msg: "hello Vue3"      /* 定义数据 */
			}
		},
		methods: {
			handle: function(){
				this.msg="我被点击了";
			}
			……
		}
	}).mount('#app')    /* 挂载到某个html元素 */
</script>
```
## 常用指令
### v-for
>列表渲染，遍历<u>容器的元素/对象的属性</u>

- ***使用方法***：要让哪个标签循环展示多次，就在哪个标签上使用 `v-for`
- ***写法***
	- `item in items` item为数组元素，items为数组名
	- `(item, index) in items` index为索引

```html
<body>
	<div id="app">
		/* 无索引的遍历 */
		<span v-for="e in list">{{e}} &nbsp</span>
		<br>
		/* 有索引的遍历 */
		<span v-for="(e, index) in list">{{index}}: {{e}} &nbsp</span>
	</div>
</body>

<script type="module">
	import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'

	createApp({
		data() {
			return {    /* 准备数组 */
				list: ['吴彦祖', '郭富城', '张学友', '刘德华', '梁朝伟']
			}
		}
	}).mount('#app')
</script>


---
吴彦祖  郭富城  张学友  刘德华  梁朝伟    
0: 吴彦祖  1: 郭富城  2: 张学友  3: 刘德华  4: 梁朝伟
```
### v-bind
>为标签绑定***属性值***

- ***使用方法***：在需要属性值的标签内写上 `v-bind`
- ***写法***
	- `v-bind:属性名="属性值"`
	- `:属性值="属性值"`

```html
<body>
	<div id="app">
		<a v-bind:href="url">百度</a>
	</div>
</body>

<script type="module">
	import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'

	createApp({
		data() {
			return {
				url: 'https://www.baidu.com' /* 定义属性值 */
			}
		}
	}).mount('#app')
</script>
```
### v-model
> 为<u>表单元素</u>创建***双向***数据绑定

- ***语法***：`v-model="数据名"`

```html
<body>
    <div id="app">
        <input type="text" v-model="msg">
		<p>{{ msg }}</p>   /* 文本框的内容更改，这里也动态变化 */
    </div>
</body>

<script type="module">
    import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'

    createApp({
        data() {
            return {
                msg: 'Hello Vue 3!'
            }
        }
    }).mount('#app')
</script>
```
### v-on
>为标签绑定***事件***

- ***语法***
	- `v-on:事件名="函数名"`
	- `@事件名="函数名"`

```html
<body>
    <div id="app">
        <button @click="handle">点击我</button>
    </div>
</body>

<script type="module">
    import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'

    createApp({
        methods: {
            handle: function () {    //声明某个方法
                alert("我被点击了")
            }
        }
    }).mount('#app')
</script>
```
### v-if，v-else if，v-else
>条件性的渲染某元素

- ***语法***：`v-if="表达式"`

```html
<body>
    <div id="app">   /* 根据条件，三个span只渲染一个 */
        <span v-if="age<=35"><b>年轻人</b></span>
        <span v-else-if="age>35&&age<=60"><b>中年人</b></span>
        <span v-else="age>60"><b>老年人</b></span>
    </div>
</body>

<script type="module">
    import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'

    createApp({
        data() {
            return {
                age: 18
            }
        }
    }).mount('#app')
</script>
```
### v-show
>不管条件成立与否都渲染，只是不成立的使用`display`来隐藏

- ***语法***：`v-show="表达式"`

```html
<body>
    <div id="app"> 
		<span v-show="age<=35"><b>年轻人</b></span>
		<span v-show="age>35&&age<=60"><b>中年人</b></span>
		<span v-show="age>60"><b>老年人</b></span>
    </div>
</body>

<script type="module">
    import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'

    createApp({
        data() {
            return {
                age: 18
            }
        }
    }).mount('#app')
</script>


---
<span><b>年轻人</b></span>
<span style="display: none;"><b>中年人</b></span>
<span style="display: none;"><b>老年人</b></span>
```
## 生命周期
>生命周期 就是vue对象从创建到销毁的过程

>[!attention] 生命周期中的函数 与 `data()`， `methods{}` 同级

- `beforeCreate`：创建前调用
- `created`：创建后
- `beforeMount`：挂载前
- `mounted`：挂载后

```html
<body>
	……
</body>

<script type="module">
    import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'  

    createApp({     
        mounted() {
            alert("Vue挂载完毕，发送请求获取数据");
        }
    }).mount('#app')   
</script>
```

- `beforeUpdate`：数据更新前
- `updated`：数据更新后
- `beforeUnmount`：组件销毁前
- `unmounted`：组件销毁后

# 全局工程使用
## 脚手架
### 安装前端环境Node.js
- 官网安装Node.js【js的运行时环境】
- 验证Node.js环境变量
	- `node -v`
- 配置 <u>npm</u>【node.】的全局安装路径
	- 以管理员身份运行cmd
	- 运行`npm config set prefix "安装目录"` 例如`npm config set prefix "D:\node.js"`。【成功不做任何操作】
	- 验证是否设置成功`npm config get prefix`【成功则返回Node.js安装目录】
- 切换npm的淘宝镜像
	- `npm config set registry https://registry.npm.taobao.org`【成功不做任何操作】
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
![[JavaWeb Draw#^group=KQ8yyjCW|400]]
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