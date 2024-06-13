```xml
<!-- 以下依赖也集成了 MyBatis -->
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

- `@TableId` 指定主键
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

# 核心功能
## 简单 CRUD
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
> 	- `insertSelective(T record)` 插入一条记录（选择字段，策略插入）
> - **删**
> 	- `deleteById(Serializable id)` 根据 ID 删除
> 	- `deleteByMap(@Param("et") T entity)` 根据 column 删除
> - **改**
> 	- `updateById(@Param("et") T record)` 根据 ID 修改
> - **查**
> 	- `selectById(Serializable id)` 根据 ID 查询
> 	- `selectBatchIds(Collection<? extends Serializable> idList)` 根据 ID 集合来批量查询
> 	- `selectByMap(@Param("ew") Wrapper<T> example)` 查询（根据 column 查询）
> 	- `selectCount(@Param("ew") Wrapper<T> example)` 总记录数
> 	- `selectCountByMap(@Param("ew") T entity)` 总记录数（根据 column 查询）
> 	- `selectMapsPage(@Param("current") int current, @Param("size") int size, @Param("ew") Wrapper<T> example)` 根据 column 统计
> 	- `selectMaps(@Param("ew") Wrapper<T> example)` 根据 column 统计（不分页）
> 	- `selectObjs(@Param("ew") Wrapper<T> example)` 根据 column 统计（统计字段为 ID）
> 	- `selectObjsByPage(@Param("current") int current, @Param("size") int size, @Param("ew") Wrapper<T> example)` 根据 column 统计（统计字段为 ID，不分页）
> 	- `selectObjsNotNull(@Param("ew") Wrapper<T> example)` 根据 column 统计（统计字段为 ID，不分页）
> 	- `selectOne(@Param("ew") Wrapper<T> example)` 根据 column 统计（统计字段为 ID，不分页）

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

## 条件构造器
>[!quote] 条件构造器 Wrapper
>>条件构造器 Wrapper 可以构造 `WHERE` 条件，进行条件性地 RUD
>
>**继承体系**：
> - `AbstractWrapper` 
> 	- `QueryWrapper` 专门用于 RD 操作，可以添加各种查询条件
> 	- `UpdateWrapper` 用于 U 操作，可以添加更新条件和更新的字段值，<u>可以在不创建实体对象的情况下，直接设置更新字段和条件</u>
> 	- `LambdaQueryWrapper` 
> 	- `LambdaUpdateWrapper` 

>[!hint] 推荐使用 `LambdaQueryWrapper` ，`LambdaUpdateWrapper`
>- 防止硬编码：字段名直接从实体类属性中引用，不需要自己指定
>- 类型安全：在编译期间，就可以保证实体类中的属性的数据类型和传入的数据一致
>
> ```java
> // Lambda条件查询  
> @Test  
> public void testSelectLambdaWrapper() {  
>     LambdaQueryWrapper\<User> lambdaQueryWrapper = new LambdaQueryWrapper\<User>()  
> 		    // 使用方法引用获取字段名，防止硬编码
>             .select(User::getUserName, User::getUserPassword)  
>             .like(User::getUserPassword, "K");  
>   
>     userMapper.selectList(lambdaQueryWrapper).forEach(System.out::println);  
> }
> ```

---

>[!quote] 在 BaseMapper 中需要传入 Wrapper 参数的方法
>- **增**
>	- `update(修改后的实体类对象, Wrapper wrapper)` <u>实体类中未设置的参数，不更改</u>
>- **查**
>	- `selectList(Wrapper<T> example)` 查询列表，<u>传入参数为 null，则是查询整个表</u>

### QueryWrapper
- **大小等**
	- `eq("数据库字段", 条件值)` 设置单个字段的相等条件
	- `nq()` 设置单个字段的不相等条件
	- `gt()` 设置单个字段的大于条件 【~~greater than~~】
	- `ge()` 设置单个字段的大于等于条件
	- `lt()` 设置单个字段的小于条件
	- `le()` 设置单个字段的小于等于条件
- **范围**
	- `between("数据库字段", 值1, 值2)` 设置单个字段的 BETWEEN 条件
	- `notBetween(……)` 
- **模糊匹配**
	- `like()` 设置单个字段的 LIKE 条件
	- `notLike()` 
	- `likeLeft()` 设置单个字段的左模糊匹配条件
- `isNull("数据库字段")` 判断单个字段的 IS NULL 
- `in("字段", 集合)` 设置单个字段的 IN 条件【~~字段的值在给定的集合中~~】

```java
// 更新用户权限  
@Test  
public void testUpdateUser() {  
    User user = new User();  
    user.setUserAuthority(2);  
  
    QueryWrapper<User> queryWrapper = new QueryWrapper<User>()  
            .eq("user_id", 1);  
  
    userMapper.update(user, queryWrapper);  
}

