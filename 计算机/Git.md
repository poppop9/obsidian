
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

# 工作流程
![600](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211816962.png)

- 克隆 Git 资源作为工作目录
- 在克隆的资源上添加或修改文件
- 如果其他人修改了，你可以更新资源
- 在提交前查看修改
- 提交修改
- 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交




# 拉取
- ![300](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211339240.png)
- 拉取别人仓库![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211342220.png)
- 拉取自己账号里的仓库![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211340541.png)
- 选择拉取到本地的地址![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211340313.png)

# 提交
![300](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211648397.png)







# 推送
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403211649783.png)



































