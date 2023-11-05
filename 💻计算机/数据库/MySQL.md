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
	字段1 字段类型 [约束] [COMMENT 注释],
	字段2 字段类型 [约束] [COMMENT 注释],
	字段3 字段类型 [约束] [COMMENT 注释],
	…………
	字段n 字段类型 [约束] [COMMENT 注释]
)[COMMENT 表注释]
```



# 🌕DML
>Data Manipulation Language 数据库操作语言

# 🌕DQL
>Data Query Language 数据查询语言



# 🌕DCL
>Data Control Language 数据库控制语言


# 🌕约束
>约束是处理数据库的规则

- `NOT NULL`  非空约束：限制字段不能为NULL
- `UNIQUE`  唯一约束：保证字段所有数据唯一
- `PRIMARY KEY`  主键约束
- `FOREIGN KEY`  外键约束
- `DEFAULT`  默认值约束：如果未指定字段的值，则采用默认值
### 🌗主键
>主键是用于唯一标识数据库表中每一行数据的***字段/字段组合***
##### 🌑对于主键的约束
- 每个表都需要有主键【因为这便于以后的数据操作和管理】
- 主键列不允许`null值`
- 包含主键值的列从不修改或更新
- 主键值不能重用【***如果从表中删除某一行，其主键值不分配给新行***】

```sql
CREATE TABLE Vendors  
(                          //并且还定义了该字段不能为空
    vend_id      CHAR(10) NOT NULL PRIMARY KEY auto increment, //定义了vend_id字段为主键
    vend_name    CHAR(50) NOT NULL,             //此属性可以自动自增该字段的值
    vend_address CHAR(50) NULL
);
```

```sql
ALTER TABLE Vendors  //表示需要修改的表是Vendors
    ADD CONSTRAINT PRIMARY KEY (vend_id);     //给该表添加一个主键 vend_id
```
### 🌗外键




# 🌕问题处理
>[!faq] 如果要为表的主键添加auto increment属性，这个表的主键被作为了其他表的外键，每个表中都有数据，我不想数据丢失，那我该怎么办？
>- 在表中添加一个新的自增长主键列，而不删除现有的主键列
```
```
ALTER TABLE customer ADD COLUMN NewID INT AUTO_INCREMENT PRIMARY KEY FIRST;
```

