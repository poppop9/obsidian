右键运行git，输入`ssh-keygen -t rsa -C "1962883041@qq.com"`

在C://盘找到.ssh文件夹，打开id_rsa.pub文件，找到密钥，如下：
```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCwkAb55KIogNdPeM4CzEqVcWZPHk08iswbgqi2EnK6lj486g97k8YcchCGskFt0UG0ksb6U8oH6oFGoGp8aCAjw+SNwYnGd9glg+9RHDBnhxm+O8DgcolLathhN8JkHJlnOGB/buW1YYOIQLexhEthSIT2T43pqkKAfoa43443tqpB4n0ihr+aQkTRVFJxQU272gZKMNxf0TJI0EezsQPW7jIM0DflehXupn9itefTq390chy0UQSe6wwk0W3bqbqZNf3JFIJftGCT7S8jjmsfw6bXaD4DdSXhDvdmhDEDFhZq9rW4Y46M6DxOqoS71ppPKPtMLAA34jbjkglqVyvUDzLaEYP4G4TSgBL3rOI16QX6a7jCZ38o52PlzI2tT+HJWLGIMq9MJZjN7ajFdpjGQSy3IJm5L2ug4xu5j8XOi9sOafDQRlCgXDP3GN9TxIjPh+vLQ58r8s5gUxl6Xd+sAxCaPt5SfdUt8tEdav7wlTdUn31yJyizRZplBtjSGU0= 1962883041@qq.com
```

在github上创建库，输入初始化代码：
```
echo "# 🌕obsidian" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/poppop9/obsidian.git
git push -u origin main
```

打开obsidian插件`Obsidian Git`
