# 基础
## 目录结构
- `nginx` 
	- `conf` 
		- `conf.d` 
			- default.conf
	- `html` 
	- `logs` 
	- `ssl` 

## 在 docker 中安装配置
[nginx 的 docker 地址](https://hub.docker.com/_/nginx)

- 创建一个默认的 nginx 用于拷贝配置文件
```bash
docker run --name nginxconf -p 9999:80 -d nginx
```

```bash
mkdir -p /home/nginxtest/conf
mkdir -p /home/nginxtest/log

# 从`nginxconfig` 的容器中，复制 `/etc/nginx/nginx.conf` 文件到宿主机的 `/home/nginxtest/conf/nginx.conf` 
docker cp nginxconfig:/etc/nginx/nginx.conf /home/nginxtest/conf/nginx.conf

docker cp nginxconfig:/etc/nginx/conf.d /home/nginxtest/conf/conf.d

docker cp nginxconfig:/usr/share/nginx/html /home/nginxtest
```








