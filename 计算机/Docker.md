# 基本概念
## 什么是Docker
> Docker 是一个开源的容器化平台，**用于构建、部署和运行应用程序**。它提供了一种轻量级的虚拟化技术，允许将应用程序及其依赖项打包到一个<u>容器</u>中

>[!quote] 容器
>独立的运行环境

### 作用
- **容器化应用程序**：Docker 允许将应用程序及其所有依赖项打包到一个独立的容器中。容器可以在不同的环境中运行，而无需担心环境差异导致的问题，确保应用程序在任何地方都能一致运行。每个容器都是一个可隔离的、可移植的单元，具有自己的文件系统、运行时环境和资源
- **轻量级和快速启动**：与传统的虚拟机相比，Docker 容器非常轻量级，启动时间非常快
![700](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402261348445.png)
- **环境隔离**：Docker 容器提供了强大的隔离性，使应用程序可以在独立的环境中运行，互不干扰
- **可移植性**：Docker 容器可以在不同的平台和操作系统上运行，包括Linux，Windows，macOS……，这使得应用程序可以轻松地在开发、测试和生产环境之间进行迁移和部署
- **版本控制和复制**：Docker 使用镜像来构建容器。镜像是一个可重复的、可版本控制的文件，包含了应用程序的所有代码和依赖项
- **扩展性和弹性**：Docker 容器可以轻松地进行水平扩展，通过使用容器编排工具如Docker Compose，Kubernetes，可以实现自动化的容器管理和部署

## 体系结构
![900](https://obsidian-1307744200.cos.ap-guangzhou.myqcloud.com/%E5%9B%BE%E7%89%87/202402261429382.png)

### 镜像 与 容器
>[!quote] 镜像
><u>镜像</u> 是一个只读的模板

>[!quote] 容器
><u>容器</u> 是一个运行实例【类似**类与实例的关系**】
>
>- <u>容器是一个隔离的环境，我的依赖跟你的依赖不冲突</u>【比如有一个 MySQL 服务，这个服务的内部容器端口永远是 3306，但是我可以使用端口映射创建两个 MySQL 服务，`docker run -p 3306:3306`，`docker run -p 3307:3306`】

>[!quote] 仓库
><u>仓库</u> 是用来存储，分享 Docker 镜像的地方【DockerHub……】

## Docker Engine
>Docker Engine 是 Docker 的核心部分，负责构建和容器化应用程序

### 安装 Docker
>[!hint] 以下配置均在 Ubuntu 中安装

- 卸载旧版本
```bash
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

- 卸载映像，容器，卷，网络【如果需要】
```bash
# 卸载 Docker Engine、CLI、containerd 和 Docker Compose 包
sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras

# 删除所有映像、容器和卷
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```

- 使用 apt 存储库安装
```bash
# 添加 Docker 官方的 GPG 密钥
sudo apt-get update
sudo apt-get install ca-certificates curl
# 在 `/etc/apt/keyrings` 路径下创建目录，用于存放密钥环。`-m 0755` 设置了目录的权限【所有用户都可以读取或者进入该目录，只有拥有者可以写入数据】
sudo install -m 0755 -d /etc/apt/keyrings
# 下载密钥并保存到刚刚创建的目录
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
# 修改了 `docker.asc` 文件的权限，使所有用户都可以读取该文件
sudo chmod a+r /etc/apt/keyrings/docker.asc

# 让系统知道从哪里下载Docker，并确保下载的是与系统架构和版本相匹配的Docker版本
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \

sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
# 更新系统的软件包列表，这样就可以从新添加的Docker仓库中获取Docker的最新版本
sudo apt-get update
```

- 安装 Docker 包
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# 验证是否安装成功
docker version
sudo docker run hello-world
```

- 配置镜像加速 https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors
	- 进入阿里云的容器镜像服务
	- 进入镜像工具的镜像加速器
	- 根据操作文档修改

#### 额外配置
> 额外的配置可以让我们在使用 Docker 时更加方便

---

- 以非 root 用户身份管理 Docker【可以在使用 Docker 命令时，不加 `sudo`】
	- 创建 Docker 组 `sudo groupadd docker`
	- 将用户添加到 docker 组 `sudo usermod -aG docker 用户`
	- 激活对组的更改 `newgrp docker`

---

### 容器化的步骤
>[!quote] Dockerfile
>Dockerfile 是一个文本文件，里面包含一系列指令，用来告诉 Docker 如何构建镜像

- 创建一个 Dockerfile
- 使用 Dockerfile 构建镜像
- 使用镜像创建，运行容器

## Docker Compose
>如果多个容器之间需要相互关联【前端，后端，数据库，redis，负载均衡……】，那么就需要使用 Docker Compose

## Docker Desktop
>Docker Desktop = <u>Docker Engine</u> + <u>Docker Build</u> + <u>Docker Extensions</u> + <u>Docker Compose</u>

>[!warning] Linux 上安装的 Docker Desktop 会在这个 Linux 的基础上创建一个虚拟机，这个虚拟机是在 Docker Desktop 中运行的，而不是直接在 Linux 的 Docker 引擎上。所以<u>Linux 的 Docker Engine 上部署的镜像和容器</u>与<u> Linux 上安装的 Docker Desktop 里部署的镜像和容器</u>是独立的

>[!warning] Docker Desktop 只允许在本机中运行，不允许在虚拟机中运行

### Volumes
>容器中的数据不会<u>持久化</u>【容器一旦停止，容器的所有数据都会丢失】，而**Volumes** 可以把容器中的指定路径映射到宿主机的某个位置，实现持久化

# Docker 命令
## 操作镜像
### docker pull
> docker pull 可以从远程的 Docker 镜像仓库中下载 Docker 镜像到本地




### docker images
>docker images 可以列出本地上所有的 Docker 镜像


### docker rmi
>docker rmi 可以删除本地上的镜像



### docker build



### docker push


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

### docker run
>[!hint] 运行 `docker run 镜像名称` 如果本地没有镜像，会自动去镜像仓库下载

- `docker run ……参数 镜像名称:[版本号]` 创建并运行一个容器【**版本号不写默认最新版**】
	- `-d` 在后台运行
	- `--name 名字` 设置容器的名字
	- `-p 主机端口号:容器端口号` 将<u>容器的端口</u>映射到<u>主机的端口</u>
	- `-e key=value` 配置环境变量【比如 MySQL 的账号密码，时区……】

```bash
docker run -d --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw mysql:5.7
```


### docker stop
>docker stop 可以停止正在运行的 Docker 容器，**但是容器还在，没有删除**



### docker start
> docker start 可以用于启动被停止的 Docker 容器


### docker ps
> docker ps 可以列出当前正在运行的 Docker 容器

### docker rm
> docker rm 用来删除容器


### docker logs
> docker logs 用于获取和查看 Docker 容器的日志


### docker exec
> docker exec 可以进入到容器的内部，来修改容器