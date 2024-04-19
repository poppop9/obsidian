# 局部使用 Vue
## {{}}
>使用 `{{……}}` 来插入数据，或者<u>js表达式</u>

```js
<h1>{{ msg }}</h1>
<h1>{{ message.split('').reverse().join('') }}</h1>
```

- 所有在 html 里用到的数据都要定义到 `data(){……}` 函数中
- 所有在 html 里用到的函数都要定义到 `method:{……}` 中
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

# 全局工程使用 Vue
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
>- todos.value.push(newTodo) **给数组的末尾添加元素**
>- todos.value.filter(……) **根据条件过滤出数组**

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



































