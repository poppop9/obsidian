# 基础
## 目录结构
- `nginx` 
	- `conf` 
		- `conf.d` 【所有配置文件定义在这里就好，nginx.conf 会自动引入】
			- default.conf
		- nginx.conf
	- `html` 
	- `logs` 
	- `ssl` 

## 在 docker 中安装配置
[nginx 的 docker 地址](https://hub.docker.com/_/nginx)

- 创建一个默认的 nginx 用于拷贝配置文件
```bash
docker run --name nginxconf -p 9999:80 -d nginx
```

- 在宿主机上创建目录，用来映射容器中的目录
```bash
mkdir -p /data/nginx/conf
mkdir -p /data/nginx/html
mkdir -p /data/nginx/logs

# 拷贝nginx.conf
docker cp nginxconfig:/etc/nginx/nginx.conf /data/nginx/conf/nginx.conf

# 拷贝default.conf
docker cp nginxconfig:/etc/nginx/conf.d /data/nginx/conf/conf.d/default.conf

# 拷贝html
docker cp nginxconfig:/usr/share/nginx/html /data/nginx/html
```

- 创建最终的 nginx
```bash
docker run \
  --name nginx \
  -p 8080:80 \
  -v /data/nginx/logs:/var/log/nginx \
  -v /data/nginx/html:/usr/share/nginx/html \
  -v /data/nginx/conf/nginx.conf:/etc/nginx/nginx.conf \
  -v /data/nginx/conf/conf.d:/etc/nginx/conf.d \
  -v /data/nginx/ssl:/etc/nginx/ssl \
  --privileged=true -d --restart=always nginx
```

使用 `--privileged=true` 参数可以赋予 Docker 容器许多与宿主机系统交互的权限，这包括：
- 访问和操作宿主机的设备，比如可以通过 Docker 容器来管理宿主机的硬件设备。
- 修改宿主机的系统内核设置，比如通过 sysctl 命令来调整内核参数。
- 允许容器使用一些需要特殊权限的系统调用，例如启用一些网络堆栈的特性。
- 可以让容器拥有更接近真正宿主机的网络访问权限，例如直接管理宿主机的网络接口，创建设备，设置设备的属性等。

  

虽然 `--privileged=true` 可以使容器更像一个真正的独立主机，但这也意味着可能会增加安全风险。因为如果容器里运行的进程被恶意代码利用，它将可以直接操作宿主机，这可能对宿主机的安全造成威胁。所以，除非确实需要，否则不建议在生产环境中使用 `--privileged=true`。





