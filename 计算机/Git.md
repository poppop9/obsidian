# 配置
## 三大配置文件
- `--system` 会读写 `/etc/gitconfig` 文件：影响<u>所有用户</u>的 Git 环境
- `--global` 会读写 `~/.gitconfig` 文件：对<u>当前用户</u>的<u>所有 Git 项目</u>生效
	- 如果在使用 git 命令时使用了 `--global`，那么更改的配置文件就是用户主目录下的那个，以后该用户所有的项目都会默认使用这里配置的用户信息
- `默认` 会读写当前工作目录中的 `.git/config` 文件：这里的配置仅仅针对<u>当前项目</u>有效

>[!hint] 每一个级别的配置都会覆盖上层的相同配置【例如，`.git/config` 里的配置会覆盖 `/etc/gitconfig`】

## 配置相关命令
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
>- `HEAD`：是指向 master 分支的一个"游标"，**它指向了分支最新提交的那个结点**
>- `objects`：是 Git 的**本地仓库**，里面包含了创建的各种对象及内容

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
>`git init` 会在 `.git 目录` 【包含了资源的所有元数据】中初始化一个 <u>Git 仓库</u>【在指定目录下】

- `git init` 在当前目录下创建
	- `git init 指定目录` 在当前目录下创建指定目录，并在里面创建仓库

>[!warning]
>- 在 Linux 系统中，`commit` 的提交说明使用单引号 ' 
>- Windows 系统，`commit` 的提交说明使用双引号 "

## git clone
>>在本地仓库上创建一个远程仓库的完整副本
>- `git clone 仓库地址` 
>- `git clone 仓库地址 指定目录` 拷贝到指定的目录

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

# 根据日期条件，以简洁的方式，显示非合并提交
$ git log --oneline --before={3.weeks.ago} --after={2010-04-18} --no-merges
```

---

- `git blame 文件` <u>逐行显示</u>查看指定文件的历史修改记录，可以追踪<u>文件中每一行的变更历史</u>【作者，提交哈希，提交日期，提交消息……】
	- `-L 起始行号,结束行号` 只显示指定行号范围内的代码注释
	- `-C` 对于重命名或拷贝的代码行，也进行代码行溯源
	- `-M` 对于移动的代码行，也进行代码行溯源
	- `-C -C` 或 `-M -M` 对于较多改动的代码行，进行更进一步的溯源
	- `--show-stats` 显示包含每个作者的行数统计信息

```bash
$ git blame 属性 文件

