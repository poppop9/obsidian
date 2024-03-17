# 占位符
>为组件或页面使用加载占位符，以显示某些内容仍在加载中
>![150](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403171020883.png)

# 表单
## 禁用表单
>在 `<fieldset>标签`【功能是为表单分组】 添加 `disabled` 属性

```html
<form>
  <fieldset disabled>
    <legend>Disabled fieldset example</legend>
    <div class="mb-3">
      <label for="disabledTextInput" class="form-label">Disabled input</label>
      <input type="text" id="disabledTextInput" class="form-control" placeholder="Disabled input">
    </div>
    <div class="mb-3">
      <label for="disabledSelect" class="form-label">Disabled select menu</label>
      <select id="disabledSelect" class="form-select">
        <option>Disabled select</option>
      </select>
    </div>
    <div class="mb-3">
      <div class="form-check">
        <input class="form-check-input" type="checkbox" id="disabledFieldsetCheck" disabled>
        <label class="form-check-label" for="disabledFieldsetCheck">
          Can't check this
        </label>
      </div>
    </div>
    <button type="submit" class="btn btn-primary">Submit</button>
  </fieldset>
</form>
```

## \<input>
>在 `<input>` 标签中添加 `form-control`

- **类型**
	- `text` 单行输入字段
	- `password` 密码字段
	- `radio` 单选按钮
	- `checkbox` 复选框
	- `file` 文件上传
	- `date` 日期
	- `time` 时间
	- `month` 月份，年份
	- `week` 周，年
	- `color` 颜色
	- `range` 一个范围
	- `datetime-local` 日期＋时间
	- `number` 数字输入框
	- `email` 邮件输入框
	- `hidden` 隐藏域
	- `按钮` 
		- `submit` 提交按钮
		- `reset` 重置按钮【重置表单数据】
		- `button` 可点击按钮

>[!hint] 使用 `multiple` 属性，一次上传多个文件
> ```html
> \<label for="formFileMultiple" class="form-label">Multiple files input example\</label>
> \<input class="form-control" type="file" id="formFileMultiple" multiple>
> ```

>[!hint] 使用 `.form-control-color` ，优化颜色表单
> ```html
> \<input class="form-control form-control-color" type="color">
> ```

---

- **大小**
	- `form-control-lg`
	- 默认
	- `form-control-sm`

![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403171327820.png)
```html
// placeholder表示占位符
<input class="form-control form-control-lg" type="text" placeholder=".form-control-lg">
<input class="form-control" type="text" placeholder="Default input">
<input class="form-control form-control-sm" type="text" placeholder=".form-control-sm">
```

---

- **禁用**
	- `disabled`

![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403171331964.png)
```html
<input class="form-control" type="text" placeholder="Disabled input" disabled>
```

---

- **只读**
	- `readonly`

![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403171332192.png)
```html
<input class="form-control" type="text" value="Disabled readonly input" readonly>
```

---
## \<textarea>

```html
<div>
  <label for="exampleFormControlTextarea1" class="form-label">Example textarea</label>
  <textarea class="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
</div>
```

































