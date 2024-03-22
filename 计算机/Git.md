
# 配置
## 三大配置文件
- `--system` 会读写 `/etc/gitconfig` 文件：影响<u>所有用户</u>的 Git 环境
- `--global` 会读写 `~/.gitconfig` 文件：对<u>当前用户</u>的<u>所有 Git 项目</u>生效
	- 如果在使用 git 命令时使用了 `--global`，那么更改的配置文件就是用户主目录下的那个，以后该用户所有的项目都会默认使用这里配置的用户信息
- `默认` 会读写当前工作目录中的 `.git/config` 文件：这里的配置仅仅针对<u>当前项目</u>有效

>[!hint] 每一个级别的配置都会覆盖上层的相同配置【例如，`.git/config` 里的配置会覆盖 `/etc/gitconfig`】

## 配置命令
- **查看配置信息**
	- 查看所有配置 `$ git config --list`
	- 查看某个配置 `$ git config user.name`
- 编辑配置文件 `$ git config -e` 

>[!hint] 有时候会看到重复的变量名，意味着它们来自不同的配置文件

---

- 配置提交代码时的用户名称和电子邮件地址
`$ git config --global user.name "runoob"`
`$ git config --global user.email test@runoob.com`

---

- 差异分析工具
```bash
# 比如要改用成 vimdiff 
$ git config --global merge.tool vimdiff
```

---


# 概念
## 工作流程
![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211816962.png)

- **克隆 Git 资源作为工作目录**：也就是“拉取”，克隆操作会创建一个与远程仓库同步的本地副本，包括所有的文件和版本历史记录
- **在克隆的资源上添加或修改文件**：你可以在本地工作目录中进行更改，而不会影响远程仓库
- **如果其他人修改了，你可以更新资源**
- **在提交前查看修改**：查看哪些文件被修改了，这可以帮助你确认所有的更改都是你想要提交的
- **提交修改**：会生成一个新的版本快照，并允许你为更改提供描述性的消息
- **在修改完成后，如果发现错误，可以撤回提交并再次修改并提交**

## 工作区，暂存区，版本库
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211830517.png)

>[!quote] 工作区
>你在电脑里能看到的目录

>[!quote] 暂存区 / index
>一般存放在 `.git` 目录下的 `index` 文件中

>[!quote] 版本库
>>是工作区中的一个隐藏目录 `.git`
>
>- `master`：是 master 分支所代表的目录树
>- `HEAD`：是指向 master 分支的一个"游标"【所以命令中出现 HEAD 的地方可以用 master 来替换】
>- `objects`：是 Git 的对象库，里面包含了创建的各种对象及内容

---

### 执行各种命令时，三区的变化
- 当对工作区修改的文件执行 `git add` 命令时，暂存区的目录树会被更新，同时工作区修改的文件内容被写入到 objects 中的一个新的对象中，而该对象的 ID 被记录在暂存区的文件索引中

- 当执行提交操作 `git commit` 时，暂存区的目录树会写到版本库的 objects 中，当前分支【~~通常是 master 分支~~】会指向新提交的目录树

- 当执行 `git reset HEAD` 时，暂存区的目录树会被重写【被 master 分支指向的目录树所替换（~~工作区不受影响~~）】

- 当执行 `git rm --cached <file>` 时，会删除暂存区文件【~~工作区不变~~】

- 当执行 `git checkout .` ，或者 `git checkout -- <file>` 时，会用暂存区全部，或指定的文件替换工作区的文件

- 当执行 `git checkout HEAD .` ，或者 `git checkout HEAD <file>` 时，会用 HEAD 指向的 master 分支中的全部，或者部分文件替换暂存区和以及工作区中的文件

# 创建仓库
## git init
>`git init` / `git init 指定目录` 会在 `.git 目录` 【包含了资源的所有元数据】中初始化一个 <u>Git 仓库</u>【在指定目录下】

如果当前目录下有几个文件想要纳入版本控制，需要先用 git add 命令告诉 Git 开始对这些文件进行跟踪，然后提交：
`$ git add *.c`
`$ git add README`
`$ git commit -m`

>[!warning]
>- 在 Linux 系统中，`commit` 的提交说明使用单引号 ' 
>- Windows 系统，`commit` 的提交说明使用双引号 "

