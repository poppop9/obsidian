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

# AOP


