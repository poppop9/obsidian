# 函数
## 日期函数
>[!summary] 方法
>now()  获取当前的系统时间
>YEAR(date)  ------在date数据类型中提取出year

```sql
insert into customer(update_time) values (now());         //插入当前时间

SELECT order_num FROM Orders WHERE YEAR(order_date) = 2020;
```
## 文本函数
>[!summary] 方法
>CONCAT(S1,S2,..Sn)  ------将S1，S2，….Sn拼接成一个字符串
>
>LOWER(str)  ------将字符串str全部转为小写
>UPPER(str)  ------将字符串str全部转为大写
>
>LPAD(str，n，pad)  ------左填充，用字符串pad对str的左边进行填充，达到n个长度
>RPAD(str，n，pad)  ------右填充，用字符串pad对str的右边进行填充，达到n个长度
>
>TRIM(str)  ------去掉字符串头部和尾部的空格
>SUBSTRING(str,start,len)  ------返回从字符串str从start位置起的len个长度的字符串
>
>LEFT(str，len)  ------返回str左边开始数len长度个字符
>RIGHT(str，len)  ------返回str右边开始数len长度个字符
>LENGTH(str)  ------返回str字符串的长度

```sql
select concat ('hello', 'MySQL');         hello MySQL 
select Lower('Hello');       hello
select upper('Hello');        HELLO
select lpad('01', 5, '-');       ---01
select rpad('01', 5, '-');        01---
select trim(' Hello MySQL ')       Hello MySQL
						// RTRIM()：去掉字符串右边的空格
						// LTRIM()：去掉字符串左边的空格

select substring('Hello MySQL',1, 5);     Hello
          // 注意索引是从1开始的

SELECT LEFT('HELLO',3);     HEL
SELECT LENGTH('HELLO');     5
```
## 数值函数
>[!summary] 方法
>
## 聚合函数
- `AVG()` 返回某列的平均值

---

- `COUNT()` 返回某列的行数

```sql
SELECT COUNT(cust_email) AS num_cust FROM Customers;
```

>[!hint] 对于 `NULL` 的计数
>- 使用 `COUNT(*)` 对表中行进行计数时，对于 `NULL值` 也会记录
> ```sql
> SELECT COUNT(*) FROM Customers;
> ```
> 
> - 如果只是 `COUNT(某个字段)`，则不会计数 `NULL值`
> ```sql
> SELECT COUNT(numbers) FROM Customers;
> ```

---

- `MAX()` 返回某列的最大值
- `MIN()` 返回某列的最小值
- `SUM()` 返回某列值之和

# 🔗 联结表
>[!quote] 联结表
>联结表 是一种将<u>两个</u>或<u>多个表</u>中的数据**通过某些共同的值**关联起来的操作

>[!hint] 笛卡尔积
>如果在联结时，没有加上限制条件，则是把<u>表A</u>的每一行匹配<u>表B</u>的每一行，**所以如果此种情况***`SELECT *`***时，则查询的行数 = 表A行数 \* 表B行数**

>[!hint] 联结的好处
>大多数 DBMS，处理联结的速度 远大于 子查询

## 内联结
- **隐式内联结** `SELECT 字段 FROM 表1，表2 WHERE 条件;` 【表 1 和表 2 就通过了 `WHERE` 联结在了一起】

- **显示内联结** `SELECT 字段 FROM 表1 [INNER] JOIN 表2 ON 联结条件;`
```sql
select user.id, user.name, user.age, table_name.产品ID 
from user 
INNER JOIN table_name ON table_name.id = user.id;

---
|id|name|age|            
|:-:|:-:|:-:|
|123|陈冠希|45|
|11|刘诗诗|14|
|444|吴彦祖|4|
     +
|产品ID|id|
|:-:|:-:|
|乌鸦 |444|
|狗|11|
|老虎|123|
     ↓
|id|name|age|产品ID|
|:-:|:-:|:-:|:-:|
|123|陈冠希|45|老虎|
|444 |吴彦祖|4|乌鸦|
|11 |刘诗诗|14|狗|
```
## 自联结
```sql
//使用自联结的方式来实现
SELECT c1.id, c1.name, c1.contact
FROM customers AS c1,
     customers AS c2
WHERE c2.contact = 'jim'    //经过这个条件筛选过后，c2表中只剩下一条记录
  AND c1.name = c2.name;     //c1表中的name与c2表中的那一条记录进行比较

//如果使用子查询的方式来实现：
SELECT id, name, contact
FROM customers
WHERE name = (SELECT name FROM customers WHERE contact = 'Jim');

---

|id|name|contact|
|:-:|:-:|:-:|
|100|Fun123|Jim|
|101|Fun566|Tom|     × 2
|102|Fun123|Mike|
|103|Fun578|July|
       ↓
|100|Fun123|Jim|
|102|Fun123|Mike|
```
## 外联结
- **左外联结**  `SELECT 字段列表 FROM 表A LEFT JOIN 表B ON 联结条件;`：返回左表中所有的行，以及右表中满足条件的行

```sql
SELECT customers.id, orders.numbers
FROM customers
         LEFT JOIN orders ON customers.id = orders.id;

---
|id|numbers|
|:-:|:-:|
|101|null|
|102 |9|
|103 |229|
    +
|id|name|contact|
|:-:|:-:|:-:|
|100|Fun123|Jim|
|101|Fun566|Tom|  
|102|Fun123|Mike|
|103|Fun578|July|
        ↓
|id|numbers|
|:-:|:-:|
|100|9|
|101|null|
|102 |null|
|103 |229|
```

