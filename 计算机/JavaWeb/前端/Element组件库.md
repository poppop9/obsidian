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
# 常用组件
### 表格
```table_1.vue
<template>
    <div>
        <el-table :data="tableData" style="width: 100%">
            <el-table-column prop="date" label="日期" width="180">
            </el-table-column>
            <el-table-column prop="name" label="姓名" width="180">
            </el-table-column>
            <el-table-column prop="address" label="地址">
            </el-table-column>
        </el-table>
    </div>
</template>

<script>
export default {
    data() {
        return {
            tableData: [{          
                date: '2016-05-02',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1518 弄'
            }, {
                date: '2016-05-04',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1517 弄'
            }, {
                date: '2016-05-01',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1519 弄'
            }, {
                date: '2016-05-03',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1516 弄'
            }]
        }
    }
}
</script>
```
```App.vue
<template>
  <div id="app">
    <vue_1Vue />
    <table_1Vue />      //声明
  </div>
</template>

<script>
import vue_1Vue from "./views/Element/vue_1.vue";
import table_1Vue from "./views/Element/table_1.vue";    //导入

export default {
  components: {
    vue_1Vue, table_1Vue       //导入
  }
};
</script>

<style></style>
```
### 分页
```pagination_1.vue
<template>
    <div>
        <el-pagination background layout="prev, pager, next" :total="1000" />
    </div>
</template>
```
##### 事件














