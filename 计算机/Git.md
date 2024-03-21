
# 配置
## 三大配置文件
- `--system` 会读写 `/etc/gitconfig` 文件：影响<u>所有用户</u>的 Git 环境
- `--global` 会读写 `~/.gitconfig` 文件：对<u>当前用户</u>的<u>所有 Git 项目</u>生效
	- 如果在使用 git 命令时使用了 `--global`，那么更改的配置文件就是用户主目录下的那个，以后该用户所有的项目都会默认使用这里配置的用户信息
- `默认` 会读写当前工作目录中的 `.git/config` 文件：这里的配置仅仅针对<u>当前项目</u>有效

>[!hint] 每一个级别的配置都会覆盖上层的相同配置【例如，`.git/config` 里的配置会覆盖 `/etc/gitconfig`】

## 用户信息
配置个人的用户名称和电子邮件地址：
`$ git config --global user.name "runoob"`
`$ git config --global user.email test@runoob.com`

## 差异分析工具
在解决合并冲突时使用哪种差异分析工具。比如要改用 vimdiff 的话：
`$ git config --global merge.tool vimdiff`

## 查看配置信息
- 查看所有配置 `$ git config --list`
- 查看某个配置 `$ git config user.name`

>[!hint] 有时候会看到重复的变量名，意味着它们来自不同的配置文件

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

>[!quote] 暂存区
>一般存放在 `.git` 目录下的 `index` 文件中，所以我们把暂存区有时也叫作“索引”

>[!quote] 版本库
>>是工作区中的一个隐藏目录 `.git`
>
>- 标记为 "master" 的是 master 分支所代表的目录树
>- "HEAD" 是指向 master 分支的一个"游标"【所以命令中出现 HEAD 的地方可以用 master 来替换】
>- objects 标识的区域为 Git 的对象库，里面包含了创建的各种对象及内容


- 当对工作区修改的文件执行 `git add` 命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的ID被记录在暂存区的文件索引中。
- 当执行提交操作（git commit）时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。
    
- 当执行 git reset HEAD 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。
    
- 当执行 git rm --cached \<file> 命令时，会直接从暂存区删除文件，工作区则不做出改变。
    
- 当执行 git checkout . 或者 git checkout -- \<file> 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区中的改动。
    
- 当执行 git checkout HEAD . 或者 git checkout HEAD \<file> 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。








# 拉取
- ![300](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211339240.png)
- 拉取别人仓库![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211342220.png)
- 拉取自己账号里的仓库![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211340541.png)
- 选择拉取到本地的地址![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211340313.png)

# 提交
![300](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211648397.png)







# 推送
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211649783.png)



































