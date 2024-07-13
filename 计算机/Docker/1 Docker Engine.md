
>[!quote] Docker Engine
>Docker Engine 是 Docker 的核心部分，负责构建和容器化应用程序

# 安装 Docker Engine
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
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# 更新系统的软件包列表，这样就可以从新添加的Docker仓库中获取Docker的最新版本
sudo apt-get update
```

- 安装 Docker 包
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# 验证是否安装成功
docker version
```

- 配置镜像加速 https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors
	- 进入阿里云的容器镜像服务
	- 进入镜像工具的镜像加速器
	- 根据操作文档修改

>[!hint] 额外配置
>>额外的配置可以让我们在使用 Docker 时更加方便
>
> - 以非 root 用户身份管理 Docker【可以在使用 Docker 命令时，不加 `sudo`】
> 	- 创建 Docker 组 `sudo groupadd docker`
> 	- 将用户添加到 docker 组 `sudo usermod -aG docker 用户`
> 	- 激活对组的更改 `newgrp docker`

# 制作镜像
## 根据 Dockerfile 制作镜像
>[!quote] Dockerfile
>Dockerfile 是一个文本文件，里面包含一系列指令，用来告诉 Docker 如何构建镜像
>
>- 指令
>	- `FROM` 指定基础镜像
>	- `EVN` 设置环境变量
>	- `COPY` 拷贝本地文件到镜像目录里，`COPY 本地文件 镜像目录`
>	- `RUN` 将拷贝的文件在 Linux 里解压缩……，`RUN tar -zxvf 文件……`
>	- `EXPOSE` 指定容器运行时的端口号，`EXPOSE 端口号`
>	- `ENTRYPOINT` <u>入口命令</u>【应用程序启动的命令，比如 Java 是 `java -jar jar包`】

- 创建一个 Dockerfile
```dockerfile
# 定义基础镜像
FROM openjdk:17-alpine
# 设置时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
# 将跟Dockerfile同一路径下的jar包，拷贝到Docker镜像的根目录下
COPY docker-demo.jar /app.jar
# 入口
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

- 将 Dockerfile 和 jar 包放到同一目录下

- 在该目录下，使用 Dockerfile 构建镜像
```bash
docker build -t demo:1.0 .
```

## 根据容器实例构建镜像
- `docker commit 容器id/名称` 将运行中的容器快照生成为一个新的镜像
	- `-a 镜像作者` 
	- `-m '说明信息'`


# 推送到 DockerHub
```bash
# 进行登录
docker login

# 推送到dockerhub
# docker push 用户名/仓库名:版本号
docker push 1962883041612/ltzf-interface
```


# 挂载
>[!hint] 在容器内修改文件是很困难的，因为从仓库中下载的镜像一般是可运行某个应用程序的最小镜像，不会包括 Vim 编辑器，**所以我们需要挂载**，使用宿主机里的 Vim 编辑器进行修改

## 挂载到数据卷
>容器中的数据不会<u>持久化</u>【容器一旦删除，容器的所有数据都会丢失】，而**数据卷 Volumes** 可以把容器中的指定路径映射到宿主机的某个位置，实现双向数据绑定，实现持久化

数据卷默认在宿主机的 `/var/lib/docker/volumes/数据卷名`

>[!hint] 由于数据卷存储在宿主机上的<u>只有 `root 用户` </u>才可以访问的位置，我们频繁修改文件非常不方便，所以**一般我们会使用直接挂载到本地目录**

---

## 直接挂载到本地目录
> 直接挂载到本地目录可以任意指定挂载的地方，方便访问和修改

