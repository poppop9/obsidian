
>[!quote] MinIO 
>MinIO 是一个对象存储系统

# ❤️ 安装
```bash
docker run --name minio \
    -p 9000:9000 \
    -p 9001:9001 \
    -v /path/to/minio-persistence:/bitnami/minio/data \
    -e MINIO_ROOT_USER=用户名
    -e MINIO_ROOT_PASSWORD=密码
    bitnami/minio:latest
```

>[!warning] minIO 的密码要设置超过 8 位，要不然会报错

1. **9000 端口**：这是 MinIO 的主要 API 端口，用于数据的对象存储操作。你可以通过这个端口进行文件的上传、下载和管理。
    
2. **9001 端口**：这是 MinIO 控制台的端口，用于管理界面访问。通过这个端口，你可以使用浏览器访问 MinIO 的管理控制台，进行用户管理、监控等操作。

。/。/。。。