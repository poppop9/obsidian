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

```html
<body>
	<div id="app">
		<h1>{{msg}}</h1>
	</div>
</body>

<script type="module">
	import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'   /* 导入 */

	createApp({       /* 使用 */
		data() {    /* 定义data函数插入数据 */
			return {      /* 使用return返回数据 */
				msg: "hello Vue3"      /* 定义数据 */
			}
		}
	}).mount('#app')    /* 挂载到某个html元素 */
</script>
```
## 常用指令
### v-for
>列表渲染


### v-bind





# 工程使用