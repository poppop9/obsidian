- 彩云天气SVIP解锁
- Testflight下载修正
- Spotify Premuim解锁
- BiliBili去广告
- 知乎去广告+优化

`https://raw.githubusercontent.com/erdongchanyo/Rules/main/Surge/Module/AllinOne.sgmodule`

---

# 配置说明
#### 配置文件下载地址
`https://raw.githubusercontent.com/erdongchanyo/Rules/main/Surge/Surge_EDC-Lzay.conf`

#### 1. 点击UI界面左上角 `当前配置文件名` 进入 - `配置列表` 界面

#### 2. 点击 `从URL下载配置` 并粘贴配置文件下载链接进行下载

#### 3.下载配置后，需要 `创建当前配置副本` 后自行添加机场订阅链接

> - 此处推荐使用Sub-Store订阅链接，多机场用户可以将多个机场订阅整合为一个Sub-Store订阅
>     
>     - 需自行安装 `Sub-Store模块` ，参考[Sub-Store 文字教程](https://www.notion.so/Sub-Store-6259586994d34c11a4ced5c406264b46)

> - Surge MAC：
>     
>     - 显示主窗口 - 策略
>     - 右键编辑"PROXY"策略组 - 选择"可选策略组"下一步
>     - 更换“同时包含外部策略”对话框中的链接为你自己的Sub-Store订阅链接或机场订阅链接；

> - Surge iOS:
>     
>     - 首页 - “出站模式”模块下选择“代理服务器”
>     - 选择“PROXY”策略组 - 下拉到底部“外部代理列表”
>     - 更换其中的链接为你自己的Sub-Store订阅链接或机场订阅链接。

#### 3.打开 `脚本(Scripting)` 、`重写(Rewrite)` 、`MitM` 功能开关

> - 使用`MitM`需要安装并信任证书
>     
>     - UI界面点击 - `MitM` 模块下的- `配置证书`
>     - 跳转至新页面后，点击 `生成新的 CA 证书`
>     - 点击 `安装证书` 跳转至浏览器后，点击 `允许` 下载证书
>     - iPhone设置 - 通用 - VPN与设备管理 - 点击已下载的描述文件 `Surge Generated CA ...` 进行安装
>     - iPhone设置 - 通用 - 关于本机 - 证书信任设置 - 打开 `Surge Generated CA ...` 证书信任开关

**[更多Airport、合租、VPS推荐](https://i.erdon.cc/)**

### a. 策略组及对应分流规则

> **Proxy策略(全部节点)**

> **自动选择最优节点策略(香港)** `默认隐藏`

> **服务器按国家(地区)分组策略**
> 
> - 美国服务器策略组
> - 香港服务器策略组
> - 日本服务器策略组
> - 台湾服务器策略组
> - 新加坡服务器策略组

> **国外策略(Global)**

> **媒体策略(GlobalMedia)**
> 
> - 媒体细分策略(Neiflix、Disney+、HBO、YouTube、Spotify、TikTok、Bilibili
> - 软件细分策略(Telegram、Twitter、Speedtest、PayPal、Testflight、Apple、Google、Microsoft、Weibo

> **国内策略(Mainland)** - 默认无特殊需求请选择 DIRECT 策略

> **去广告策略** `默认REJECT，直接隐藏`
> 
> - Advertising（RULE-SET + DOMAIN-SET）
> - Privacy
> - Hijacking

> **最终策略(Final)**

### b. 模块（根据个人需求通过 `模块` 进行安装）

> **EDC-AllinOne(iOS)** [安装链接](https://raw.githubusercontent.com/erdongchanyo/Rules/main/Surge/Module/AllinOne.sgmodule)
> 
> - 彩云天气SVIP解锁(By Tartarus
> - Testflight下载修正
> - Spotify Premuim解锁(By app2smile
> - BiliBili去广告
> - 知乎去广告+优化

> **TikTok 解锁-美国** [安装链接](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/external/Surge/TikTokUnlock/TikTokUS.sgmodule)
> 
> - 仅支持TikTok 21.1.0及以下版本

> **BoxJS** [安装链接](https://raw.githubusercontent.com/chavyleung/scripts/master/box/rewrite/boxjs.rewrite.surge.sgmodule)
> 
> - 访问：[http://boxjs.com](http://boxjs.com/)

> **Sub-Store** [安装链接](https://raw.githubusercontent.com/Peng-YM/Sub-Store/master/config/Surge.sgmodule)
> 
> - 高级订阅管理工具，访问：[https://sub-store.vercel.app](https://sub-store.vercel.app/)

### c.脚本任务

自行Google或各大Telegram群组获取
















