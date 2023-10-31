#计算机/数据库
# DDL
>Data Definition Language 数据库定义语言
### 数据库操作
##### 查询
`SHOW DATABASES;`  查询所有数据库
`SELECT DATABASE();`  查询当前正在使用的数据库
##### 创建
创建数据库
```sql
CREATE DATABASE  
    [IF NOT EXISTS]      /*中括号表示可选项*/
    数据库名  
    [CHARACTER SET 字符集名]
    [COLLATE 排序规则];
```
##### 使用
`USE 数据库名;`  切换到某个数据库
##### 删除
`DROP DATABASE [IF EXISTS] 数据库名;`  删除某个数据库


- 查询
`SHOW DATABASES;`  查询所有数据库
`SELECT DATABASE();`  查询当前正在使用的数据库

- 创建
```sql
CREATE DATABASE  
    [IF NOT EXISTS]      /*中括号表示可选项*/
    数据库名  
    [CHARACTER SET 字符集名]
    [COLLATE 排序规则];
```

- 使用
`USE 数据库名;`  切换到某个数据库

- 删除
`DROP DATABASE [IF EXISTS] 数据库名;`  删除某个数据库

# DML
>Data Manipulation Language 数据库操作语言

# DQL
>Data Query Language 数据查询语言



# DCL
>Data Control Language 数据库控制语言