$ git blame README 
^d2097aa (tianqixin 2020-08-25 14:59:25 +0800 1) # Runoob Git 测试
db9315b0 (runoob    2020-08-25 16:00:23 +0800 2) # 菜鸟教程
```

### 查看仓库状态
#### git status
`git status` 查看仓库当前的状态【文件是否被跟踪，是否未提交】

- **未跟踪（Untracked）**：这些是新增的文件或目录，未被 `git add`
- **已修改（Modified）**：这些是已被 Git 跟踪的文件，但其内容已被修改
- **已暂存的变更（Added）**：已通过 `git add` 将修改的文件添加到暂存区的文件
- **未合并的路径（Unmerged paths）**：这些是在合并分支时产生冲突的文件，需要手动解决冲突后才能完成合并
- **已删除（Deleted）**：这些是已被删除但尚未提交的文件

#### git diff
- `git diff` 比较工作区与暂存区之间的差异内容
- `git diff --cached` 比较暂存区与本地仓库之间的差异内容
- `git diff 版本id1 版本id2` 比较两个版本之间的差异
- `git diff HEAD` 比较工作区与本地仓库之间的差异内容
- `git diff 版本id HEAD` 比较某个版本与本地仓库的差异
- `git diff HEAD~ HEAD` 比较本地仓库和上一个版本之间的差异
- `git diff HEAD~2 HEAD` 比较本地仓库和上 2 个版本之间的差异
---
- `git diff 文件名` 只会查看这个文件的差异
---
- `git diff 分支1 分支2` 比较两个分支之间的差异

## 提交与修改
### 工作区操作
#### git add
- `git add` 将添加文件到暂存区
	- `git add .` 表示将当前工作目录中所有已修改或新增的文件都添加到 Git 的暂存区中
	- `git add *.txt` 将以 `.txt` 结尾的文件添加到暂存区

#### git commit
- `git commit` 提交暂存区到本地仓库
	- `git commit -m '第一次版本提交'` 添加提交信息

#### git reset
- `git reset 要回退的版本id` 回退版本
	- `--soft` 回退版本时，保留两个版本之间工作区和暂存区的修改内容
	- `--hard` 回退版本时，清空两个版本之间工作区和暂存区的修改内容
	- `--mixed` 回退版本时，保留两个版本之间工作区的修改内容，清空两个版本之间暂存区的修改内容

>[!hint] 使用场景
>- 当我们有了多次提交，但是又觉得这些提交没有什么意义，可以合并成一个版本时
>	>我们可以 `git reset --soft 需要回退的版本id`，然后回退了版本，但是最新版的文件又没删除，那我们可以重新 `git commit` 一下，就实现了文件还是那些文件，但是多个无用版本合并了

#### git rm
`git rm` 将文件从暂存区和工作区中都删除

>[!hint] 如果只是使用 Linux 中的 `rm 文件`，只会从工作区中删除文件，暂存区中不会被删除，还需要 `git add .` 一下，**比较麻烦**

#### 其他
- `git mv` 移动或重命名工作区文件
- `git restore` 恢复或撤销文件的更改
- `git checkout`

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

- `git branch -d 分支名` **删除已经被合并的分支**
- `git branch -D 分支名` 删除未被合并的分支

---

- `git switch 分支名` **切换分支**：Git 会查找目标分支最后一次提交时的快照，并将你的工作目录中的文件更新为该快照中的内容

---

- `git merge 分支1` **合并分支**：将分支 1 合并到当前分支

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
# 进行合并
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

# 标签
>[!hint] 什么时候要使用<u>标签</u> ？
>如果你到了一个重要的阶段，并希望永远记住那个特别的提交快照，你可以使用 `git tag` 给它打上标签

- `git tag` **查看所有标签**
	- `-a` **创建一个带注解的标签**【记录打标签的时间，谁打的标签】
	- `-d` 删除标签

```bash
# 查看所有标签
$ git tag
v0.9
v1.0

# 给最新一次提交打上（HEAD）"v1.0"的标签
$ git tag -a v1.0
# 带注释信息的打标签
$ git tag -a v2.0 -m "runoob.com标签"

$ git tag -d v1.0
```

## 追加标签
>如果我们忘了给某个提交打标签，又将它发布了，我们可以给它追加标签

```bash
# 追加标签时，最后面指定提交的id（85fc7e7）
$ git tag -a v0.9 85fc7e7

