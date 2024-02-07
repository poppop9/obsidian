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
	<div id="app">{{ message }}</div>
</body>

<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
	const { createApp, ref } = Vue

	createApp({
		setup() {
				const message = ref('Hello vue!')
				return {
						message
				}
		}
	}).mount('#app')
</script>
```



# 工程使用