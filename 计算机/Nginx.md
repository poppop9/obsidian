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
  -v /data/nginx/logs:/var/log/nginx
```







