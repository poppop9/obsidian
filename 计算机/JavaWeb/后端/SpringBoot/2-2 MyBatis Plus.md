```xml
<!-- 这个依赖也集成了 MyBatis -->
<!-- Spring 2 -->
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-boot-starter</artifactId>
    <version>3.5.6</version>
</dependency>

<!-- Spring 3 -->
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-spring-boot3-starter</artifactId>
    <version>3.5.6</version>
</dependency>
```

>[!quote] MyBatis Plus
>MyBatis 偏向于定制化开发，MyBatis Plus 不是用来替换 MyBatis 的，是在 MyBatis 的基础上提供的一套增强功能

# 具体操作
- 配置 yml 文件
```yml
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/security
    username: root
    password: ……
```

- 定义实体类
```java
package com.example.Pojo;  

@Data  
@NoArgsConstructor  
@AllArgsConstructor  
// 定义实体类对应的数据库中的表名
@TableName("user")  
public class userPlus {  
    private Long userId;       // 用户ID  
    private String userName;   // 用户名  
    private String userPassword; // 用户密码  
    private Integer userAuthority; // 用户权限  
}
```

- 让 Mapper 继承 `BaseMapper<实体类>` 
```java
@Mapper
public interface UserMapperPlus extends BaseMapper<userPlus> {}
```

>[!quote]+ `BaseMapper<T>`
>`BaseMapper<T>` 里面定义了常用的<u>增删改查</u>代码
>
>- **增**
> 	- `insertSelective(T record)`: 插入一条记录（选择字段，策略插入）
> - **删**
> 	- `deleteById(Serializable id)`: 根据 ID 删除
> 	- `deleteByMap(@Param("et") T entity)`: 根据 column 删除
> - **改**
> 	- `updateById(@Param("et") T record)`: 根据 ID 修改
> 	- `updateSelectiveById(@Param("et") T record)`: 根据 ID 修改（选择字段）
> - **查**
> 	- `selectById(Serializable id)`: 根据 ID 查询
> 	- `selectBatchIds(@Param("ids") Collection<? extends Serializable> idList)`: 查询（根据 ID 批量查询）
> 	- `selectByMap(@Param("ew") Wrapper<T> example)`: 查询（根据 column 查询）
> 	- `selectCount(@Param("ew") Wrapper<T> example)`: 总记录数
> 	- `selectCountByMap(@Param("ew") T entity)`: 总记录数（根据 column 查询）
> 	- `selectList(@Param("ew") Wrapper<T> example)`: 查询列表
> 	- `selectMapsPage(@Param("current") int current, @Param("size") int size, @Param("ew") Wrapper<T> example)`: 根据 column 统计
> 	- `selectMaps(@Param("ew") Wrapper<T> example)`: 根据 column 统计（不分页）
> 	- `selectObjs(@Param("ew") Wrapper<T> example)`: 根据 column 统计（统计字段为 ID）
> 	- `selectObjsByPage(@Param("current") int current, @Param("size") int size, @Param("ew") Wrapper<T> example)`: 根据 column 统计（统计字段为 ID，不分页）
> 	- `selectObjsNotNull(@Param("ew") Wrapper<T> example)`: 根据 column 统计（统计字段为 ID，不分页）
> 	- `selectOne(@Param("ew") Wrapper<T> example)`: 根据 column 统计（统计字段为 ID，不分页）
> 	- `selectList(Wrapper<T> queryWrapper)`: 查询所有记录

- 测试
```java
package com.example;

@RunWith(SpringRunner.class)
@SpringBootTest
public class MyBatisPlusTest {
    @Autowired
    private UserMapperPlus userMapperPlus;

    @Test
    public void testSelect() {
        System.out.println(("----- selectAll method test ------"));
        List<userPlus> userPluses = userMapperPlus.selectList(null);
        userPluses.forEach(System.out::println);
    }
}

---
userPlus(userId=1, userName=kite, userPassword=$2a$10$NP/SbcLek9Q8hemltyG024K, userAuthority=1)
userPlus(userId=2, userName=nelson, userPassword=Fra, userAuthority=1)
```


















