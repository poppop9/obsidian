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

# AOP


































