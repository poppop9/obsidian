
>[!quote] Sass
>Sass 是一个 CSS 预处理器，增加了<u>规则、变量、混入、选择器、继承、内置函数</u> …… ，可以帮助我们减少 CSS 重复的代码
>- 文件后缀为 `.scss`

# 🌞安装
- NPM 安装 `npm install -g sass`

# 🌞变量
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
 
# 🌞嵌套
很多 CSS 属性都有同样的前缀，例如：`font-family` , `font-size` ，`font-weight` ，`text-align` , `text-transform` ，`text-overflow`

---

- 例 1
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
// 以上代码等价于以下css代码
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
```

- 例 2
```css
font: {
  family: Helvetica, sans-serif;
  size: 18px;
  weight: bold;
}

text: {
  align: center;
  transform: lowercase;
  overflow: hidden;
}

---
font-family: Helvetica, sans-serif;
font-size: 18px;
font-weight: bold;

text-align: center;
text-transform: lowercase;
text-overflow: hidden;
```

# 🌞导入文件
- **完整导入文件**【~~没有下划线前缀的 Sass 文件~~】：它们可以被 Sass 编译器直接编译成 CSS 文件。~~例如，如果你有一个 styles.scss 文件，Sass 编译器会将其编译成 styles.css~~
- **部分导入文件**【~~带有下划线前缀的 Sass 文件~~】：它们是用来被其他 Sass 文件导入的，不需要被编译为 CSS 文件。~~例如，如果你有一个 `_variables.scss` 文件，你可以在其他 Sass 文件中通过 `@import 'variables';` 来导入它~~

>[!warning] 不要将带下划线与不带下划线的同名文件放置在同一个目录下
>比如，`_colors.scss` 和 `colors.scss` 不能同时存在于同一个目录下，<u>否则带下划线的文件将会被忽略</u>

## 🔸完全导入文件
`@import filename;` @import 指令可以让我们导入其他文件的内容，导入后我们就可以在主文件中使用导入文件的变量

>[!warning]
>- 包含文件时不需要指定文件后缀，Sass 会自动添加后缀 `.scss`
>- 可以导入 CSS 文件

---

- 例子
```css
// 导入 variables.scss、colors.scss 和 reset.scss 文件
@import "variables";
@import "colors";
@import "reset";
```

## 🔸部分导入文件
有时我们不想某个 `.scss` 文件被编译为 `.css` ，而是作为一个导入文件，导入到其他 Sass 文件中，我们就可以将这个 `.scss` 文件以下划线开头，例如 `_temp.scss`

```css
// 这是_colors.scss 文件
$myPink: #EE82EE;
$myBlue: #4169E1;
$myGreen: #8FBC8F;
```

```css
// 在其他文件中导入_colors.scss文件
@import "colors";

body {
  font-family: Helvetica, sans-serif;
  font-size: 18px;
  color: $myBlue;
}
```




### 🔹你好

#### 你好

🌕🌖🌗🌘🌑☀🌞⭐🌟


🔶🔸🔷🔹🔺🔻🔲🔳

