> Ajax是异步的JavaScript和XML
- ***Ajax可以发送请求到服务器，并获取服务器的响应***
- ***Ajax还可以在不加载网页的情况下，实现实时更新网页的数据***

---

1. 网页中发生一个事件（页面加载、按钮点击）
2. 由 JavaScript 创建 XMLHttpRequest 对象
3. XMLHttpRequest 对象向 web 服务器发送请求
4. 服务器处理该请求
5. 服务器将响应发送回网页
6. 由 JavaScript 读取响应
7. 由 JavaScript 执行正确的动作（比如更新页面）

# XMLHttpRequest
>[!summary] 属性
>***readyState***  保存 XMLHttpRequest 的状态【0：请求未初始化；1：服务器连接已建立；2：请求已收到；3：正在处理请求；4：请求已完成且响应已就绪】
>
>***status***  返回请求的状态号【200: "OK"；403: "Forbidden"；404: "Not Found"】
>
>***responseText***	以字符串形式返回响应数据
# Axios
> Axios 对原生的 Ajax 进行了封装，简化了书写

https://www.axios-http.cn/docs/intro
## 安装Axios
### 工程化 Axios
- 在项目目录下的cmd输入 `npm install axios`
- 需要Axios时，在 `script标签` 中导入
```js
<script setup>
import axios from 'axios';
</script>
```

- 然后就可以在 `script标签` 中使用axios了
### 局部化 Axios
- 在 `head标签` 中导入 `axios.js` 文件
	```html
	<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
	```

- 然后就可以在 `script标签` 中使用axios了

## 使用与定义
>我们一般会把异步请求封装到一个单独的 `.js文件` 中，并暴露调用函数，这样在其他文件中可以直接调用，不用重复书写相同的 `axios代码`

```js
export function getHello() {

}
```

## 方法
### get
- `result` 服务器返回的所有数据【响应头，响应体】
- `result.data` 服务器返回的核心数据

---
- 不带参数的请求
```js
axios.get('http://localhost:8080/hello').then(res => {      // 处理成功情况
	alert(res.data);
}).catch(err => {          // 处理错误情况
	alert(err);
}).finally(function () {         // 总是会执行
	……
});
```
- 带明确参数的请求
```js
axios.get('http://localhost:8080/helloparam?id=1').then(result => {
	alert(result.data);
});
```
- 带变量参数的请求
```js
const msg2 = ref({
    id: 1,
    name: 'John'
});

axios.get('http://localhost:8080/helloparam', {
    params: {
        id: msg2.value.id,
        name: msg2.value.name
    }
}).then(res => {
    alert(res.data);
}).catch(err => {
    alert(err);
});
```

### post
```js
let jsondata = {
	id: 1,
	name: '张三'
};

axios.post('http://localhost:8080/hellojson', jsondata).then(result => {
	alert(result.data);
});
```
### delete
### put
## 同步与异步
### 同步
>`js代码` 与 `axios请求代码` 顺序执行，<u>使用</u> `async`，`await`

当需要等待请求结果来渲染页面时，那就需要***同步***：
```js
// hello.js
import axios from 'axios';

// 使用export暴露函数
export function hello(msg2) {   
	// 使用return返回结果
    return axios.get('http://localhost:8080/helloparam', {  
        params: {
            id: msg2.value.id,
            name: msg2.value.name
        }
    }).then(res => {
        return res.data;
    });
}
```

```js
// 需要等待请求结果之后再alert，如果是异步执行，那么将alert出来空数据
<script setup>
import { hello } from '@/api/hello.js';

// 定义数据
const msg2 = ref({
    id: 111,
    name: 'John'
});

// async定义异步函数，表示函数是异步的
const getData = async function() {
	// await定义同步，表示这行代码是同步的，这行代码不执行完，不会执行下一行
    const data1 = await hello(msg2);  	
    alert(data1);
};

getData();
</script>
```

>[!attention] `async` 是异步的意思，为什么用于==同步==呢
>由于 JavaScript 是赶工出来的语言，这是它的设计缺陷，`await` 必须在 `async` 定义的函数<u>里面才能使用</u>

## 公共路径baseURL
>如果每一个 `axios请求` 都包含完整的路径，那么后续改动时将非常麻烦，所以我们<u>会定义一个公共路径</u> `baseURL`

- ~~未定义~~ `baseURL`
```js
axios.get('http://localhost:8080/helloparam').then(result => {
	alert(result.data);
});
```

- 定义 `baseURL`
```js
// 定义基础路径
const baseURL = 'http://localhost:8080';
// 将基础路径作为js对象，传递给axios，拿到instance对象
const instance = axios.create({ baseURL });

// 使用instance对象
instance.get('/helloparam').then(result => {
	alert(result.data);
});
```



































