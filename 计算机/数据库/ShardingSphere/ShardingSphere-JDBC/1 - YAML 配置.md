https://shardingsphere.apache.org/document/current/cn/user-manual/shardingsphere-jdbc/yaml-config/

ShardingSphere-JDBC 的 YAML 配置文件组成 ：
- 逻辑数据库
- 运行模式
- 数据源
- 规则
- 属性配置

# 逻辑数据库
![](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/20240928150157.png)

```yml
# 逻辑数据库名
databaseName: logic_db
```

# 运行模式
<u>单机模式</u> ：
```yml
mode:
  type: Standalone
  repository:
    type: JDBC
    props: 
	  provider: MySQL 
	  jdbc_url: jdbc:mysql://localhost:3306/security
	  username: root
	  password: 134
```

---

<u>集群模式</u> ：**推荐使用集群模式**，并**推荐使用 ZooKeeper**
- 引入持久化仓库依赖
```yml
<dependency>
    <groupId>org.apache.shardingsphere</groupId>
    <artifactId>shardingsphere-cluster-mode-repository-zookeeper</artifactId>
    <version>5.5.0</version>
</dependency>
```

```yml
mode:
  type: Cluster
  repository:
    type: ZooKeeper  # 持久化仓库类型
    props:
      namespace: governance_ds  # 注册中心命名空间
      server-lists: localhost:2181  # 注册中心连接地址
      retryIntervalMilliseconds: 500
      timeToLiveSeconds: 60
      maxRetries: 3
      operationTimeoutMilliseconds: 500
```

# 数据源
```yml
# 数据源配置
dataSources:
  ds_0:
    driverClassName: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/ds_0
    username: root
    password: root
  ds_1:
    driverClassName: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/ds_1
    username: root
    password: root
```

# 规则
## 数据分片
- `databaseStrategy` 分库策略
	- none ~~默认~~，不分片
	- standard 单分片键的标准分片场景
		- `shardingColumn` 指定用于分片的列名称
		- `shardingAlgorithmName` 分片算法名称
	- complex 多分片键的复合分片场景
		- `shardingColumns` 多个列名，用逗号分隔
		- `shardingAlgorithmName` 分片算法名称
	- hint 动态选择分片
		- `shardingAlgorithmName` 分片算法名称
- `tableStrategy` 分表策略，属性同分库策略
- `keyGenerateStrategy` 主键生成策略，**会与 ORM 框架有冲突，建议不配置**
	- column 主键列名
	- keyGeneratorName 算法名
- `auditStrategy` 分片审计策略 ：确保每次数据的修改、插入或删除操作都有记录，便于事后审查和追踪
	- auditorNames 审计算法
	- allowHintDisable 












