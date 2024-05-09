# 事务管理
>与 `Mysql` 中相同，事务是一组操作，要么同时成功，要么同时失败

在接口，类，方法上添加 `@Transactional` ，将<u>接口</u>【该接口下的所有实现类的所有方法】，<u>类</u>【该类下的所有方法】，<u>方法</u>交给 Spring 进行事务管理

>[!warning] 事务管理一般添加在 `Service 层`，用于处理多个数据操作

```java
@Service
public class DancerService implements com.example.service.DancerService {
    @Autowired
    private DancerMapper DancerMapper;

    @Override
    @Transactional
    public void DeleteDanceType(Integer id) {
	    // 删除舞种表
        DancerMapper.DeleteDanceType(id);  
        // 可能出现异常
        // 删除对应舞种的舞者
        DancerMapper.DeleteDancer(id);
    }
}
```

## rollbackFor
>事务管理默认只在 `RuntimeException 运行时异常` 出现时才事务回滚，我们可以使用 `rollbackFor` 来指定什么异常需要回滚

```java
@Override
@Transactional(rollbackFor = Exception.class)  // 此处指定所有异常都回滚
public void DeleteDanceType(Integer id) {
	……
}
```

## propagation
>用于指定<u>当事务嵌套了</u>，该如何处理事务

| 传播属性             | 描述                                     |
| ---------------- | -------------------------------------- |
| **REQUIRED**【默认】 | 如果当前没有事务，则新建一个事务；如果已经存在一个事务中，则加入到这个事务中 |
| SUPPORTS         | 如果当前存在事务，则加入该事务；如果没有，就以非事务方式执行         |
| MANDATORY        | 强制要求存在一个事务，否则抛出异常                      |
| **REQUIRES_NEW** | 新建一个事务，如果当前存在事务，则挂起该事务                 |
| NOT_SUPPORTED    | 以非事务方式执行操作，如果当前存在事务，则挂起该事务             |
| NEVER            | 以非事务方式执行操作，如果当前存在事务，则抛出异常              |
| NESTED           | 如果当前存在事务，则在嵌套事务内执行；如果没有，就新建一个事务        |

### REQUIRED
```java
@Transactional
public void workA (){
	try {
		C
		……异常
		D
	} finally {
		// 此处一般用来记录日志
		// 在 B 类中已经给 workB 这个方法加入了事务
		B.workB();
	}
}
```

![500](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402291623087.png)

### REQUIRES_NEW
```java
@Transactional(propagation = Propagation.REQUIRES_NEW)
public void workA (){
	try {
		C
		……异常
		D
	} finally {
		// 此处一般用来记录日志
		// 这个方法在 B 中加入了事务
		B.workB();
	}
}
```

![900](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402291632083.png)

>[!hint] 事务管理 的底层就是 AOP

# AOP
>[!quote] AOP
>AOP 是面向切面编程。当你想操作项目中的所有方法时【比如<u>计算各个方法的耗时</u>，<u>记录方法的参数，返回值</u>，<u>权限控制</u>】，可以不用一个一个添加，而是可以在 AOP 中统一管理
> - 代码无侵入【无需修改原有代码，就可以增强功能】
> - 维护方便
> - 减少重复代码

>[!hint] 当某个方法被 AOP 控制后，将不再运行原始目标对象，而是会生成一个基于原始目标对象的<u>动态代理对象</u>【这个对象中会自动加入 AOP 增强后的功能】

## 概念
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403021349901.png)

### 连接点
>可以被 AOP 控制的所有方法，在 AOP 类中可以使用连接点获取<u>相关信息</u>【目标对象的类名，方法名，方法参数……】

- 对于 `@Around`，连接点对象为 `ProceedingJoinPoint`
```java
public Object recordTime(ProceedingJoinPoint joinPoint) {
	……
}
```

- 对于其它四种通知类型，连接点对象为 `JoinPoint`
```java
public void AfterReturning(JoinPoint joinPoint) {
	……
}
```
### 切入点
>被 AOP 声明为要控制的方法

#### 表达式
- `execution((方法修饰符) 返回值 包名.类名.方法名(方法参数) (throws 异常))`
	- `*` 可以通配任意类型的一个参数，`execution(* 包名.类名.update*(*)` 匹配任意返回值的，指定包名类名下，以 `update` 开头的只能有一个任意类型参数的方法
	- `..` 通配任意数量的任意类型参数，`execution(* com..类名.update(..)` 匹配任意返回值的，com包下任意层级的指定类名的 `update(..)` 方法
- `@annotation(……)` **用于标识带有特定注解的方法**

>[!hint] 多个表达式条件可以使用 `+` 连接

>[!hint] 切入点的表达式尽量基于接口描述

### 目标对象
>某个对象里有方法被 AOP 声明为要控制了，那这个对象就是目标对象

### 通知
>也就是具体的工作内容，要从切入点怎么切入，也就是切面类中定义的方法内容

通知的类型有 <u>5</u> 种：
- `@Around` 围绕目标方法执行，通知方法在目标方法的前，后都执行。**必须指定返回值为 `Object`，来接收原始方法的返回值**
- `@Before` 在目标方法执行之前执行
- `@AfterReturning` 在目标方法正常完成后执行
- `@After` 在目标方法完成后执行，无论是否发生异常
- `@AfterThrowing` 在目标方法抛出异常后才会执行

>[!warning] 后 4 种方法无需考虑目标方法的执行

### 切面
>切面 = 切入点 + 通知

## 引入依赖
```xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-aop</artifactId>  
</dependency>
```

## 通知顺序
当多个切面类中的切入点相同时，<u>默认</u>：在 `Before` 通知类型时优先执行类名靠前的 AOP 类；在 `After` 通知类型时，优先执行类名靠后的 AOP 类

### 自定义通知顺序
>在 AOP 类前加上 `@Order(*)` 注解，**数字越小，`Before` 通知类型越先执行，`After` 通知类型越后执行**

```java
@Component  // 交给IOC容器管理
@Aspect    // 声明为aop类
@Order(3) 
public class TimeAspect {
	……
}
```

## 例子
### 计算各个方法的耗时
- 创建 aop 包，aop 类
```java
package com.example.spring_aop.aop;

@Component  // 交给IOC容器管理
@Aspect    // 声明为aop类
public class TimeAspect {
	// 拦截 com.example.spring_aop.controller 包下的所有类的所有方法，并且这些方法可以有任意数量的参数（..），且方法的返回值可以任意（*）
    @Around("execution(* com.example.spring_aop.controller.*.*(..))")
    // 原始方法执行可能有返回值，所以定义返回值为 Object
    public Object recordTime(ProceedingJoinPoint joinPoint) throws Throwable {
        // 记录开始时间
        long start = System.currentTimeMillis();

        // 调用原始方法，比如调用recordTime()的是A方法，那么joinPoint.proceed()就是A方法
        Object proceed = joinPoint.proceed();

        // 记录结束时间，计算耗时
        long end = System.currentTimeMillis();
        System.out.println(joinPoint.getSignature() + "耗时：" + (end - start) + "ms");

        return proceed;
    }
}
```

### 在各个方法运行结束，打印方法名
```java
package com.example.spring_aop.aop;

@Component
@Aspect
public class NameAspect {
    @AfterReturning("execution(* com.example.spring_aop.controller.*.*(..))")
    // 获取到连接点对象
    public void AfterReturning(JoinPoint joinPoint) throws Throwable {
        System.out.println(joinPoint.getSignature().getName());
    }
}
```

































