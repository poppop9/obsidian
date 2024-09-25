
# 分库分表概念
>[!hint] 如果一个系统可以预测将来数据量会很大，那么在一开始开发就可以上分库分表，因为技术已经成熟了

<u>分库分表</u> ：❓
- 垂直分库：DB【表1，表2】 -> DB1【表1】，DB2【表2】
- 水平分库：DB【表1】 -> DB【表1，表2，表3，表4】


# ShardingSphere 架构
ShardingSphere 包括：
- ShardingSphere-JDBC 客户端分库分表
- ShardingSphere-Proxy 服务端分库分表，是一个独立部署的项目，而 Java 项目不是直接操作数据库了，而是操作 ShardingSphere-Proxy，再由 ShardingSphere-Proxy 操作数据库


# ShardingSphere-JDBC





