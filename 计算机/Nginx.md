# 在 docker 中安装配置
[nginx 的 docker 地址](https://hub.docker.com/_/nginx)

- 创建一个默认的 nginx 用于拷贝配置文件
```bash
docker run --name nginxconf -p 9999:80 -d nginx
```

```bash

```



1. `docker cp nginxconfig:/etc/nginx/nginx.conf /home/nginxtest/conf/nginx.conf`：这条命令从名为 `nginxconfig` 的容器中，复制 `/etc/nginx/nginx.conf` 文件到宿主机上的 `/home/nginxtest/conf/nginx.conf` 位置
    
2. `docker cp nginxconfig:/etc/nginx/conf.d /home/nginxtest/conf/conf.d`：这条命令从 `nginxconfig` 容器中，复制 `/etc/nginx/conf.d` 目录（以及目录下的所有内容）到宿主机的 `/home/nginxtest/conf/conf.d` 位置。
    
3. `docker cp nginxconfig:/usr/share/nginx/html /home/nginxtest`：这条命令从 `nginxconfig` 容器中，复制 `/usr/share/nginx/html` 目录（以及目录下的所有内容）到宿主机的 `/home/nginxtest` 位置。
    

  

这样一来，你就可以在宿主机上编辑 Nginx 的配置文件和静态网页文件，然后再通过挂载的方式将这些文件放入新的 Nginx 容器中，而不必每次都在容器内部修改。






