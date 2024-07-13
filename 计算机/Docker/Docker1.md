

# Docker 命令
## 操作镜像
```mermaid
graph LR
	a[jar 包]--build-->b[镜像]
	b--save-->c[tar 包]
	c--load-->b
	
	d[远程仓库]--pull-->b
	b--push-->d
```

- **创建**
	- `docker build Dockerfile所在的目录` 根据 Dockerfile 构建镜像
		- `-t 镜像名称:版本号` 指定镜像名，和<u>版本号</u>【不指定默认为 latest】
- **获取/推送**
	- 从 tar 包获取/打包
		- `docker save -o 文件名 镜像名` 把一个镜像保存为一个 `tar 文件`
		- `docker load -i 文件名` 从文件中导入一个镜像
	- 从远程仓库获取/推送
		- `docker push` 
		- `docker pull 镜像名` 从远程的 Docker 镜像仓库中下载 Docker 镜像到本地
- **查看**
	- `docker images` 列出本地上所有的 Docker 镜像
- **删除**
	- `docker rmi 镜像名:版本号` 删除本地上的镜像

```bash
# . 表示Dockerfile就在当前目录
docker build -t demo:1.0 .
```

```bash
# save，load
docker save -o my_mysql.tar my_mysql

docker load -i my_mysql.tar
```

## 操作容器
```mermaid
graph TB
	a[本地镜像]--docker run 创建运行-->b[运行中容器]

	subgraph 容器
		subgraph 容器状态
			b--docker stop-->c[停止中容器]
		end
	end

	c--docker start-->b
	d[操作者]--docker ps 查看-->容器状态
	容器--docker rm-->g[垃圾箱]
```

---

>[!hint] 运行 `docker run 镜像名称` 如果本地没有镜像，会自动去镜像仓库下载

- **创建并运行**：`docker run ……参数 镜像名称:[版本号]` 【**版本号不写默认最新版**】
	- `-d` 在后台运行
	- `--name 容器名字` 设置容器的名字
	- `-p 主机端口号:容器端口号` 将<u>容器的端口</u>映射到<u>主机的端口</u>
	- `-e key=value` 配置环境变量【比如 MySQL 的账号密码，时区……】
	- `-v 数据卷名:绝对容器内的目录` 挂载数据卷 ^131b42
	- `-v 绝对本地目录:绝对容器内的目录` 将容器内目录直接挂载到本地目录【不用数据卷】 ^ca483a
	- `--privileged=true` 可以让容器操作宿主机【不推荐使用】
	- `--restart=always` 如果容器停止，总是重新启动容器

```bash
docker run -d --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -p 3306:3306 mysql:5.7
```

---

- **启动/停止**
	- `docker restart 容器名` 重启某个容器，可以重新加载配置文件
	- `docker stop 容器名` 停止正在运行的 Docker 容器【**但是容器还在，没有删除**】
	- `docker start 容器名` 启动被停止的 Docker 容器
- **查看**
	- `docker ps` 列出当前正在运行的 Docker 容器
		- `-a` 查看所有容器【包括停止的】
	- `docker inspect 容器名` 详细的查看某个容器的信息【某个容器数据卷挂载的情况……】
	- `docker logs 容器名` 获取和查看 Docker 容器的日志
		- `-f` 持续跟进日志
	- `docker top 容器名` 查看容器内运行的进程，及其 PID
	- `docker stats 容器名` 查看容器的实时资源使用情况，包括 CPU，内存，IO ……
- **删除**
	- `docker rm` 删除停止的容器
		- `-f` 强制删除【可以删除正在运行的容器】

---

>[!hint] 容器就是虚拟了一个计算机，我们可以进入容器，去修改里面文件系统中的文件

- **进入容器**：`docker exec [参数] 容器名 [命令]` 可以进入到容器的内部，来修改容器
	- 参数
		- `-i` 允许提供输入给容器内部
		- `-t` 分配一个伪终端
	- 命令
		- `bash` 在容器中打开一个交互式的 bash shell
		- `ls` 查看目录
		- ……

```bash
docker exec -it my_container bash
```

## 挂载
### 复制
- `docker cp 容器名:容器内文件 宿主机文件` 将容器内的文件复制到宿主机上

### 数据卷
>[!warning] 容器创建之后不能再挂载数据卷，只能在 `docker run` 的时候就挂载

```mermaid
graph LR
	a[宿主机目录]---->b[数据卷]
	b-->a
	b---->c[容器内目录]
	c-->b
```

---

- `docker volume create` 创建数据卷

- [[#^131b42]] ，挂载数据卷时，如果没有数据卷，会自动创建数据卷

```bash
docker run -d --name nginx -p 80:80 -v html:/usr/share/nginx/html nginx
```

- 查看
	- `docker volume ls` 查看所有数据卷
	- `docker volume inspect 数据卷名` 查看某个数据卷的详情【数据卷在宿主机的目录，……】
- 删除
	- `docker volume rm` 删除指定数据卷
	- `docker volume prune` 删除未使用的数据卷

### 本地目录
具体操作：[[#^ca483a]]

```bash
docker run -d --name mysql -p 3306:3306 -e TZ=Asia/Shanghai -e MYSQL_ROOT_PASSWORD=13433026660 -v ./mysql/data:/var/lib/mysql -v ./mysql/conf:/etc/mysql/conf.d -v ./mysql/init:/docker-entrypoint-initdb.d mysql
```




---

For a better experience on WSL, consider enabling the WSL [autoMemoryReclaim 3](https://learn.microsoft.com/en-us/windows/wsl/wsl-config) setting available since WSL 1.3.10 (experimental).

This feature causes the Windows host to better reclaim unused memory inside the WSL virtual machine, thereby resulting in better memory availability to other host applications. This is particularly helpful with Docker Desktop, since otherwise the WSL VM may consume large amounts (GBs) of memory in the Linux kernel’s page cache as Docker builds container images, without ever returning that memory to the host when it becomes unused inside the VM.

感觉你可以尝试下在 .wslconfig 文件里加上如下配置：
`[experimental] autoMemoryReclaim=dropcache`








