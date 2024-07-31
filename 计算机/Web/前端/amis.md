amis 是百度的低代码框架，使用 JSON 来生成页面
https://aisuda.bce.baidu.com/amis/zh-CN/docs/index



# ❤️ 配置与组件

每一个配置都必须有 `type` ，表示要渲染的是什么，`type` 的值可以取：

- page 页面

- divider 分割线

- form 表单

  - select 下拉框

  - input-date-range 时间范围



## page

如果 `type` 是 page，那就要有 `body` 属性，表示 page 的值

```json
{
  "type":"page",
  "body":"Hello World!"
}
```





## form

- `form` 同级
  - `target` 表单提交的路径
  - `submitOnChange` 修改时是否直接提交表单

- `form` 子级的表单元素
  - `input-text` 输入框
  - `select` 下拉框
    - label 标签
    - name 表单提交时的 key
    - selectFirst 默认选择项是否是第一个
    - mode
    - options 下拉框的选项
  - `input-data-range` 时间范围
    - value
    - inputFormat 显示的时间格式，`YYYY-MM-DD`
    - format 提交的时间格式





