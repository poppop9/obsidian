
>[!quote] Sass
>Sass 是一个 CSS 预处理器，增加了<u>规则、变量、混入、选择器、继承、内置函数</u> …… ，可以帮助我们减少 CSS 重复的代码
>- 文件后缀为 `.scss`

# 安装
- NPM 安装 `npm install -g sass`

# 变量
>[!hint] 
>- Sass 变量可以存储以下信息：
> 	- 字符串
> 	- 数字
> 	- 颜色值
> 	- 布尔值
> 	- 列表
> 	- null 值
> 
> - Sass 变量以 `$` 开头

```css
$myFont: Helvetica, sans-serif;
$myColor: red;
$myFontSize: 18px;
$myWidth: 680px;

body {  
  font-family: $myFont;  
  font-size: $myFontSize;  
  color: $myColor;  
}  
  
#container {  
  width: $myWidth;  
}
```

>[!hint] 变量的作用域
>- 默认作用域为同一层级
> ```css
> $myColor: red;
> 
> h1 {
>   // 只在 h1 里有用，局部作用域
>   $myColor: green;   
>   color: $myColor;   // 为green
> }
> 
> p {
>   color: $myColor;   // 为red
> }
> ```
> 
>- 可以使用 `！global` 来设置某个变量为<u>全局变量</u>【一般定义在一个单独的 `_global.scss` 文件中，再使用 `@include` 引入】
> ```css
> $myColor: red;
> 
> h1 {
>   // 设置myColor变量为全局变量
>   $myColor: green !global;
>   color: $myColor;  // 为green
> }
> 
> p {
>   color: $myColor;  // 为green
> }
> ```
 
# 嵌套
很多 CSS 属性都有同样的前缀，例如：`font-family` , `font-size` ，`font-weight` ，`text-align` , `text-transform` ，`text-overflow`

```css
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  li {
    display: inline-block;
  }
}

---
// 以上代码等价于
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
```





















