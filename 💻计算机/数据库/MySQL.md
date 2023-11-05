---
tags:
  - 计算机/数据库
---
# 🌕DDL
>Data Definition Language 数据库定义语言
### 🌗数据库操作
- ***查询***
	- `SHOW DATABASES;`  查询所有数据库
	- `SELECT DATABASE();`  查询当前正在使用的数据库
- ***创建***
	```sql
	CREATE DATABASE  
	    [IF NOT EXISTS]      /*中括号表示可选项*/
	    数据库名  
	    [CHARACTER SET 字符集名]
	    [COLLATE 排序规则];
	```
- ***使用***
	- `USE 数据库名;`  切换到某个数据库
- ***删除***
	- `DROP DATABASE [IF EXISTS] 数据库名;`  删除某个数据库
### 🌗表的操作
- ***查询***
	- `SHOW TABLES;`  查询当前数据库所有的表
	- `DESC 表名`  查询表结构
- ***创建***
```sql
CREATE TABLE 表名(
	字段1 字段类型[COMMENT 注释],
	字段2 字段类型[COMMENT 注释],
	字段3 字段类型[COMMENT 注释],
	…………
	字段n 字段类型[COMMENT 注释]
)[COMMENT 表注释]
```



# 🌕DML
>Data Manipulation Language 数据库操作语言

# 🌕DQL
>Data Query Language 数据查询语言



# 🌕DCL
>Data Control Language 数据库控制语言




