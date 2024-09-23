# ❤️ 安装
```bash
docker run \
  --name pgsql \
  -e POSTGRES_USER=postgres \
  -e POSTGRES_PASSWORD=13433026660 \
  -d postgres
```

# ❤️ 命令
<u>连接</u> ：
- `psql -U 用户名` 

---

<u>数据库</u> ：
- `\c` 进入/切换数据库
- 【删】
	- `DROP DATABASE 数据库名;` 
- 【查】
	- `\l` 查看所有的数据库

---

<u>表</u> ：
- `\dt` 查看所有表

