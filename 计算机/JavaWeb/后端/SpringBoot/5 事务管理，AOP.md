# 事务管理
>与 `Mysql` 中相同，事务是一组操作，要么同时成功，要么同时失败

在接口，类，方法上添加 `@Transactional注解` ，将<u>接口</u>【该接口下的所有实现类的所有方法都是事务】，<u>类</u>【该类下的所有方法都是事务】，<u>方法</u>交给 Spring 进行事务管理

>[!warning] 事务管理一般添加在 `Service逻辑层`，用于处理多个数据操作

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
>事务管理默认只在 `RuntimeException运行时异常` 出现时才事务回滚，我们可以使用 `rollbackFor属性` 用来指定什么异常需要回滚

```java
@Override
@Transactional(rollbackFor = Exception.class)  // 此处指定所有异常都回滚
public void DeleteDanceType(Integer id) {
	……
}
```

## propagation
>用于指定<u>当事务嵌套了</u>该如何处理事务

| 传播属性               | 描述                                     |
| ------------------ | -------------------------------------- |
| ***REQUIRED***【默认】 | 如果当前没有事务，则新建一个事务；如果已经存在一个事务中，则加入到这个事务中 |
| SUPPORTS           | 如果当前存在事务，则加入该事务；如果没有，就以非事务方式执行         |
| MANDATORY          | 强制要求存在一个事务，否则抛出异常                      |
| ***REQUIRES_NEW*** | 新建一个事务，如果当前存在事务，则挂起该事务                 |
| NOT_SUPPORTED      | 以非事务方式执行操作，如果当前存在事务，则挂起该事务             |
| NEVER              | 以非事务方式执行操作，如果当前存在事务，则抛出异常              |
| NESTED             | 如果当前存在事务，则在嵌套事务内执行；如果没有，就新建一个事务        |

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
		// 在B类中已经给workB这个方法加入了事务
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
		// 这个方法在B中加入了事务
		B.workB();
	}
}
```

![900](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402291632083.png)

>[!hint] 事务管理 的底层就是 AOP

# AOP
>AOP 是面向切面编程。当你想操作项目中的所有方法时【比如<u>计算各个方法的耗时</u>，<u>记录方法的参数，返回值</u>，<u>权限控制</u>】，你可以不用一个一个添加，而是可以在 AOP 中统一管理

- 代码无侵入【无需修改原有代码，就可以增强功能】
- 维护方便
- 减少重复代码

>[!hint] 当某个方法被 AOP 控制后，将不再运行原始目标对象，而是会生成一个基于原始目标对象的<u>动态代理对象</u>【这个对象中会自动加入 AOP 增强后的功能】

## 概念
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202403021349901.png)

>[!quote] 连接点 JoinPoint
>可以被 AOP 控制的所有方法

>[!quote] 切入点 PointCut
>被 AOP 声明为要控制的方法

>[!quote] 目标对象 Target
>某个对象里有方法被 AOP 声明为要控制了，那这个对象就是目标对象

>[!quote] 通知 Advice
>也就是具体的工作内容，要从切入点怎么切入，也就是切面类中定义的方法内容
>
>通知的类型有 <u>5</u> 种：
>- `@Around` 围绕目标方法执行，通知方法在目标方法的前，后都执行
>- `@Before` 在目标方法执行之前执行
>- `@AfterReturning` 在目标方法正常完成后执行
>- `@After` 无论目标方法如何结束，都将执行
>- `@AfterThrowing` 在目标方法抛出异常后执行

>[!quote] 切面 Aspect
>切面 = 切入点 + 通知

## 引入依赖
```xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-aop</artifactId>  
</dependency>
```

## 计算各个方法的耗时
- 创建 aop包，aop类【`Component`，`Aspect`，`Around`】
```java
package com.example.spring_aop.aop;

@Component  // 交给IOC容器管理
@Aspect    // 声明为aop类
public class TimeAspect {
	// 拦截 com.example.spring_aop.controller 包下的所有类的所有方法，并且这些方法可以有任意数量的参数（..），且方法的返回值可以任意（*）
    @Around("execution(* com.example.spring_aop.controller.*.*(..))")
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

































