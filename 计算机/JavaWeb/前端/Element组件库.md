# 准备工作

- 安装Element
  - 在工程目录下的 cmd 运行`npm i element-ui -S`
- 在`main.js`中引入Element组件库
	```js
	import ElementUI from 'element-ui';
	import 'element-ui/lib/theme-chalk/index.css';
	Vue.use(ElementUI);
	```
# 导入组件
- 在帮助文档中找到组件复制代码，粘贴到新建的`.vue`文件中
	```vue
	<template>
	    <div>
	        <el-row>
	            <el-button>默认按钮</el-button>
	            <el-button type="primary">主要按钮</el-button>
	            <el-button type="success">成功按钮</el-button>
	            <el-button type="info">信息按钮</el-button>
	            <el-button type="warning">警告按钮</el-button>
	            <el-button type="danger">危险按钮</el-button>
	        </el-row>
	    </div>
	</template>
	
	<script>
	export default {
	    data() {
	        return {
	
	        }
	    }
	}
	</script>
	
	<style></style>
	```
- 在根组件`App.vue`中导入刚刚组件的`.vue`文件
	```vue
	<template>
	  <div id="app">
	    <element-view></element-view>   //声明
	  </div>
	</template>
	
	<script>
	import ElementView from "./views/Element/vue_1.vue";  //导入刚刚创建的vue文件
	export default {
	  components: {        //声明
	    ElementView 
	  }
	};
	</script>
	
	<style></style>
	```

















