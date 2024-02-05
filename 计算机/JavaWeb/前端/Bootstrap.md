Bootstrap 可以轻松地创建响应式设计，而且提供了丰富的 JavaScript 插件

# 布局
## 容器
![800](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402051731979.png)
### .container 固定宽度容器
>提供了一个响应式的***固定宽度容器***【`max-width`会在不同的屏幕尺寸变化】

| 类 | Extra small  <br><576px | Small  <br>≥576px | Medium  <br>≥768px | Large  <br>≥992px | Extra large  <br>≥1200px | XXL  <br>≥1400px |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| `.container` | 100% | 540px | 720px | 960px | 1140px | 1320px |
| `.container-md` | 100% | 100% | 720px | 960px | 1140px | 1320px |
| `.container-lg` | 100% | 100% | 100% | 960px | 1140px | 1320px |
| `.container-xl` | 100% | 100% | 100% | 100% | 1140px | 1320px |
| `.container-xxl` | 100% | 100% | 100% | 100% | 100% | 1320px |
### .container-fluid 全宽容器
>提供了一个***全宽容器***【`width` 总是 `100%`】
## 网格
>利用 `flexbox` ，共有12列【会根据屏幕大小，自动重排】
>![800](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402051753353.png)

Bootstrap 5 网格系统有六个类：
- `.col-` (超小型设备 - 屏幕宽度小于 576px)
- `.col-sm-` (小型设备 - 屏幕宽度等于或大于 576px)
- `.col-md-` (中型设备 - 屏幕宽度等于或大于 768 像素)
- `.col-lg-` (大型设备 - 屏幕宽度等于或大于 992 像素)
- `.col-xl-` (xlarge 设备 - 屏幕宽度等于或大于 1200px)
- `.col-xxl-` (xxlarge 设备 - 屏幕宽度等于或大于 1400px)

您可以组合上述类，以创建更动态和灵活的布局。

每个类都是按比例放大的，所以如果你想为 `sm` 和 `md` 设置相同的宽度，你只需要指定 `sm`

























