# JRE
>java runtime environment，是java程序运行的环境

JRM包含了<u>JVM</u>【java运行的虚拟机】和<u>运行时所需要的核心类库</u>

# JDK
>java development Kit，是java程序开发工具包

***JDK包含了<u>JRE</u>和<u>开发人员使用的工具</u>[^2]***

[^2]:编译工具（javac.exe）和运行工具（java.exe）
## JDK与JRE的关系
![[Java的理论知识 Draw#^group=WoUaBvDBivaXsGySRHOQk|447]]
## JDK的安装目录
| **目录名称**          | **说明**          |
| -------------- | -------------- | 
| bin | 存放了JDK的各种工具命令，javac和java就放在这里 | 
| conf | 存放了JDK的相关配置文件 |
| include | 存放了一些平台特定的头文件 | 
| jmods | 存放了JDK的各种模块 | 
| legal | 存放了JDK各模块的授权文档 |
| lib | 存放了JDK工具的一些补充JAR |

# DOS命令窗口
## 常用的dos命令
| **操作**          | **说明**          |
| -------------- | -------------- | 
| 打开命令提示符窗口 | win+r ，输入cmd | 
| 盘符名称: | 盘符切换 | 
| dir | 查看当前路径下的内容 |
| cd 目录          | 进入单级目录     |
| cd .. | 回退到上一级目录 | 
| cd 目录1\目录2\…… | 进入多级目录 | 
| cd\ | 回退到盘符目录 |
| cls | 清屏 | 
| exit | 退出命令提示符窗口 |

# path环境变量的配置
## 为什么要配置环境变量？
>打开javac和java的过程要在dos中打开，非常麻烦，所以要配置
>配置完之后，不需要在dos中输入javac的文件路径，可以直接输入javac

# Java 的内存
>Java 的内存分为两种：
>- 栈内存
>- 堆内存



























