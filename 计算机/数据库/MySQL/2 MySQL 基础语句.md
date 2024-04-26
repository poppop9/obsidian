# DDL
>[!quote] DDL
>DDL 是数据库定义语言【Data Definition Language】

## 数据库操作
- ***查询***
	- `SHOW DATABASES;`  查询所有数据库
	- `SELECT DATABASE();`  查询当前正在使用的数据库

---

- ***创建***
```sql
CREATE DATABASE  
	[IF NOT EXISTS]      /*中括号表示可选项*/
	数据库名  
	[CHARACTER SET 字符集名]
	[COLLATE 排序规则];
```

---

- ***使用***
	- `USE 数据库名;`  切换到某个数据库

---

- ***删除***
	- `DROP DATABASE [IF EXISTS] 数据库名;`  删除某个数据库

## 表的操作
- ***查询***
	- `SHOW TABLES;`  查询当前数据库所有的表
	- `DESC 表名;`  查询表结构
	- `SHOW CREATE TABLE 表名;`  查询建表语句

---

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

---

- **修改字段**
	- 添加字段
		```sql
		ALTER TABLE 表名 ADD 字段名 数据类型[COMMENT 注释] [约束];
		```
	- 修改属性
		```sql
		ALTER TABLE 表名
			CHANGE 旧字段名 新字段名 新数据类型 [COMMENT 注释]
			[约束];
		```

---

- **修改表**
	- 修改表名
		```sql
		ALTER TABLE 旧表名 RENAME TO 新表名;
		```
	- 修改表的存储引擎
		```sql
		ALTER TABLE 表名
			ENGINE = 存储引擎类型;       //修改表的存储引擎
		```

---

- ***删除***
```sql
ALTER TABLE 表名 DROP 字段名;   //删除某个字段名【删除一列】
```

```sql
DROP TABLE [IF EXISTS] 表名;       //删除整张表
```

```sql
TRUNCATE TABLE 表名;        //删除表中数据，但保留表结构
```

# DML
>[!QUOTE] DML
>DML 是数据库操作语言【Data Manipulation Language】

字符串和日期时间类型都需要包含在 `引号''` 内

## INSERT
- **单个插入**
	- 给指定数量字段插入【**安全插入**】[^1]
		```sql
		INSERT INTO 表名(字段1,字段2,……,字段n) VALUES(值1,值2,……,值n);
		```
	- 给所有字段插入【**不安全插入**】[^2]
		```sql
		INSERT INTO 表名 VALUES(值1,值2,……,值n);
		```

>[!quote] 安全插入，不安全插入
>- **安全插入**：不会由于表结构的改变而导致语法错误
>- **不安全插入**：可能因为表结构的改变而导致语法错误

---

- **批量插入**
	- 给指定数量字段插入
		```sql
		INSERT TABLE 表名(字段1,字段2) VALUES(值1,值2,……,值n),(值1,值2,……,值n)……;
		```
	- 给所有字段插入
		```sql
		INSERT INTO 表名 VALUES(值1,值2,……,值n),(值1,值2,……,值n)……;
		```

---

>[!hint] 如何插入 SELECT 出的数据
>```sql
> INSERT INTO 表1 (column1, column2, ...)  
> SELECT column1,  
>        column2, 
>        ...  
> FROM 表2;
> ```
> ***INSERT只能插入一行，而INSERT-SELECT可以插入多行***

## UPDATE
```sql
UPDATE 表名 SET 字段名1=值1,字段名2=值2 [WHERE 条件];
```

>[!hint] 如何从 表A 中选择数据，并使用这些数据来更新 表B 的行
>```sql
>UPDATE table1
> 	JOIN table2 ON join_condition
> 	SET table1.column1 = table2.column1, table1.column2 = table2.column2, ...
> 	[WHERE 条件];
>```
>`table1` 是要更新的目标表，`table2` 是提供数据的源表。`JOIN` 子句用于指定两个表之间的连接条件。您可以在 `SET` 子句中指定要更新的列，并将其设置为源表中相应列的值

## DELETE
>[!hint] DELETE 的删除是以行为单位的

```sql
DELETE FROM 表名 [WHERE 条件];   //删除n行
```

---

>[!hint] 如何不删除某个字段，但是删除这个字段的所有数据
>```sql
>UPDATE 表名 SET 字段名 = NULL;
>```

# DQL
>[!quote] DQL
>DQL 是数据查询语言【Data Query Language】

>[!hint] DQL语句的执行顺序
>```sql
> select 字段列表  // 4
> from 表名  // 1
> where 条件  // 2 
> group by 分组字段列表  // 3
> having 分组后条件列表  // 7
> order by 排序字段列表  // 5
> limit 分页参数； // 6
>```

## 基本查询
- 查询指定个字段
	```sql
	SELECT 字段1,字段2,……,字段n FROM 表名;  //查询指定个字段的所有内容
	```
- 查询所有字段
	```sql
	SELECT * FROM 表名;
	```
- 去除重复查询
	```sql
	SELECT DISTINCT 字段1,字段2,……,字段n FROM 表名;
	```
- 取别名查询
	```sql
	SELECT 字段1[别名1],字段2[别名2] FROM 表名;
	```

## 条件查询
```sql
SELECT 字段 FROM 表名 WHERE 条件;   //可以有多个条件【用逻辑符连接】
 ```

