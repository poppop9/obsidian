
$$
DDD 就是领域驱动设计，Domain，Driven，Design
$$

# 设计原则
- **单一职责原则**：一个类只做一件事【比如 A 类负责转账业务，那么只有转账业务流程发生变化了，才改动这个类，其他不管怎么变，A 类雷打不动】
- **开放封闭原则**：对扩展开放，对修改封闭【未来增加功能时，做到增加类，而不修改类】
- **依赖反转原则**：程序之间只依赖于抽象接口，而不依赖于具体的实现

## 充血模型
>[!quote] 贫血模型
>贫血模型就是 MVC 中的 pojo 类，里面只有属性，和 `get()`，`set()` 方法
> 
> ```java
> public class Account {
> 	private int id;
> 	private int balance;  // 余额
> 
> 	……对应的 get ，set 方法
> }
> ```
> 当我们的业务多起来之后，这个 pojo 承载了哪些业务看不出来了，我需要到一个个 `Service` 中去找

---

<u>充血模型</u> 【也叫“实体”】就是把 pojo 的属性，以及引起属性的值发生变化的方法，写到 pojo 中。例如下面这个 pojo ，一看就知道有两个业务：

```java
public class Account {
	private int id;
	private int balance;  // 余额

	……对应的 get ，set 方法

	public void TransferIn(int money){
		balance = balance + money;
	}

	public void TransferOut(int money){
		if(balance < money){
			throws new InsufficientMonryException();
		}
		balance = balance - money;
	}
}
```

>[!warning] 只有引起 pojo 属性值变化的方法，才写到 pojo 里。【比如写入到数据库的这个操作，不会引起账户余额的变化，那就不应该写进 pojo 里】

>[!warning] 一个充血模型只负责一个业务，如果有多个业务需要到同一个充血模型，那就每个业务创建一个<u>该业务需要用到的属性</u>的充血模型。但是多个相似的充血模型还是只会创建一个数据库表
>
> ```java
> public class AccountOne {
> 	属性1;
> 	属性2;
> }
> 
> public class AccountTwo {
> 	属性3;
> 	属性4;
> }
> 
> // 数据库表
> 字段：属性1 属性2 属性3 属性4
> ```

## 仓库
>[!quote] 仓库
>仓库 是用来管理实体类的，类似 MVC 中的 `Mapper`

>[!quote] 工厂
>>工厂 是仓库的一个组件，用来<u>组建复杂的 pojo 类</u>
>
>**好处**：<u>业务实体 和 数据库表结构 不用绑定</u>【比如 Account 类需要很多属性，来自于很多个数据库表，但是我不想 Account 类里有很多属性，那我们就可以利用 accountBuilder 构建一个新的 AccountDo，A 表里查的数据放到 AccountDo 里，B 表里查的数据也放到 AccountDo 里】

```java
// 仓库接口
public interface AccountRepository {……}

// 仓库的实现类
public class AccountRepositoryImpl {
	// 关于 Account 类的数据库操作……
	@Override
	public Account Save(Account account) {
		// 将 Account 类封装成一个更复杂的 AccountDo，这就是一个工厂
		AccountDo accountDo = accountBuilder.fromAccount(account);
		// 数据库操作……
	}
	……
}
```

## 对比 MVC ，DDD
### 架构易拆分
- 传统的 MVC 架构**架构不灵活**：在项目推进的过程中，拆分功能会拆不动【A 功能，B 功能底层的调用会很混乱，会调到一起】
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403282043607.png)
- 由于 DDD 架构是业务优先，所以拆分项目会很容易
![400](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403282101681.png)

### 业务优先
- MVC 架构的项目结构，一看是不知道这一块是干嘛的
- DDD 架构是按业务划分的
	- `genService` 
		- ……
	- `hisRequest` 
		- ……
	- `sysManage` 
		- ……

### 类爆炸
#### 方法一
看完 DDD 架构的设计原则，会发现本来 MVC 用一个 `Controller`，一个 `Service` 能解决的问题，DDD 要用 `interfaces`，`application`，充血模型，仓库，工厂……很多类来解决，所以我们引入了 <u>聚合</u>

>[!quote] 聚合
>聚合 中包括<u>聚合根</u>【聚合内的一个对象，也是唯一对外开放的接口】，<u>各种值对象</u>，<u>各种实体</u>
>
>- 减少类之间的依赖关系
>![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403302058399.png)