$ git log --oneline --decorate --graph
*   d5e9fc2 (HEAD -> master) Merge branch 'change_site'
|\  
| * 7774248 (change_site) changed the runoob.php
* | c68142b 修改代码
|/  
* c1501a2 removed test.txt、add runoob.php
* 3e92c19 add test.txt
* 85fc7e7 (tag: v0.9) 第一次版本提交
```

# 远程仓库
>如果你想通过 Git 分享你的代码或者与其他开发人员合作，你就需要将数据放到一台其他开发人员能够连接的服务器上
>![400](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403221113329.png)

## 初始化
- 在本地生成 SSH Key `ssh-keygen -t rsa -C "github注册的邮箱"`
	- 第一次：默认一直回车
	- 第二次及以上……
		- 指定新的 SSH 文件名
		- 
- 成功的话，会在 `~/` 下生成 `.ssh` 文件夹，打开 `id_rsa.pub`，复制
- 打开 github，打开 **SSH and GPG keys**，然后点击 **New SSH key** ，设置名称，再粘贴复制的 Key
- 验证是否成功 `ssh -T git@github.com`
- 设置 username 和 email【因为每次 commit 都会记录它们】
```bash
$ git config --global user.name "your name"
$ git config --global user.email "your_email@youremail.com"
```

>[!hint] 查看在 Git 中配置的全局用户名和邮箱
> ```bash
> C:\Users\19628>git config --global user.name
> 123
> 
> C:\Users\19628>git config --global user.email
> 1962883041@qq.com
> ```

---

- 添加远程仓库，并添加别名【~~远程仓库的地址会存储在 `config文件` 中 ~~】
`git remote add 别名 git@github.com:github的名字/仓库名.git`

## 推送到远程库
- `git push 远程仓库别名 本地分支名:远程分支名` 进行推送

## 查看
- `git remote` 查看当前配置有哪些远程仓库
	- `-v` 查看到链接地址

## 拉取
>`pull` = `fetch` + `merge`
>![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403222350736.png)

- `git fetch 远程仓库名` 获取远程仓库的最新信息而不直接修改本地的工作文件
	- `git fetch -all` 获取远程仓库的所有分支
	- `git fetch 远程仓库名 分支名` 获取远程仓库的特定分支
- `git merge` 合并 `fetch` 的最新信息到当前分支
- `git pull 远程仓库名 远程分支名:本地分支名` 获取并合并远程仓库的更改到本地工作目录

```bash
git fetch test
# 将远程仓库的`test`的`master`分支合并到当前所在的分支
git merge test/master
```

>[!hint] `git clone` 与 `git pull`
>>这两个命令的结果是一样的，但是所代表的含义不一样：
>- `git clone` 表示从头开始一个项目时，我们需要初始化仓库，如果不使用 `git init` ，那我们就需要在本地仓库创建一个远程仓库的副本
>- `git pull` 表示在已经初始化好了本地仓库之后，拉取远程仓库中最新更新的一些文件【如果没有进行初始化，是 `git pull` 不了的 】

## 删除
- `git remote rm 本地仓库别名` 删除本地仓库中指定的远程仓库别名
- `git push 远程仓库别名 --delete 分支名` 删除远程仓库的某个分支

---

```bash
# 整体的步骤
# 进入到对应的目录
$ git init    
$ git add README.md  
$ git commit -m "添加 README.md 文件"  
[master (root-commit) 0205aab] 添加 README.md 文件
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

$ git remote add test git@github.com:tianqixin/runoob-git-test.git
$ git push -u test master
```

# .gitignore
>[!hint] 应该被忽略的文件
>- 系统自动生成的文件
>- 缓存文件
>- 中间文件【比如 Java 产生的 `.class` 文件】
>- 敏感信息文件

>[!hint] 如果某个文件在 `.gitignore` 创建之前已经被 `commit` 到了本地仓库了，那 `.gitignore` 就控制不到了
>解决办法：
>- 删除本地仓库的文件 `git rm --cached 文件`
>- 再次提交 `git commit -m "……"`

```
#.gitignore 文件
file1.txt

# 只忽略当前目录下的 temp 文件夹
/temp

# 忽略该目录下的所有 temp 文件夹 
temp/   
```

# 规范
- `main分支` ==主要分支==
	- 不允许直接修改，只能通过合并修改【每次合并时都打一个标签】
	- 要一直保持 `main分支` 的代码是稳定的，是可发布的
- `问题修复分支` ：合并到 `main分支` 之后会删除该分支，==辅助分支==【可合并】
- `功能分支` ：当功能分支稳定后，会合并到开发分支中，==辅助分支==
- `开发分支` ：结合了所有的功能分支，==主要分支==
- `预发布分支` ：用于发布前测试开发分支，修订问题，测试完毕后，合并到 `main分支`，和 `开发分支`，==辅助分支==

>[!hint] 版本号 `A.B.C`，A 是主要版本，B 是次要版本，C 是修订版本


# idea

### 拉取
- ![300](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211339240.png)
- 拉取别人仓库![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211342220.png)
- 拉取自己账号里的仓库![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211340541.png)
- 选择拉取到本地的地址![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211340313.png)

### 提交
![300](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211648397.png)



### 推送
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211649783.png)



































