# 布局
## display
每个HTML元素都有一个默认的 display 值【具体取决于它的元素类型，大多数元素为`block`或`inline`】
### 块级元素 block
>总是从新行开始，并占据可用的全部宽度

>[!hint] 常见的块级元素标签
> - `<div>`
> - `<h1>` - `<h6>`
> - `<p>`
> - `<form>`
> - `<header>`
> - `<footer>`
> - `<section>`
### 行内元素 inline
>不从新行开始，仅占用所需的宽度

>[!hint] 常见的行内元素
> - `<span>`
> - `<a>`
> - `<img>`

```css
/* 可以将列表项横向展示 */
li {
  display: inline;
}
```
### 隐藏元素 none
默认情况下`<script>元素`使用`display: none;`

```css
/* 元素被隐藏，不会占用空间 */
h1.hidden {
  display: none;
}

/* 元素被隐藏，但仍然占用空间 */
h1.hidden {
  visibility: hidden;
}
```
## max-width
>`width` 当浏览器窗口小于元素的宽度时，浏览器会将水平滚动条添加到页面
>`max-width` 可以改善浏览器对小窗口的处理，当浏览器窗口小于元素的宽度时，会自动换行
## position
>[!hint] 属性值
> - `static`【默认】：不受 top、bottom、left 和 right 属性的影响，始终根据页面的正常流进行定位
> - `relative`：相对于其正常位置进行定位
> - `fixed`：相对于视口定位【意味着即使滚动页面，也始终位于同一位置】
> - `absolute`：相对于<u>最近的定位祖先元素</u>【除`static`】进行定位，如果没有祖先则祖先为整个文档主体`body`
> - `sticky`：根据用户的滚动位置进行定位【起先会被`relative`，而后为`fixed`】

```css
div.static {
  position: static;
  border: 3px solid #73AD21;
}

/* 左留30px，上留50px */
div.relative {
  position: relative;
  left: 30px;
  top: 50px;
  border: 3px solid #73AD21;
}

/* 始终位于右下角 */
div.fixed {
  position: fixed;
  bottom: 0;
  right: 0;
  width: 300px;
  border: 3px solid #73AD21;
}

div.absolute {
  position: absolute;
  top: 80px;
  right: 0;
  width: 200px;
  height: 100px;
  border: 3px solid #73AD21;
}

div.sticky {
  position: -webkit-sticky;    /* 为了匹配safari */
  position: sticky;
  top: 0;                /* 页面向下滚动时，将粘在页面的上方 */
  background-color: #cae8ca;
  border: 2px solid #4CAF50;
}
```
## 重叠
```css
/* 由于所有元素都设置了absolute，所以会重叠 */
<style>
h1 {
	position: absolute;
	color: red;
	z-index: 1;       /* h1的z-index最大，所以图层在最上面 */
}

p {                       /* p 和 img 未指定z-index，所以按照html的标签顺序自动指定，后面的元素后渲染 */
	position: absolute;
	color: red;                 
}

img {
	position: absolute;
}
</style>

<h1>这是标题</h1> 
<p>p1111111111111111111111111111111111111111111111</p> 
<img src="/i/logo/w3logo-1.png" width="188" height="267" /> 
<p>p2222222222222222222222222222222222222222222222</p>   
```












































