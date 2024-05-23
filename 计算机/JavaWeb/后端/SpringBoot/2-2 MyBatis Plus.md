```xml
<!-- 这个依赖也集成了 MyBatis -->
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-boot-starter</artifactId>
    <version>3.5.6</version>
</dependency>
```

>[!quote] MyBatis Plus
>MyBatis 偏向于定制化开发，MyBatis Plus 不是用来替换 MyBatis 的，是在 MyBatis 的基础上提供的一套增强功能

# 具体操作
- 让 Mapper 继承 `BaseMapper<实体类>` 

>[!quote] `BaseMapper<T>`
>`BaseMapper<T>` 里面定义了常用的<u>增删改查</u>代码
>
> - `insertSelective(T record)`: 插入一条记录（选择字段，策略插入）
> - `deleteById(Serializable id)`: 根据 ID 删除
> - `deleteByMap(@Param("et") T entity)`: 根据 column 删除
> - `updateById(@Param("et") T record)`: 根据 ID 修改
> - `updateSelectiveById(@Param("et") T record)`: 根据 ID 修改（选择字段）
> - `selectById(Serializable id)`: 根据 ID 查询
> - `selectBatchIds(@Param("ids") Collection<? extends Serializable> idList)`: 查询（根据 ID 批量查询）
> - `selectByMap(@Param("ew") Wrapper<T> example)`: 查询（根据 column 查询）
> - `selectCount(@Param("ew") Wrapper<T> example)`: 总记录数
> - `selectCountByMap(@Param("ew") T entity)`: 总记录数（根据 column 查询）
> - `selectList(@Param("ew") Wrapper<T> example)`: 查询列表
> - `selectMapsPage(@Param("current") int current, @Param("size") int size, @Param("ew") Wrapper<T> example)`: 根据 column 统计
> - `selectMaps(@Param("ew") Wrapper<T> example)`: 根据 column 统计（不分页）
> - `selectObjs(@Param("ew") Wrapper<T> example)`: 根据 column 统计（统计字段为 ID）
> - `selectObjsByPage(@Param("current") int current, @Param("size") int size, @Param("ew") Wrapper<T> example)`: 根据 column 统计（统计字段为 ID，不分页）
> - `selectObjsNotNull(@Param("ew") Wrapper<T> example)`: 根据 column 统计（统计字段为 ID，不分页）
> - `selectOne(@Param("ew") Wrapper<T> example)`: 根据 column 统计（统计字段为 ID，不分页）
> - `selectList(Wrapper<T> queryWrapper)`: 查询所有记录