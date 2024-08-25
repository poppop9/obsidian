
[https://www.runoob.com/docker/docker-compose.html](https://www.runoob.com/docker/docker-compose.html)

[https://www.cnblogs.com/johnnyzen/p/17785405.html#_lab2_0_2](https://www.cnblogs.com/johnnyzen/p/17785405.html#_lab2_0_2)

[https://www.cnblogs.com/crazymakercircle/p/15505199.html](https://www.cnblogs.com/crazymakercircle/p/15505199.html)

>[!quote] Docker Compose 
>Docker Compose 主要用于在**单个主机**上管理关联多个容器【~~前端，后端，数据库，redis，负载均衡 ……~~】。如果要管理集群，建议使用 K8s
>
> <u>版本差异</u> ：
> - `docker-compose V1` 
> 	- 扩展性差
> 	- 语法过时
> - `docker compose V2` 
> 	- 性能好
> 	- 可以定义多个网络
> 	- 可以配置继承重用
> 
> <u>使用步骤</u> ：
> - 使用 `Dockerfile` 定义应用程序的环境
> - 使用 `docker-compose.yml` 定义构成应用程序的服务，这样它们可以在隔离环境中一起运行
> - 最后，执行 `docker-compose up` 来启动并运行整个应用程序

# ❤ 安装
<u>下载</u> ：
- 从 github 下载
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/v2.28.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

- DaoCloud 第三方高速下载
```bash
curl -L https://get.daocloud.io/docker/compose/releases/download/v2.28.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
```

<u>配置</u> ：
- 将可执行权限应用于二进制文件：`sudo chmod +x /usr/local/bin/docker-compose`
- 创建软链：`sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose`

<u>测试</u> ：
```bash
docker compose version
```

# ❤ 文件编写
## version
version 是 Compose 文件格式版本，需要与 Docker Engine 版本匹配

| Docker Compose file format | Docker Engine |
| -------------------------- | ------------- |
| 2.0, 2.1                   | 1.10.0+       |
| 2.2, 3.0, 3.1, 3.2         | 1.13.0+       |
| 3.6, 3.7, 3.8              | 17.06.0+      |
| 3.4, 3.5                   | 17.12.0+      |
| 3.7, 3.8                   | 18.02.0+      |
| 3.8, 3.9                   | 18.06.0+      |

## services
services 中定义了所有服务的配置，一个服务是一个容器，可以包含多个配置项 ：
- `image`
- `ports`
- `volumes`
- `environment` 

## networks
networks 定义了所有服务可以连接的网络，以便容器之间通信

## volumes
volumes 定义了所有服务可以使用的卷

# ❤ 常用命令
## 💛 镜像
- `docker compose build` 构建镜像，根据 `docker-compose.yml` 文件中有定义 `build` 部分的服务，构建其 Docker 镜像
- `docker compose pull` 拉取镜像，从镜像仓库中拉取 docker-compose.yml 文件中定义的镜像

## 💛 容器
- 启动服务 `docker compose up` 构建、（重新）创建、启动容器

- -d 后台运行

---

如果当前宿主机已存在与该应用对应的容器：
- 用户指定可以重新启动已有服务，重新创建并启动新的容器
- 未指定：直接启动已有容器

---

- 启动服务 `docker compose start` 启动已经存在的容器
- 停止服务 `docker compose stop` 停止运行中的容器
- 重启服务 `docker compose restart 指定容器名` 不指定容器名，则重启所有相关容器

- `docker compose rm 容器名` 如果没有指定容器名，则会删除与 docker-compose.yml 文件相关的所有容器
- `docker compose down`停止并移除所有服务的容器

- 查看

- `docker compose ls` 列出所有运行容器组
- `docker compose ps` 在 docker-compose.yml 目录下运行，列出与该容器组相关的所有容器
- 查看日志 `docker compose logs`

















