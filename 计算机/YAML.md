
>[!hint] YAML 的配置文件后缀为 `.yml`
> - 大小写敏感
> - 缩进不允许使用 `tab`，只允许空格
> - 缩进的空格数不重要
> - 注释使用 `#`

## YAML 对象

冒号后面要加一个空格

```
key: 
    child-key: value
    child-key2: value2
```

## YAML 数组

以 **-** 开头的行表示构成一个数组：

```
companies:
  - id: 1
    name: company1
    price: 200W
    fruits:
      - 苹果
      - 香蕉
  - id: 2
    name: company2
    price: 500W
    fruits:
      - 橙子
      - 葡萄
```

### 纯量

纯量是最基本的，不可再分的值，包括：

- 字符串
- 布尔值
- 整数
- 浮点数
- Null
- 时间
- 日期

使用一个例子来快速了解纯量的基本使用：

```
boolean: 
    - TRUE 
    - FALSE
float:
    - 3.14
    - 6.8523015e+5  #可以使用科学计数法
int:
    - 123
    - 0b1010_0111_0100_1010_1110    #二进制表示
null:
    nodeName: 'node'
    parent: ~  #使用~表示null
string:
    - 哈哈
    - 'Hello world'  #可以使用双引号或者单引号包裹特殊字符
    - newline
      newline2    #字符串可以拆成多行，每一行会被转化成一个空格
date:
    - 2018-02-17    #日期必须使用ISO 8601格式，即yyyy-MM-dd
datetime: 
    -  2018-02-17T15:02:31+08:00    #时间使用ISO 8601格式，时间和日期之间使用T连接，最后使用+代表时区
```