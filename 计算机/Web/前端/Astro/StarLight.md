---
title: Starlight
---

# 安装
- `npm create astro@latest -- --template starlight` 
	- 这时候不要安装依赖
- 进入项目目录
- `npm install` 
- `npm run dev` 

>[!hint] 更新 `npx @astrojs/upgrade` 

# ❤️ 页面
## 💛 md 页面
在 `src/content/docs/` 中创建 md 文件来添加新页面，使用子文件夹来组织文件

扩展 md 的代码块： https://starlight.astro.build/zh-cn/guides/authoring-content/#expressive-code-%E5%8A%9F%E8%83%BD

自定义 md 语法 ： https://docs.astro.build/zh-cn/guides/markdown-content/#%E9%85%8D%E7%BD%AE-markdown


### frontmatter
- 每个文档的 frontmatter 都必须包含 title 属性，在网页上显示为标题

```
---
title: Hello, World!
---
```

---

不想要这个，怎么取消： https://starlight.astro.build/zh-cn/guides/authoring-content/#%E5%A6%82%E4%BD%95%E5%9C%A8-starlight-%E4%B8%AD%E7%BB%84%E7%BB%87%E9%A1%B5%E9%9D%A2%E5%86%85%E5%AE%B9        




## 💛 自定义页面
https://starlight.astro.build/zh-cn/guides/pages/#%E8%87%AA%E5%AE%9A%E4%B9%89%E9%A1%B5%E9%9D%A2





# 部署
https://docs.astro.build/zh-cn/guides/deploy/