---

有个大商场【电商系统】：
- **购物车【订单聚合】**：购物车里可以有很多商品【订单项】，也可以包含支付方式……
- **购物车的把手【订单实体，即聚合根】**：顾客通过购物车的把手来推动购物车，而不是直接拿着商品走，购物车的把手是操作整个购物车的唯一方式【无论你是要添加商品、移除商品，还是查看支付信息】
- **商品和支付信息【订单项，支付方式值对象】**：它们属于购物车，但你不会直接拿着商品走向收银台支付，而是通过推动整个购物车来进行结算

#### 方法二
只有引起实体类属性值变化的业务【新增，删除……】才去按照 DDD 架构的条条框框去做，如果这个实体类只有查询，排序……，这些不引起实体类属性值变化的业务，那我们可以不要<u>充血模型</u>，`repository` ……，避免引入更多的类

# 项目结构
![450](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403282149177.png)

## 接口层
- `interfaces` **接口层**，包含了与外部系统或用户的交互接口 ==Controller==

## 应用层
- `application` **应用层**，用来组合领域层之间的业务，形成完整的业务【比如有一个领域是知识星球领域，另一个领域是 ChatGPT 领域，我要进行两个领域的对接，就在应用层实现】 ==Service==

## 领域层
- `domain` **领域层**，与业务无关的类/接口不要放到领域层中 ==Service==
	- `model` **领域模型**，定义了领域对象、聚合和值对象
		- `entity` 实体
		- `po` 持久化对象
		- `vo` 值对象
		- `req` 请求对象的封装
		- `res` 响应对象的封装
		- ……
	- `service` **领域服务**，包含业务逻辑，<u>但是只构建业务场景，不负责处理数据，处理数据在充血模型中处理</u>

---

持久对象可以是实体，但并不是所有的持久对象都必须是实体。持久对象更强调其持久化的特性，而实体强调其在业务中的唯一性和身份标识

>[!hint] Model
>- `PO`【~~persistant object~~】 PO 是与数据库中的表相映射的 Java 对象，通常包含与数据库表字段对应的属性，以及 getter ，setter。在使用 ORM 框架 MyBatis时，PO 使得 Java 对象与数据库表之间可以进行映射
>- `VO`【~~value object~~】 VO 用于业务层之间的数据传递，仅仅包含数据而已，<u>没有唯一 ID 标识符</u>【~~意味着如果两个值对象的属性相同，那么它们就是相等的~~】
>- `DAO`【~~data access object~~】DAO 是一种设计模式，它解耦了业务层和数据访问层
>- `BO` 
>- `DTO` 
>- `POJO`
>
>- `Entity` ：Entity = `PO` + 唯一 ID 标识符，意味着如果两个 Entity 的属性值相同，它们也不相等。<u>Entity 中可以有业务逻辑，也可以没有</u>
>- `充血模型` ：充血模型 = `Entity` + 业务逻辑

业务对象层（BO）
业务对象层（BO）是封装了与业务相关的数据和操作逻辑的对象。它们包含了业务规则和业务逻辑的实现，可能包含多个PO或DTO的属性，以及处理这些属性的业务方法. 

数据传输对象（DTO）
DTO 用于在不同层之间传输数据，不包含任何业务逻辑，仅用于传输数据

简单的Java对象（POJO）
简单的Java对象（POJO）是一个简单的Java类，不包含任何特定的框架或接口依赖。POJO对象通常只包含私有的属性和对应的getter/setter方法，以及可能的其他业务方法。POJO是Java中最基本的数据模型之一，可以作为数据传输对象、业务对象等多种角色. 


>[!hint] 在领域与领域之间，如果需要某个充血模型，要把 <u>充血模型</u> 使用工厂组装成 <u>贫血模型</u> 进行传输

## 基础层
- `infrastructure` **基础层**，包含了数据库，缓存，网关，第三方工具…… ==Mapper==

# 扩展
微服务创始人说过：
- **单体架构优先**：单体架构能用，不要用微服务
- **项目不要一开始就构建微服务**：所有成功的微服务案例，都是从单体架构演变的【因为你只有做好了单体架构，你才熟悉业务流程，知道哪块臃肿了，要拆出去，如果一上来就微服务，一不下心拆错了，后期就难改了】
