|比较运算符|描述 |示例|
|---|---|---|
|=|等于|WHERE column_name = value|
|!= 或 <>|不等于|WHERE column_name != value |
|>|大于|WHERE column_name > value |
|< |小于|WHERE column_name < value|
|>= |大于等于 |WHERE column_name >= value|
|<= |小于等于|WHERE column_name <= value|
|BETWEEN...AND... |在范围内|WHERE column_name BETWEEN 值1 AND 值2 |
|NOT BETWEEN...AND...|不在范围内|WHERE column_name NOT BETWEEN 值1 AND 值2|
|IN|在给定值列表中|WHERE column_name IN (值1, 值2, ...)|
|NOT IN|不在给定值列表中|WHERE column_name NOT IN (值1, 值2, ...)|
|LIKE|模糊匹配|WHERE column_name LIKE `pattern`|
|NOT LIKE|不匹配指定模式|WHERE column_name NOT LIKE `pattern`|
|IS NULL |为 NULL|WHERE column_name IS NULL|
|IS NOT NULL|不为 NULL|WHERE column_name IS NOT NULL |
`pattern` 中的 `_` 表示单个模糊字符，`%` 表示任意个字符，***此类通配符只能用于文本字段【字符串】***
```sql
SELECT * FROM 表名 WHERE name like '张_';  //表示查询name为姓张什么的人

SELECT * FROM 表名 WHERE name like '张%';  //表示查询name为姓张什么什么什么……的人
```

- 尽量不要把通配符用在搜索模式的开始处，例如`LIKE '%立'`，这样搜索起来是最慢的【数据库需要对表中的每个记录进行扫描】
- `IN`操作符比`OR`操作符的执行速度更快【数据越多越明显】
- 如果其他操作符可以达到相同目的，就不要使用通配符【***通配符处理时间长***】

---

|逻辑运算符 |描述|示例|
|:-:|:-:|:-:|
|AND 或 &&|并且 |WHERE 字段 > 1 AND 字段 != 5 |
|OR 或 \|\||或者|WHERE 字段 > 1 OR 字段 != 5|
|NOT 或 !|非|WHERE NOT 字段 = 2|
- ***AND 的优先级高于 OR***
- ***逻辑不明确时可以加括号***

## 分组查询
```sql
SELECT 字段 FROM 表名 [WHERE 条件] GROUP BY 分组字段名 [HAVING 分组后的过滤条件]; 

---

SELECT gender,COUNT(*) FROM table GROUP BY gender;

|gender|COUNT(\*)|
|:-:|:-:|
|女 |7|
|男 |9|
```

- 如果分组列中包含具有NULL值的行，则NULL将作为一个分组返回

>[!hint] WHERE 与 HAVING 的区别
>where：
>- 对分组之前的数据进行过滤，如果不满足则不参与分组；
>- 而且where不能对聚合函数进行过滤；
>
>having：
>- 对分组之后的数据进行过滤；
>- having可以对聚合函数进行过滤；

>[!hint] 在有 GROUP BY 子句的SELECT语句中，被SELECT的字段是有限制的
>使用了GROUP BY的SELECT语句中，只能SELECT已经GROUP BY过的列，和使用了聚集函数的任何列。例如：
>```sql
> SELECT customer_name, SUM(order_amount)
> FROM orders
> GROUP BY customer_name;
> ```
> 就是正确的，不能在SELECT里再加入customer_year，***因为这是没有意义的***，但是可以加入聚合函数（customer_year）

## 排序查询
```sql
SELECT 字段 FROM 表名 ORDER BY 字段1 排序方式1,字段2 排序方式2……;

---

根据年龄对公司员工进行升序排序，年龄相同，再按照入职时间进行降序
SELECT * FROM table ORDER BY age ASC,entrydate DESC……; 
                                     //DESC为降序，ASC为升序【默认】
```

## 分页查询
```sql
SELECT 字段 FROM 表名 LIMIT 起始索引,查询记录数;    //起始索引从0开始

---

查询第1页员工数据，每页展示10条记录
select * from emp limit 0,10；//查询的是第1页数据，起始索引可以省略，简写为limit 10

查询第二页的员工数据，每页展示10条记录
select * from emp limit 10,10;
```

**分页查询是数据库的方言【每个数据库都不同】**

## 子查询
### 标量子查询
>子查询返回的结果是单个值

```sql
SELECT * FROM emp WHERE dept_id = (SELECT id FROM dept WHERE name = '教研部');
                                        //这里的子查询只有一个结果
```
### 列子查询
>子查询返回的结果是一列

```sql
SELECT * FROM emp WHERE dept_id in (SELECT id FROM dept WHERE name = '教研部' OR name = '咨询部');                    //这里的子查询有多个结果
```
### 行子查询
>子查询返回的结果是一行

```sql
//查询入职日期和工作跟吴彦祖都相同的人
SELECT * FROM emp WHERE entrydate = (SELECT entrydate FROM emp WHERE name = '吴彦祖'),job = (SELECT job FROM emp WHERE name = '吴彦祖');
或
SELECT * FROM emp WHERE (entrydate,job) = (SELECT entrydate,job FROM emp WHERE name = '吴彦祖');
```
### 表子查询
>子查询返回的结果是多行多列

```SQL
SELECT e.*,dept.name FROM (SELECT * FROM emp WHERE entrydate > 2) e,dept WHERE e.dept_id = dept.id;          //此处把子查询的结果作为了一张表 
```

# DCL
>[!quote] DCL
>DCL 是数据库控制语言【~~Data Control Language~~】，管理数据库用户，控制数据库的访问权限

在每个数据库服务中，都会自带一个叫 mysql 的数据库，里面有一张 `user 表` ，存储用户信息

```sql
Host,User
localhost,mysql.infoschema
localhost,mysql.session
localhost,mysql.sys
localhost,root
```

- 拆线