# 🌕准备工作

- 安装Element
  - 在工程目录下的 cmd 运行`npm i element-ui -S`
- 在`main.js`中引入Element组件库
	```js
	import ElementUI from 'element-ui';
	import 'element-ui/lib/theme-chalk/index.css';
	Vue.use(ElementUI);
	```
# 🌕导入组件
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
# 🌕常用组件
### 🌗Container 布局容器

### 🌗表格
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
### 🌗分页
```pagination_1.vue
<template>
    <div>
        <el-pagination background layout="prev, pager, next" :total="1000" />
    </div>
</template>
```
##### 🌗事件
```pagination_1.vue
<template>
    <div>
        <el-pagination background layout="prev, pager, next" :total="1000" @size-change="handleSizeChange" @current-change="handleCurrentChange" />  //绑定两个事件
    </div>
</template>

<script>
export default {
    data() {
        return {
        }
    },
    methods: {  //定义两个事件的触发方法
        handleSizeChange(val) {         //val是一个回调参数，表示每页条数
            console.log("每页" + val + "条");
        },
        handleCurrentChange(val) {       //val是一个回调参数，表示当前页码
            console.log("当前为" + val + "页");
        }
    }
}
</script>
```
### 🌗对话框
```dialog_1.vue
<template>
    <div>
        <el-button type="text" @click="dialogFormVisible = true">打开嵌套表单的 Dialog</el-button>

        <el-dialog title="收货地址" :visible.sync="dialogFormVisible">
            <el-form :model="form">
                <el-form-item label="活动名称" :label-width="formLabelWidth">
                    <el-input v-model="form.name" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="活动区域" :label-width="formLabelWidth">
                    <el-select v-model="form.region" placeholder="请选择活动区域">
                        <el-option label="区域一" value="shanghai"></el-option>
                        <el-option label="区域二" value="beijing"></el-option>
                    </el-select>
                </el-form-item>
            </el-form>
            <div slot="footer" class="dialog-footer">
                <el-button @click="dialogFormVisible = false">取 消</el-button>
                <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
            </div>
        </el-dialog>
    </div>
</template>

<script>
export default {
    data() {
        return {
            dialogFormVisible: false,
            form: {
                name: '',
                region: '',
                date1: '',
                date2: '',
                delivery: false,
                type: [],
                resource: '',
                desc: ''
            },
            formLabelWidth: '120px'
        };
    }
}
</script>
```
### 🌗表单
```dialogForm_1.vue
<template>
    <div>
        <el-form ref="form" :model="form" label-width="80px">
            <el-form-item label="活动名称">
                <el-input v-model="form.name"></el-input>
            </el-form-item>
            <el-form-item label="活动区域">
                <el-select v-model="form.region" placeholder="请选择活动区域">
                    <el-option label="区域一" value="shanghai"></el-option>
                    <el-option label="区域二" value="beijing"></el-option>
                </el-select>
            </el-form-item>
            <el-form-item label="活动时间">
                <el-col :span="11">
                    <el-date-picker type="date" placeholder="选择日期" v-model="form.date1"
                        style="width: 100%;"></el-date-picker>
                </el-col>
                <el-col class="line" :span="2">-</el-col>
                <el-col :span="11">
                    <el-time-picker placeholder="选择时间" v-model="form.date2" style="width: 100%;"></el-time-picker>
                </el-col>
            </el-form-item>
            <el-form-item label="即时配送">
                <el-switch v-model="form.delivery"></el-switch>
            </el-form-item>
            <el-form-item label="活动性质">
                <el-checkbox-group v-model="form.type">
                    <el-checkbox label="美食/餐厅线上活动" name="type"></el-checkbox>
                    <el-checkbox label="地推活动" name="type"></el-checkbox>
                    <el-checkbox label="线下主题活动" name="type"></el-checkbox>
                    <el-checkbox label="单纯品牌曝光" name="type"></el-checkbox>
                </el-checkbox-group>
            </el-form-item>
            <el-form-item label="特殊资源">
                <el-radio-group v-model="form.resource">
                    <el-radio label="线上品牌商赞助"></el-radio>
                    <el-radio label="线下场地免费"></el-radio>
                </el-radio-group>
            </el-form-item>
            <el-form-item label="活动形式">
                <el-input type="textarea" v-model="form.desc"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="onSubmit">立即创建</el-button>
                <el-button>取消</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
export default {
    data() {
        return {
            form: {
                name: '',
                region: '',
                date1: '',
                date2: '',
                delivery: false,
                type: [],
                resource: '',
                desc: ''
            }
        }
    },
    methods: {
        onSubmit() {
            console.log('submit!');
        }
    }
}
</script>
```











