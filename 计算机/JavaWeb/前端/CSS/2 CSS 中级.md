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
> - static
> - relative
> - fixed
> - absolute
> - sticky















































