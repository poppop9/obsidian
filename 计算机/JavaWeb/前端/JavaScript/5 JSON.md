>JSON 是存储和传输数据的格式

# 🌕语法
```js
{         // 数据是键值对
	"age":18,         // 数据之间由逗号分隔
	"employees":[   // 方括号保存数组
	    {"firstName":"Bill", "lastName":"Gates"},    // 花括号保存对象
	    {"firstName":"Steve", "lastName":"Jobs"},
	    {"firstName":"Alan", "lastName":"Turing"}
	]
}
```
# 🌕JSON 与 JS对象
JSON 格式在语法上与创建 JS对象 的代码相同。所以，JavaScript 程序可以很容易地将 JSON 转换成本地的 JS对象

```js
//json
var jsonstr = '{"name":"吴彦祖","age":48,"isman":true,"works":["新警察故事","环游地球80天"]}';

//json转js对象
var obj = JSON.parse(jsonstr);
console.log(obj.name);

//js对象转json
var json = JSON.stringify(obj);
console.log(json);


---
吴彦祖
{"name":"吴彦祖","age":48,"isman":true,"works":["新警察故事","环游地球80天"]}
```






