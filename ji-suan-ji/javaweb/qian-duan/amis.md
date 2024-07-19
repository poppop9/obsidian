---
description: https://aisuda.bce.baidu.com/amis/zh-CN/docs/index  这是百度的低代码框架，使用 JSON 来生成页面
---

# amis



## 配置与组件

每一个配置都必须有 `type` ，表示要渲染的是什么，`type` 的值可以取：

* page
* ……



### page

如果 `type` 是 page，那就要有 `body` 属性，表示 page 的值

```json
 {
  "type": "page",
  "body": "Hello World!"
}
```