- **右外联结**：返回右表中所有的行，以及左表中满足条件的行【~~一般不使用~~】

# 视图


# 存储过程



# 事务
>[!quote] 事务
>>事务 是一组 SQL 语句
>
> - 原子性：事务要么完全执行，要么完全不执行
> - 一致性：事务完成时，必须使<u>所有数据都保持一致状态</u>【~~比如部门表中的某个部门被删除了，那员工表中就不会出现该部门下的员工~~】
> - 隔离性：只要不COMMIT，则别的窗口看不到数据的变化
> - 持久性：事务一旦COMMIT/ROLLBACK，则数据永久改变

>[!hint] 事务处理可以回退 `INSERT`, `UPDATE`, `DALETE`。不能回退 `SELECT`, `CREATE`, `DROP`

---

**如果执行过程中没有发生错误，则 COMMIT 整组 SQL 语句；如果发生错误，则 ROLLBACK，将数据库恢复到正常状态**

- `START TRANSACTION;`  开始事务
- `COMMIT;`  结束事务并提交
- `ROLLBACK;`  回退到事务处理之前
- `SAVEPOINT 保留点名;`  设置保留点：允许在事务中的特定位置进行部分回滚，而不必回滚整个事务

```sql
START TRANSACTION;    //第一步先执行此语句

SAVEPOINT point1;    //设置一个保留点

UPDATE table SET id = 188;       //-------------------
UPDATE table SET name = Tom;      //然后执行这组语句体
UPDATE table SET age = 18;       //-------------------

---

COMMIT;      //如果这组语句体都执行成功，则可以执行COMMIT来提交

ROLLBACK;     //如果有语句执行失败了，则执行ROLLBACK来回退

ROLLBACK TO point1;  //返回到保留点point1
```

# 游标






# 约束
>[!quote] 约束
>>约束 是处理数据库的规则
>
> - `NOT NULL`  非空约束：限制字段不能为NULL
> - `UNIQUE`  唯一约束：保证字段所有数据唯一
> - `PRIMARY KEY`  主键约束
> - `FOREIGN KEY`  外键约束
> - `DEFAULT`  默认值约束：如果未指定字段的值，则采用默认值

## 主键
>[!quote] 主键
>主键 是用于唯一标识数据库表中每一行数据的**字段/字段组合**

>[!hint] 对于主键的约束
> - 每个表都需要有主键【因为这便于以后的数据操作和管理】
> - 主键列不允许`null值`
> - 包含主键值的列从不修改或更新
> - 主键值不能重用【**如果从表中删除某一行，其主键值不分配给新行**】
> 
> ```sql
> CREATE TABLE Vendors  
> (                          //并且还定义了该字段不能为空
>     vend_id      CHAR(10) NOT NULL PRIMARY KEY auto increment, //定义了vend_id字段为主键
>     vend_name    CHAR(50) NOT NULL,             //此属性可以自动自增该字段的值
>     vend_address CHAR(50) NULL
> );
> ```
> 
> ```sql
> ALTER TABLE Vendors  //表示需要修改的表是Vendors
>     ADD CONSTRAINT PRIMARY KEY (vend_id);     //给该表添加一个主键 vend_id
> ```

## 外键
>[!quote] 外键
>>外键 定义了一个表中的一个或多个字段，而这些字段来源于另一个表中的主键
>
>- **缺点**：
>	- 影响增删改的效率【需要检查外键关系】
>	- 容易引发数据库的死锁问题

### 如何创建外键
- 在创建表时指定
	```sql
	CREATE TABLE(
		字段名 数据类型，
		……
		FOREIGN KEY(外键字段名) REFERENCES 主表(字段名)
	);
	```

- 在建表之后指定
	```sql
	ALTER TABLE 表名 
	add constraint
	FOREIGN KEY(外键字段名) REFERENCES 主表(字段名);
	```


## 唯一约束
>[!quote] 唯一约束
>唯一约束 用于确保表中的<u>某个列/一组列</u>的**值是唯一的**

>[!hint] 在唯一约束的列中，允许NULL值，且可以有多个NULL值

### 如何创建唯一约束
- 在创建表时指定
	```sql
	CREATE TABLE 表名 (
	    字段名 数据类型 UNIQUE,   //使用UNIQUE关键字
	    ...
	);
	```

- 在建表之后指定
	```sql
	ALTER TABLE 表名
	ADD CONSTRAINT [约束名称] UNIQUE (字段名);
	```

## 检查约束
>检查约束是一种用于**限制表中列值**的条件约束，可以应用于单个列或多个列的组合

### 如何创建检查约束
- 在创建表时指定
	```sql
	CREATE TABLE 表名 (
	    字段名 数据类型 CHECK (逻辑表达式),
	    ...
	);

	---

	CREATE TABLE 表名 (
	age int CHECK (age > 18),    //保证了age大于18
	...
	);
	```

- 在建表之后指定
	```sql
	ALTER TABLE 表名
	ADD CONSTRAINT [约束名] CHECK (逻辑表达式);
	```

## 额外约束
### 时间约束
表中除了主键，还需要指定两个基础字段，一个是**创建时间**，一个是**更新时间**

### 前端动态渲染约束
如果要存储的某些值，在前端不会固定渲染的话，一般存储为`int`【比如要存储性别，在前端可能渲染为男士，男生，男神，所以我们把性别存储为`int`，在前端需要展示时再把`int`转换为具体的值】