---
将id为1的行，的authority修改为2
```

```java
// 条件查询
@Test
public void testSelectWrapper() {
	QueryWrapper<User> queryWrapper = new QueryWrapper<User>()
			.select("user_name", "user_password")
			.like("user_password", "K");

	userMapper.selectList(queryWrapper).forEach(System.out::println);
}

---
User(userId=null, userName=jaygee, userPassword=Korea, userAuthority=null)
User(userId=null, userName=Hoan, userPassword=Korea, userAuthority=null)
```

### UpdateWrapper
如果在 `UPDATE` 时，`SET` 的条件是<u>动态的</u>【~~例如，某个字段减 200，而不是说设置某个字段为固定的值~~】，那就需要使用 `UpdateWrapper`

```java
// UpdateWrapper动态SET  
@Test  
public void testUpdateWrapper() {  
    UpdateWrapper<User> updateWrapper = new UpdateWrapper<User>()  
            .setSql("user_authority = user_authority - 1")  
            .eq("user_id", 1);  
  
    userMapper.update(null, updateWrapper);  
}

---
将id为 1 的行，authority字段的值减 1
```

## IService 接口
>[!quote] IService 接口
>~~由于 `Controller` 需要调 `Service` 不能直接调 `Mapper` ，所以我们引入了 `IService` 和 `ServiceImpl<Mapper, Entity>`~~ ，`IService` 接口相对于 `BaseMapper<>` 功能只多不少。<u>IService 有批处理功能，可以提高性能</u>
>
> ```java
> // UserService 实现 IService
> public interface UserService extends IService\<User> { …… }
> ```
> 
> ```java
> // UserServiceImpl 继承 ServiceImpl，这样就可以获得 ServiceImpl 里所有的方法
> @Service
> public class UserServiceImpl extends ServiceImpl<UserMapper, User>
>         implements UserService { …… }
> ```

- **增**
	- `save-` 插入
- **删**
	- `remove-` 删除
- **改**
	- `update-` 
- **查**
	- `get-` 查询单行
	- `list-` 查询集合
	- `page` 分页查询

```java

```

## 半自动 SQL
>[!quote] 半自动 SQL
>半自动 SQL 是指 sql 语句的<u>前半部分还是写在 XML 文件里</u>，而  <u>`WHERE 条件` 使用 MyBatis-Plus 来写</u>
>
>- 在开发规范中，sql 语句不能写在业务代码里，所以业务代码里只写 MP 的 WHERE 条件
>- MP 不擅长生成 sql 语句的前半部分，只擅长编写 WHERE 条件

- 测试类
```java
// 半自动sql，实现动态SET
@Test
public void testSemiAutoUpdate() {
	LambdaQueryWrapper<User> lambdaQueryWrapper = new LambdaQueryWrapper<User>()
			.eq(User::getId, 1);

	userService.increaseAuthority(lambdaQueryWrapper);
}
```

- Service 接口
```java
public interface UserService extends IService<User> {  
    void increaseAuthority(LambdaQueryWrapper<User> lambdaQueryWrapper);  
}
```

- Service 实现类
```java
@Service  
public class UserServiceImpl extends ServiceImpl<UserMapper, User> implements UserService {  
    @Autowired  
    private UserMapper userMapper;  
  
    // 将用户权限加1  
    @Override  
    public void increaseAuthority(LambdaQueryWrapper<User> lambdaQueryWrapper) {  
        userMapper.incrementAuthority(lambdaQueryWrapper);  
    }  
}
```

- Mapper
```java
@Mapper  
public interface UserMapper extends BaseMapper<User> {  
	// 将参数LambdaQueryWrapper命名为ew，方便后续xml引用
    void incrementAuthority(@Param("ew") LambdaQueryWrapper<User> lambdaQueryWrapper);  
}
```

- xml 文件
```xml
<!-- ${ew.customSqlSegment} 就是一个WHERE片段 -->
<!-- ew是传入的LambdaQueryWrapper -->
<!-- customSqlSegment是LambdaQueryWrapper里的一个属性，表示拼接的WHERE片段 -->
<update id="incrementAuthority">
	UPDATE user
	SET user_authority = user_authority + 1 ${ew.customSqlSegment}
</update>
```

## 代码生成
- 插件
	- MyBatisX
	- MyBatisPlus
	- easycode
- MP 官方的代码生成器配置代码

## 分页查询
```java
package com.example.config;

@Configuration
public class MybatisPlusConfig {
    @Bean
    public MybatisPlusInterceptor mybatisPlusInterceptor() {
        MybatisPlusInterceptor interceptor = new MybatisPlusInterceptor();
        // 如果配置多个插件, 切记分页最后添加
	    interceptor.addInnerInterceptor(new PaginationInnerInterceptor(DbType.MYSQL)); 
        // 如果有多数据源可以不配具体类型, 否则都建议配上具体的 DbType
        return interceptor;
    }
}
```
















