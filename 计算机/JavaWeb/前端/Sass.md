
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

```sass
$myFont: Helvetica, sans-serif;
$myColor: red;
$myFontSize: 18px;
$myWidth: 680px;

```