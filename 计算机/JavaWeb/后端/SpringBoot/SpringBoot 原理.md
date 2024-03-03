# 配置优先级
SpringBoot 中正常支持<u>三种</u>配置文件【`properties`，`yml`，`yaml`】，如果一个项目中出现了多个配置文件配置相同属性的冲突，则它们的优先级排行是`properties` > `yml` > `yaml`

## 外部配置
其实 SpringBoot 中还可以使用 ***Java系统属性***，或***命令行参数*** 来配置项目属性，但是在项目中一般不使用

>[!hint] 如果要在项目打包成 `jar包` 后，非永久性的修改配置，可以使用 ***Java系统属性***，或***命令行参数*** 
>- 运行 `jar包`
>- 在命令行运行 `java -jar your-application.jar --server.port=8080`

---

>[!hint] 总的优先级排行
>***命令行参数*** > ***Java系统属性*** > `properties` > `yml` > `yaml`

# Bean管理
Spring 项目启动后，***默认***会把 Bean 都创建好放入到 IOC 容器中【还受到<u>作用域</u>，<u>延迟初始化</u>的影响】

## 手动获取Bean
### 根据 name 获取

### 根据类型获取

### 根据 name，类型获取

```java
@SpringBootTest
class SpringAopApplicationTests {
    @Autowired
    private ApplicationContext applicationContext;

    @Test
    public void TestGetBean() {
	// 根据name获取bean
    System.out.println(applicationContext.getBean("helloController"));

	// 根据类型获取bean
	System.out.println(applicationContext.getBean(HelloController.class));

	// 根据name, 类型获取bean
	System.out.println(applicationContext.getBean("helloController", HelloController.class));
    }
}
```



## Bean的作用域



## 第三方Bean


















