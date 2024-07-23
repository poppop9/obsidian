
$$
DDD 就是领域驱动设计，Domain，Driven，Design
$$

# ❤ 设计原则
- **单一职责原则**：一个类只做一件事【比如 A 类负责转账业务，那么只有转账业务流程发生变化了，才改动这个类，其他不管怎么变，A 类雷打不动】
- **开放封闭原则**：对扩展开放，对修改封闭【未来增加功能时，做到增加类，而不修改类】
- **依赖反转原则**：程序之间只依赖于抽象接口，而不依赖于具体的实现

## 💛 充血模型
>[!quote] 贫血模型
>贫血模型就是只有属性，和 `get()`，`set()` 方法的 POJO
> 
> ```java
> public class Account {
> 	private int id;
> 	private int balance;  // 余额
> 
> 	……对应的 get ，set 方法
> }
> ```
> 
> 当我们的业务多起来之后，这个 pojo 承载了哪些业务看不出来了，我需要到一个个 `Service` 中去找

---

>[!quote] 充血模型
><u>充血模型</u> 就是把 pojo 的属性，以及引起属性的值发生变化的方法，写到 pojo 中。例如下面这个 pojo ，一看就知道有两个业务：
>
> ```java
> public class Account {
> 	private int id;
> 	private int balance;  // 余额
> 
> 	……对应的 get ，set 方法
> 
> 	public void TransferIn(int money){
> 		balance = balance + money;
> 	}
> 
> 	public void TransferOut(int money){
> 		if(balance < money){
> 			throws new InsufficientMonryException();
> 		}
> 		balance = balance - money;
> 	}
> }
> ```
> 
>- 只有引起 pojo 属性值变化的方法，才写到 pojo 里

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

## 💛 聚合
>[!quote] 聚合
>聚合 是一组具有内聚性的相关<u>对象的集合</u>。当你对数据库的操作需要使用到多个实体时，可以创建聚合

>[!quote] 聚合根


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

# ❤ 项目结构
## 💛 触发器层 trigger
<u>我们可以根据触发动作进行分类</u>：
- 接口调用（HTTP/RPC）
	- HTTP 接口：通过 RESTful API ，外部系统可以直接调用领域服务。适合需要同步响应的场景。
	- RPC 调用：通过 gRPC、Thrift 等远程过程调用框架，实现服务之间的高效通信。适合服务之间的高性能通信需求
- 消息监听：通过消息中间件 kfaka，系统可以订阅和监听消息队列中的消息。当特定的消息到达时，触发相应的领域逻辑处理。适合解耦和异步处理的场景
- 定时任务：通过定时任务框架，定时触发某些领域逻辑

>[!hint] 如果这个应用程序只有接口调用，那可以把 `trigger 层` 换成 `interfaces 层`

## 💛 应用层 / 编排层
- `application` **应用层**，用来组合领域层之间的业务，形成完整的业务【比如有一个领域是知识星球领域，另一个领域是 ChatGPT 领域，我要进行两个领域的对接，就在应用层实现】 ==Service==

## 💛 领域层
- `domain` **领域层**，与业务无关的类/接口不要放到领域层中 ==Service==
	- `model` **领域模型**，定义了领域对象、聚合和值对象
		- `po` 持久化对象
		- `vo` 值对象
		- `req` 请求对象的封装
		- `res` 响应对象的封装
		- ……
	- `repository` 仓库，里面定义了仓库接口，访问 Infrastructure 层的 repository 实现类
	- `service` **领域服务**，包含业务逻辑，只关注业务功能实现，不与外部任何接口和服务直连，而是通过<u>仓储 Repository</u>，<u>端口 Port</u>，或者<u>适配器 Adapter</u> 实现调用

---

>[!hint] Model
>![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202407232236853.png)
>
>- `POJO`【~~plain old java object~~】普通 Java 对象，可以作为其他数据模型的基础
>	- `VO`【~~value object~~】 ：值对象是不可变的对象，<u>没有唯一 ID 标识符</u>，用于表示一组值【~~意味着如果两个值对象的属性相同，那么它们就是相等的~~】
>		- 通常不会提供 setter 方法，而是提供构造函数或者 Builder 方法来实例化对象
>		- VO 中通常重写 equals 和 hashCode 方法，以便基于值进行比较
>	- `PO / 实体`【~~Entity~~】 ：实体<u>必须要有唯一 ID 标识符</u>，意味着如果两个 Entity 的属性值相同，它们也不相等；PO 是与数据库表相映射的 Java 对象【~~所以 PO 和实体可以看作是相同的概念~~】
>	- `DTO`【~~data transfer object~~】：DTO 用于在不同层之间传输数据
>		- 不包含任何业务逻辑
>	- `充血模型` ：充血模型 = PO + 业务逻辑，~~如果某个 PO 中有业务逻辑，那它就是充血模型~~
>		- `BO`【~~Business object~~】：业务对象包含业务逻辑
>			- 只用于 Service 层

>[!hint] 在领域与领域之间，如果需要某个充血模型，要把 <u>充血模型</u> 使用工厂组装成 <u>贫血模型</u> 进行传输

## 💛 仓储层
>[!quote] 仓储
>仓储 Repository 位于 `Mapper 层`，和 `Service 层` 之间，目的就是<u>解耦 `domain 层` 和 `infrastructure 层`</u>
>
>![650](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202406301405963.png)

- `domain` 
	- 【model】
	- 【repository】
		- IStrategyRepository
	- 【service】
		- IStrategyService：IStrategyService 需要访问数据库，那就通过 IStrategyRepository 访问

---

- `infrastructure` 
	- 【mapper】
		- IStrategyMapper
	- 【repository】
		- StrategyRepository：StrategyRepository 实现了 IStrategyRepository 接口；调用了 IStrategyMapper

## 💛 基础层
- `infrastructure` **基础层**，包含了数据库，缓存，网关，第三方工具…… ==Mapper==
	- `Mapper` 
	- `PO` 
	- `redis` 
	- `repository` 使用 `@Repository` 标记

# ❤ 扩展
微服务创始人说过：
- **单体架构优先**：单体架构能用，不要用微服务
- **项目不要一开始就构建微服务**：所有成功的微服务案例，都是从单体架构演变的【因为你只有做好了单体架构，你才熟悉业务流程，知道哪块臃肿了，要拆出去，如果一上来就微服务，一不下心拆错了，后期就难改了】


>[!hint] 除非你的系统过于复杂，无法作为单体进行管理，否则就不要考虑微服务





















