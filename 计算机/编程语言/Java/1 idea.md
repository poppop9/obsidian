
# ❤ 设置
- 编辑器 - 常规 - 编辑器标签页 - 在以下位置显示标签页 - 多行


# ❤ 快捷键
## 生成语句
快速生成 main() 方法 `psvm`
生成输出语句 `sout`
get ,set 方法，构造方法 `alt+insert`
生成左边对象 `ctrl+alt+v` / 在对象后面输入 `.var`

## 快捷操作
- **编辑**
	- 单行注释 `ctrl+/`
	- 多行注释 `ctrl+shift+/`
	- 格式化代码 `ctrl+alt+L`
	- 批量选中相同代码 `shift+F6` 
	- `ctrl+shift+↑` 将光标所在行上移
	- `ctrl+d` 将光标所在代码行复制到下一行
	- `ctrl+w` 扩展选中区域
	- `ctrl+shift+w` 减小选中区域
	- `ctrl+alt+o` 删除没有使用的导包

---

- **查看**
	- 在左侧的文件目录窗口，直接键盘输入就可以搜索类
	- `ctrl+p` 在调用方法时，提示需要传入的参数类型
	- `ctrl+B` 查看源码
	- `ctrl + alt + ←` 返回上一个类
	- `ctrl + alt + →` 返回下一个类
	- 查看类的结构信息 `alt+7`
	- 查看某个类的所有方法 `ctrl+f12`
	- 查看接口的所有实现类 `ctrl+alt+左键` 

---

- **搜索**
	- `ctrl+F` 在当前类中，进行搜索
	- `shift + shift` 全局搜索
	- `ctrl+r` 在该文件中搜索

---

- **调试，运行**
	- 运行代码 `ctrl+shift+F10`

# ❤ Debug
- `F7` 步入
- `shift+F7` 智能步入，~~当一行上有多个方法时，可以自己选择要步入的方法~~
- `F8` 步过
- `shift+F8` 步出，从当前方法中步出，退出到方法调用处
- `F9` 运行到该类的下一个断点，如果没有断点，就跳出断点，继续运行
- `ALT + F9` 运行到鼠标光标处
- `ctrl+shift+F9` 重新编译

>[!hint] 小 Tips
>调试时 ：
>- 如果新增了类，或者改动了继承关系，就要重启项目才能继续调试
>- 其他情况，可以重新编译项目，再继续调试

## 条件断点
设置条件断点后，只有当条件符合，才会 debug 住，否则会继续往下执行
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202409022212739.png)

## 异常断点
设置异常断点后，只要那一行代码会报这个异常，代码就会停在哪一行
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202409022210239.png)

# ❤ 插件
- `Mybatis`
- 中文简体
- `leetcode editor` 在 idea 里做题
- `Thief-book` 摸鱼神器【在终端看书】
- `sequence diagram` 右键某个类，查看方法的代码流程
- `codeGlance pro` 右上角的小地图















