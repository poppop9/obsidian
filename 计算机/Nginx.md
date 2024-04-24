[nginx 的 docker 地址](https://hub.docker.com/_/nginx)

```bash
docker run --name nginx -v /host/path/nginx.conf:/etc/nginx/nginx.conf -d nginx -p 8080:80
```









