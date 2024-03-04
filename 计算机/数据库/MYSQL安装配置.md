## 官网下载MySQL
- [下载Mysql](https://dev.mysql.com/downloads/mysql/)
![点击Download|700](https://img-blog.csdnimg.cn/2021052417324674.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzU3OTAxNQ==,size_16,color_FFFFFF,t_70)
- 下载完成后解压到某一个文件夹
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210524173506685.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzU3OTAxNQ==,size_16,color_FFFFFF,t_70)
## 配置初始化文件my.ini
在安装文件的根目录下创建一个txt文件，名字叫my，文件后缀为ini
之后复制下面这个代码放在my.ini里
***以下代码除安装目录和数据的存放目录需修改，其余不用修改***

```
[mysqld]
## 设置3306端口
port=3306
## 设置mysql的安装目录   ----------是你的文件路径-------------
basedir=E:\mysql\mysql
## 设置mysql数据库的数据的存放目录  ---------是你的文件路径data文件夹自行创建
datadir=E:\mysql\mysql\data
## 允许最大连接数
max_connections=200
## 允许连接失败的次数。
max_connect_errors=10
## 服务端使用的字符集默认为utf8mb4
character-set-server=utf8mb4
## 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
## 默认使用“mysql_native_password”插件认证
#mysql_native_password
default_authentication_plugin=mysql_native_password
[mysql]
## 设置mysql客户端默认字符集
default-character-set=utf8mb4
[client]
## 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8mb4
```
## 初始化MySQL
使用**管理员**身份运行CMD
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210524174426362.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzU3OTAxNQ==,size_16,color_FFFFFF,t_70)-
进入mysql的bin目录
`cd E:\mysql\mysql\bin\`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210524174552515.png)-
在MySQL目录下的bin目录下执行命令：
`mysqld --initialize --console`
复制root@localhost:之后的密码到本地文件夹，保存好( **: 后有一个空格，不复制**)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210525093717642.png)
## 安装mysql服务并启动+修改密码
### 安装mysql服务
`mysqld --install mysql`
之后会提示服务已经成功安装-
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210525093910256.png)
### 启动mysql服务
`net start mysql`
**输入之后提示以下内容**-
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210525094002685.png)
### 连接mysql
`mysql -uroot -p`
**输入之后去复制一下刚刚保存下来的密码，并粘贴到命令台**-
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021052509403911.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzU3OTAxNQ==,size_16,color_FFFFFF,t_70)-
输入以下命令修改密码(把新的密码修改成你想要的密码)
`ALTER USER 'root'@'localhost' IDENTIFIED BY '新的密码';`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210525094411413.png)-
**密码修改完成**
## 配置环境变量
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210525100357202.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzU3OTAxNQ==,size_16,color_FFFFFF,t_70)-
在path中加入以下代码
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021052510042863.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzU3OTAxNQ==,size_16,color_FFFFFF,t_70)
## 使用连接工具连接mysql
### 打开DataGrip之后按照以下步骤添加数据库
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210531154902665.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzU3OTAxNQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210531155954575.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzU3OTAxNQ==,size_16,color_FFFFFF,t_70)
### 输入 show databases之后查看结果
出现如下结果则**配置成功**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210531160620941.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzU3OTAxNQ==,size_16,color_FFFFFF,t_70)
## 疑难杂病
### 执行mysqld --install mysql时提示该服务已存在
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210525095818371.png)-
就先删除该服务（使用以下代码）
`sc delete mysql`
然后在执行mysqld --install mysql

### cmd运行net start mysql发生系统错误193 *** 不是有效的 Win32 应用程序。
报错：
发生系统错误193 *** 不是有效的 Win32 应用程序

删除bin目录下0KB的mysqld文件

启动成功！

---

