>[!quote] sed 流编辑器
>sed 是一个非交互式的编辑器

sed 命令基本格式：

```bash
sed [参数]... [执行命令] [输入文件]...
# 形如：
$ sed -i 's/sad/happy/' test # 表示将test文件中的"sad"替换为"happy"
```

|参数|说明|
|---|---|
|`-n`|安静模式，只打印受影响的行，默认打印输入数据的全部内容|
|`-e`|用于在脚本中添加多个执行命令一次执行，在命令行中执行多个命令通常不需要加该参数|
|`-f filename`|指定执行 filename 文件中的命令|
|`-r`|使用扩展正则表达式，默认为标准正则表达式|
|`-i`|将直接修改输入文件内容，而不是打印到标准输出设备|

---

sed 执行命令格式：

```bash
[n1][,n2]command
[n1][~step]command
```

其中一些命令可以在后面加上作用范围，形如：

```bash
sed -i 's/sad/happy/g' test # g 表示全局范围
sed -i 's/sad/happy/4' test # 4 表示指定行中的第四个匹配字符串
```

其中 `n1,n2` 表示输入内容的行号，它们之间为 `,` 逗号则表示从 n1 到 n2 行，如果为 `~` 波浪号则表示从 n1 开始以 step 为步进的所有行；command 为执行动作，下面为一些常用动作指令：

| 命令  | 说明                    |
| --- | --------------------- |
| `s` | 行内替换                  |
| `c` | 整行替换                  |
| `a` | 插入到指定行的后面             |
| `i` | 插入到指定行的前面             |
| `p` | 打印指定行，通常与 `-n` 参数配合使用 |
| `d` | 删除指定行                 |

---

我们先找一个用于练习的文本文件：

```bash
cp /etc/passwd ~
```

#### 打印指定行

```bash
# 打印2-5行
nl passwd | sed -n '2,5p'
# 打印奇数行
nl passwd | sed -n '1~2p'
```

![此处输入图片的描述](https://doc.shiyanlou.com/document-uid735639labid354timestamp1532415685031.png)

#### 行内替换

```bash
# 将输入文本中"shiyanlou" 全局替换为"hehe"，并只打印替换的那一行，注意这里不能省略最后的"p"命令
sed -n 's/shiyanlou/hehe/gp' passwd
```

> 行内替换可以结合正则表达式使用。

#### 删除某行

```bash
nl passwd | grep "shiyanlou"
# 删除第30行
sed -i '30d' passwd
```

![图片描述](https://doc.shiyanlou.com/courses/uid600404-20191015-1571118544931)

关于 sed 命令就介绍这么多，你如果希望了解更多 sed 的高级用法，你可以参看如下链接：

- [sed 简明教程](http://coolshell.cn/articles/9104.html)
- [sed 单行脚本快速参考](http://sed.sourceforge.net/sed1line_zh-CN.html)
- [sed 完全手册](http://www.gnu.org/software/sed/manual/sed.html)

---