## git clone
>>从现有 Git 仓库中拷贝项目
>- `git clone <repo>` 
>- `git clone <repo> 指定目录` 拷贝到指定的目录

```bash
$ git clone git://github.com/schacon/grit.git

# mygrit 是项目的目录名称
$ git clone git://github.com/schacon/grit.git mygrit
```

# 基本操作
![650](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211938641.png)

## 查看
- `git log` 查看<u>历史提交记录</u> / <u>克隆记录</u>【提交的哈希值，作者，提交日期，提交消息……】
	- `-p` 显示提交的补丁（具体更改内容）
	- `--oneline` 以简洁的一行格式显示提交信息
	- `--reverse` 以逆向的形式展示历史记录
	- `--graph` 以图形化方式显示分支和合并历史
	- `--decorate` 显示分支和标签指向的提交
	- `--author=<作者>` 只显示特定作者的提交
	- `--after=<时间>` 只显示指定时间之后的提交
	- `--before=<时间>` 只显示指定时间之前的提交
	- `--grep=<模式>` 只显示包含指定模式的提交消息
	- `--no-merges` 不显示合并提交
	- `--stat` 显示简略统计信息，包括修改的文件和行数
	- `--abbrev-commit` 使用短提交哈希值
	- `--pretty=<格式>` 使用自定义的提交信息显示格式

```bash
$ git log 属性 [分支名/提交哈希]

# 以简洁的形式显示最近的5个提交历史记录，其中作者为"Linus"
git log --author=Linus --oneline -5

# 根据日期体以简洁的方式，显示非合并提交
$ git log --oneline --before={3.weeks.ago} --after={2010-04-18} --no-merges
```



---




- `git blame <file>` 以列表形式查看指定文件的历史修改记录









- 查看仓库状态
	- `git status` 查看仓库当前的状态，显示有变更的文件
	- `git diff` 比较文件的不同，即暂存区和工作区的差异





## 提交与修改
### 工作区操作
- `git add` 将添加文件到暂存区
	- `git add .` 表示将当前工作目录中所有已修改或新增的文件都添加到 Git 的暂存区中
- `git commit` 提交暂存区到本地仓库
	- `git commit -m '第一次版本提交'` 添加提交信息
- `git reset` 回退版本
- `git rm` 将文件从暂存区和工作区中删除
- `git mv` 移动或重命名工作区文件
- `git restore` 恢复或撤销文件的更改

### 远程操作
- `git remote` 远程仓库操作
- `git fetch` 从远程获取代码库
- `git pull` 下载远程代码并合并
- `git push` 上传远程代码并合并

# 分支管理
>[!quote] 分支
>>分支是指向更改快照的指针。一个分支代表一条独立的开发线，使用分支表示你可以从主线上分离开来，然后在不影响主线的同时继续工作
>
>所以删除一个分支并不会丢失历史记录或更改，删除分支只是移除了那个指向特定提交的指针，这样可以保持分支列表的整洁

---

- `git branch` **列出分支**：没有参数时，会列出当前分支

---

- `git branch 分支名` **创建分支**

---

- `git branch -d 分支名` **删除分支**

---

- `git checkout 分支名` **切换分支**：Git 会查找目标分支最后一次提交时的快照，并将你的工作目录中的文件更新为该快照中的内容

---

- `git merge` **合并分支**：可以将一个分支多次合并到统一分支，如果被合并的分支没用了可以删除

```bash
# 将分支合并后，test.txt 就被删除了
$ git branch
* master
  newtest

$ ls
README        test.txt

$ git merge newtest
……

$ ls
README        runoob.php
```

---

## 合并冲突
>合并冲突 指的是在两个分支上对同一文件的同一部分进行了不同的修改，导致 Git 无法自动合并这些更改，需要手动修改这个文件，然后再 `git add 这个文件`

```bash
# UU 表示该文件有未解决的合并冲突
$ git status -s
UU runoob.php

$ git add runoob.php

# M 表示`runoob.php`文件已经被修改，不处于合并冲突状态
$ git status -s
M  runoob.php

$ git commit
[master 88afe0e] Merge branch 'change_site'
```


# 拉取
- ![300](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211339240.png)
- 拉取别人仓库![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211342220.png)
- 拉取自己账号里的仓库![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211340541.png)
- 选择拉取到本地的地址![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211340313.png)

# 提交
![300](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211648397.png)







# 推送
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211649783.png)



































