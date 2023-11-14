---
tags:
  - 计算机/数据库
---
# 🌕准备工作
- 引入MyBatis的相关依赖
![image.png|360](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20231114095900.png)
- 配置MyBatis
![image.png|490](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20231114102048.png)
- 配置SQL提示
	![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20231114143104.png)
	- 在idea的数据库配置中添加数据库
	![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20231114143555.png)
	![image.png](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20231114143538.png)


MyBatis是一个开源的Java持久层框架，它提供了一种优雅的方式来进行数据库访问。MyBatis的主要目标是简化数据库访问代码的编写，提供灵活性和高度可定制的SQL映射，以及良好的性能。

```mermaid
graph TB
	a[Java程序]-->b[JDBC]
	b-->c[MySql实现]
	b-->d[Oracle实现]
	b-->e[SqlServer实现]

	c-->f[Mysql]
	d-->g[Oracle]
	e-->h[SqlS]

    subgraph 驱动
    c
    end
```


```mermaid

```

