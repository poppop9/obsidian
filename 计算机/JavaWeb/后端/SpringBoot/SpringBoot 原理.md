# 配置优先级
SpringBoot 中支持<u>三种</u>配置文件【`properties`，`yml`，`yaml`】，如果一个项目中出现了多个配置文件配置相同属性的冲突，则它们的优先级排行是`properties` > `yml` > `yaml`

## 外部的配置
其实 SpringBoot 中还可以使用 ***Java系统属性***，或***命令行参数*** 来配置项目属性，但是在项目中一般不使用

>[!hint] 如果要在项目打包成 `jar包` 后，非永久性的修改配置，可以使用 ***Java系统属性***，或***命令行参数*** 
>- 运行 `jar包`
>- 在命令行运行 `java -jar your-application.jar --server.port=8080`
