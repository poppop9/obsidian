# Obsidian 特殊语法

## 层次分类

```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
- 五级标题
```

## 文字的特殊形式

### 引用

> 答案，解释

### 多行代码块

```
用于答案,代码
```

### 单行代码块

`用于提炼出多行代码块的内容，进行逐行分析`

### 斜粗体

_**用于重点**_

### 脚注

脚注

### 高亮

\==非常重点== _==粉色高亮==_ **==绿色高亮==** _**==蓝色高亮==**_

### 标签（#问题）

## 快捷键

* 新建笔记`ctrl+n`
* 搜索笔记`ctrl+o`
* 在当前笔记中搜索`ctrl+f`
* 管理工作区`ctrl+w`
* 打开命令面板`ctrl+p`
* 切换编辑/阅读视图 `alt+v`
* `shift + ←` 向左选中文字
* `shift + →` 向右选中文字

***

* 一级标题`ctrl+1`
* 二级标题`ctrl+3`
* 三级标题`ctrl+5`

***

* 黄色背景`ctrl+h`
* 蓝色背景`ctrl+l`

***

* 粗体`ctrl+b`
* 斜体`ctrl+i`
* 删除线`ctrl+d`
* 批量引用`ctrl+q`
* 清除格式 `ctrl+e`
* 引用`ctrl+q`
* 插入链接`ctrl+k`
* 无序列表`ctrl+l`

***

* excalidraw里拷贝内部链接 `ctrl+shift+k`

## 妙招

### 多个空格

只有一个 空格 我有多个      空格

### 内嵌查询

```query
tag:问题
```

### 多光标协同

如果你按住 `alt`（mac 上是 `option` ）并点击，你将可以创建多个光标

```
比如，你可以通过这种方式式同时在几行内容之前加上`-`，从而将它们快速地变为列表。
```

### Callout
> [!quote] 用来编写概念

> [!example] 描述例子

> [!bug] 描述 bug

> [!summary] 进行小结；描述类或接口中的方法

> [!faq] 描述问题

> [!hint] 额外说明，提示

>[!warning] 注意

> [!done]

> [!fail]

> [!error]

> [!note]

> [!todo]

> [!info]

| 属性名称                                                                                                                           | 解释                  |
| ------------------------------------------------------------------------------------------------------------------------------ | ------------------- |
| nowrap                                                                                                                         | 元素不换行(包括图片横排带滚动条显示) |
| noicon                                                                                                                         | 隐藏callout图标         |
| banner                                                                                                                         | 可以用图片作为callout标题    |
| notitle                                                                                                                        | 隐藏callout标题栏        |
| noborder                                                                                                                       | 隐藏callout边框         |
| grip                                                                                                                           | 图片横排不带滚动条显示         |
| ### 自定义标题                                                                                                                      |                     |
| 环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕环绕 |                     |

> [!tip right indent 70%]- 这里可以自定义标题 我是indent缩进我是indent缩进我是indent缩进我是indent缩进我是indent缩进我是indent缩进我是indent缩进我是indent缩进我是indent缩进我是indent缩进我是indent缩进
>
> * 可以放进列表
> * 最后加个-可以折叠
> * 改左右对齐显示；
> * 控制宽度百分比%
> * 让文字环绕显示【打开阅读视图】


## 插件

_**Better footnote**_ 阅读视图时，脚注可以鼠标悬浮显示

_**Commander**_ 控制在侧边栏，底部，各处的按钮

_**Dataview**_ 对数据的处理

_**Editing Toolbar**_ 悬浮的快捷编辑栏

_**Excalidraw**_

_**Image auto upload Plugin**_ 图床

_**Keyboard Analyzer**_ 查看各种键的快捷键

_**Make.md**_ 文件管理器

_**Mousewheel Image zoom**_ 鼠标滚轮控制图片大小

_**Obsidian Git**_ git来备份文件

_**Recent Files**_ 显示最近文件

_**Remotely Save**_ 远程通过webdev备份文件

_**Setting Search**_ ob的原生搜素不全面，这个设置搜索好用

_**Style Settings**_ 对于主题的css设置

### Code Styler
* 代码块添加标题
```ts
import { defaultTheme } from '@vuepress/theme-default'
import { defineUserConfig } from 'vuepress'

export default defineUserConfig({
  title: '你好， VuePress',

  theme: defaultTheme({
    logo: 'https://vuejs.org/images/logo.png',
  }),
})
```

* 行号 `ln:false/true`

```java
aaa
```

* 代码行高亮
  * `hl:1` 单行
  * `hl:1-3` 范围

```java
1-2 行高亮
aaa
sss
```
