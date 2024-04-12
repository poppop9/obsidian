# 文件路径
[[1 HTML 初级#文件路径]]

补充：
`@/api/hello.js` 位于src文件夹下的api文件夹下的hello.js文件

# 创建Vue项目
https://cn.vuejs.org/guide/quick-start.html
## npm 工程化
### 安装前端环境Node.js
- 官网安装Node.js【js的运行时环境】
- 验证Node.js环境变量
	- `node -v`
- 配置 <u>npm</u>【node.js 的软件包管理器】的全局安装路径
	- 以管理员身份运行cmd
	- 运行`npm config set prefix "安装目录"` 例如`npm config set prefix "D:\node.js"`。【成功不做任何操作】
	- 验证是否设置成功`npm config get prefix`【成功则返回Node.js安装目录】
- 切换npm的淘宝镜像
	- `npm config set registry https://registry.npm.taobao.org`【成功不做任何操作】
### 创建Vue项目
1. 进入打算创建项目的目录，运行 `cmd`
2. `npm create vue@latest`
3. 选择各种功能
4. 命名项目名称
5. `cd <your-project-name>` 进入项目
6. `npm install`
7. `npm run dev`/在VSCode的NPM脚本中点击`dev`  ***启动Vue项目***
### Vue项目的目录结构
- `node_modules` 项目下载的第三方依赖包
- `public` 项目的静态文件
- `src` 项目的源代码
	- `assets` 静态资源【图片，字体…】
	- `components` 可重用组件
	- `router` 路由配置
	- `App.vue` 入口页面【根组件】
	- `main.js` 入口文件
- `.gitignore`
- `index.html` 默认首页
- `package-lock.json` 项目配置文件【无需修改，会自动生成】
- `package.json` 项目配置文件【基本信息，版本信息，依赖包】
- `vite.config.js` vue的配置文件【端口】
## CDN 局部化
`<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>`

# 局部使用Vue
>局部使用 表示使用CDN来引入 `Vue`
## {{}}
>使用 `{{……}}` 来插入数据，或者<u>js表达式</u>
```js
<h1>{{ msg }}</h1>
<h1>{{ message.split('').reverse().join('') }}</h1>
```

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
	- `v-for="item in items" :key="item.id"` item为数组元素，items为数组名，`:key` 是给每个数组元素绑定一个id值【***最好是items里唯一的值***】，让vue可以顺利的遍历
	- `v-for="(item, index) in items" :key="item.id"` index为索引

```html
<body>
	<div id="app">
        <table>
            <tr v-for="data in tabledata" :key="data.id">
                <td>{{ data.id }}</td>
                <td>{{ data.name }}</td>
                <td>{{ data.age }}</td>
            </tr>
        </table>
	</div>
</body>

<script type="module">
	import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'

	createApp({
		data() {
			return {    /* 准备数组 */
				const tabledata = [
				    { id: 1, name: 'John', age: 30 },
				    { id: 2, name: 'Paul', age: 20 },
				    { id: 3, name: 'George', age: 40 },
				    { id: 4, name: 'Ringo', age: 25 }
				];
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
	- `:属性名="属性值"`

#### 绑定单个属性值
```html
<body>
	<a v-bind:href="url">百度</a>
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

```html
<!-- {}表示一个对象，因为style里有很多属性，所以每一个都要加，Homepage是一个动态数据变量 -->
<div v-bind:style="{ display: Homepage }">
  <TeaHomepage />
</div>

<script setup>
const Homepage = ref('block');

function homepage() {
  Homepage.value = 'block';
}
</script>
```

#### 绑定多个属性值
```js
<div :class="['alert', 'alert-' + alert.type, 'alert-dismissible']"></div>

const alerts = ref([
        message: 'Nice, you triggered this alert message!',
        type: 'success'
]);


---
<div class="alert alert-success alert-dismissible"></div>
```

### v-model
> 为<u>表单元素</u>创建**双向**数据绑定

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

# 全局工程使用Vue
>[!attention] 注意
>- 在全局使用Vue时，导入数据不能使用 `createApp` ，因为 `createApp` 创建Vue实例，而Vue实例已经在<u>入口文件</u> `main.js` 里面创建过了
>- 在全局使用Vue时，方法里要访问响应式数据，不用写 `this` 关键字

>[!hint] 最终呈现在用户面前的是 `index.html` ，而 `index.html` 里导入了 `main.js` ，`main.js` 里面又导入了 `App.vue` ，***所以，如果想要所写的 `.vue文件` 在页面显示的话，要在 `App.vue` 中导入所写的 `.vue文件`，并在 `<template>` 中写入导入的 `.vue文件`***
## 模板
- `<script setup>` 必须指定
	- 从已经下载的 `vue` 文件中导入<u>各种函数</u>
	- 使用 `ref()` 定义**响应式变量**，`ref()` 会返回一个对象，这个对象的有一个指向内部值的属性 `value`
	- 定义方法可以直接定义，**不需要在 `methods` 里面**
	- 钩子方法使用 `onMounted()`
- `<template>` html代码
- `<style>` css代码

```html
<script setup>    /* 必须指明setup */
import { onMounted, ref } from 'vue';   /* 从vue中导入ref()函数，onMounted()函数 */

const count = ref(0);      /* 使用ref()函数定义响应式变量 */

function increment() {
    count.value++;    /* 在方法中使用count，需要.value拿到值 */
}

onMounted(() => {
    alert('mounted!');
});
</script>

<template>
    <div>
        <h1>{{ count }}</h1>     <!--在<template>里使用变量不需要.value -->
        <button @click="increment">Increment</button>
    </div>
</template>

<style></style>
```

# 如何操作数据
## 数组
>[!hint] 方法
>>此处 `todos` 为数组，`todo` 为数组元素
>- todos.value.push(newTodo) ***给数组的末尾添加元素***
>- todos.value.filter(……) ***根据条件过滤出数组***

```js
const todos = ref([
  { id: id++, text: 'Learn HTML' },
  { id: id++, text: 'Learn JavaScript' },
  { id: id++, text: 'Learn Vue' }
])

---
todos.value.push({ id: id++, text: newTodo.value })

---
function removeTodo(todo) {
  todos.value = todos.value.filter((todos) => todos !== todo)
}
```

## 动态赋值computed()
>可以响应式地根据某个表达式，来响应式地赋值

```js
// hideCompleted是个动态数据，根据这个值，使用三元运算符来动态返回数据，并使用返回地数据定义filteredTodos
const filteredTodos = computed(() => {
  return hideCompleted.value    
    ? todos.value.filter((todo) => todo.done===false)
    : todos.value
})
```


# 组件库
## BootStrap
[[1 Bootstrap 初级]]
## Element+
- 安装： https://element-plus.org/zh-CN/guide/installation.html
- 引入： https://element-plus.org/zh-CN/guide/quickstart.html
- 组件： https://element-plus.org/zh-CN/component/button.html




































