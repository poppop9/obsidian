

>[!hint] 如何安装双 JDK 版本 ？
>[csdn](https://blog.csdn.net/qq_40258748/article/details/115604851?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170239038616800226592284%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170239038616800226592284&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-115604851-null-null.142^v96^pc_search_result_base5&utm_term=%E7%94%B5%E8%84%91%E9%85%8D%E7%BD%AE%E4%B8%A4%E4%B8%AAjava%E7%89%88%E6%9C%AC&spm=1018.2226.3001.4187)

## JDK 的安装目录
| **目录名称** | **说明**                        |     |
| -------- | ----------------------------- | --- |
| bin      | 存放了JDK的各种工具命令，javac和java就放在这里 |     |
| conf     | 存放了JDK的相关配置文件                 |     |
| include  | 存放了一些平台特定的头文件                 |     |
| jmods    | 存放了JDK的各种模块                   |     |
| legal    | 存放了JDK各模块的授权文档                |     |
| lib      | 存放了JDK工具的一些补充JAR              |     |

# DOS 命令窗口
## 常用的 dos 命令
| **操作** | **说明**     |
| ------ | ---------- |
| 盘符名称:  | 盘符切换       |
| cd ..  | 回退到上一级目录   |
| cd\    | 回退到盘符目录    |
| cls    | 清屏         |
| exit   | 退出命令提示符窗口  |

# path 环境变量的配置
>[!hint] 为什么要配置环境变量 ？
>打开 javac 和 java 的过程要在 dos 中打开，非常麻烦，所以要配置。配置完之后，不需要在 dos 中输入 javac 的文件路径，可以直接输入 javac

# Java 的内存
>Java 的内存分为两种：
>- 栈内存
>- 堆内存

## 栈内存
>当程序运行超过变量的作用域后，Java 会自动释放掉该变量的内存空间

- 基本类型变量
- 对象的引用变量

## 堆内存
>在堆中分配的内存，由 Java 虚拟机自动垃圾回收器来管理

- new 出来的<u>对象</u>【包括数组（特殊的对象）】

>[!hint] 创建对象时，对象是在<u>堆内存</u>中的，但是对象的引用是在<u>栈内存</u>中的
























