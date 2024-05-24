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
>MyBatis 偏向于定制化开发，MyBatis Plus 也不是用来替换 MyBatis 的，是在 MyBatis 的基础上提供的一套增强功能，<u>而且只适合单表的 CRUD</u>，对于多表还是需要手写 SQL 语句

# 常用注解
>[!hint] MyBatis Plus 中的默认处理方式
> - MP 默认会把实体类名的驼峰命名转下划线作为表名【~~UserInfo 转为 user_info~~】
> - 实体类的变量名驼峰命名转下划线作为字段名
> - 名为 id 的变量作为主键

## 加在实体类上
- `@TableName("表明")` 指定表名
```java
@TableName("user")
public class User {……}
```

---

- `@TableId` 
	- `value` 指定主键字段名
	- `type`
		- `IdType.AUTO` 表示数据库表的主键是自增长的
		- `IdType.INPUT` 表示数据库表的主键由程序员自己定义
		- `IdType.ASSIGN_ID` 表示数据库表的主键由雪花算法自动生成【**默认**】

```java
public class UserEntity {
    @TableId(value = "id", type = IdType.AUTO)
    private Long userId;
}
```

---

- `@TableField` 指定其他字段名

>[!warning] 以下情况，一定要加 `@TableField`
>- 由于 MP 的机制，如果实体类中的某个属性名是以 `is` 开头的，那一定要指定 `@TableField` ，因为在反射处理时会去掉 `is`
>- 实体类中的属性名是数据库的关键字【~~比如 `order`~~】时
>- 实体类中的属性名不是数据库中的字段

```java
public class User {
    @TableField("is_married")
    private Boolean isMarried;

	// 此处要加''
	@TableField("'order'")
	private Integer order;

	// 该属性不是数据库字段
	@TableField(exist = false)
	private String address
}
```

# 常用配置
>[!hint] 大部分配置都是默认的，不用自己配，除非特殊需求要用到

```yml
mybatis-plus:
  mapper-locations: classpath:/mapper/*.xml  # 指定Mapper XML文件的位置
  type-aliases-package: com.yourpackage.domain  # 指定所有实体类的所在包
  global-config:
    db-config:
      id-type: AUTO  # 全局的主键策略
      insert-strategy: NOT_NULL  # 插入策略，只插入非空字段
      update-strategy: NOT_NULL  # 更新策略
      select-strategy: NOT_NULL  # 查询策略
      logic-delete-value: 1  # 逻辑已删除值(默认为 1)
      logic-not-delete-value: 0  # 逻辑未删除值(默认为 0)
    banner: false  # 是否显示MyBatis Plus启动横幅
  configuration:
    map-underscore-to-camel-case: true  # 是否开启自动驼峰命名规则
    cache-enabled: false  # 是否开启二级缓存
    log-impl: org.apache.ibatis.logging.slf4j.Slf4jImpl  # 打印操作的日志
    jdbc-type-for-null: 'null'  # 指定JDBC的null类型
  settings:
    use-generated-keys: true  # 是否使用数据库自增主键
    use-column-label: true  # 使用列标签代替列名
    log-execute-time: 100  # 执行慢的SQL阈值
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl  # 打印SQL日志的实现类
```





# 单表增删改查
- 配置 yml 文件
```yml
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/security
    username: root
    password: ……
```

- 定义实体类，并使用 `@TableName` 指定表名
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

# 核心功能
## 条件构造器



## 自定义 SQL



## Service 接口




















