<u>插件</u> ：
- https://chodocs.cn/program/npm-package/
- https://vitepress.yiov.top/plugin.html#%E8%87%AA%E5%8A%A8%E4%BE%A7%E8%BE%B9%E6%A0%8F
- https://blog.csdn.net/gitblog_00100/article/details/139915260

<u>教学</u> ：
- https://developer.aliyun.com/article/1487073?spm=a2c6h.14164896.0.0.2fc947c5MpOuep&scm=20140722.S_community@@%E6%96%87%E7%AB%A0@@1487073._.ID_1487073-RL_VitePress%E7%AE%80%E6%98%93%E9%80%9F%E9%80%9F%E4%B8%8A%E6%89%8B%E5%B0%8F%E5%86%8C-LOC_search~UND~community~UND~item-OR_ser-V_3-P0_0

<u>模板市场</u> ：
- https://www.builtatlightspeed.com/

<u>例子</u> ：
- https://doc.theojs.cn/


# ❤ 安装
- `npm add -D vitepress` 
- `npx vitepress init` 初始化项目

# ❤ 文件结构
- `.vitepress` 
	- `.config.js` 配置文件，自定义站点的各个方面
- `src` 
	- `public` 静态资源
	- `notes` 笔记


# ❤ 路由
<u>srcDir</u> ：将 src 目录配置为路由的根目录，这样访问笔记就可以直接端口号后面加 src 之后的路径
```js
export default defineConfig({
	// 
	srcDir: './src',
……
})
```




# ❤ 主题
在 `.vitepress/config.js` 中的 themeConfig 中配置










