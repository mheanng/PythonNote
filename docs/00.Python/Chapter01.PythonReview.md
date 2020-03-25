# 1. PYTHON简介
## 1.1. Python背景
学习先导：

- Python是什么？它从何而来？当前有何应用？它有何优劣势呢？未来如何发展？
- Python的基本组成架构是什么？了解Python程序中的基本组成
- 了解变量与对象的绑定
- 了解基本数据类型和存储方式

### 1.1.1. 诞生
- **诞生时间:** 1989圣诞节期间
- **创始人:** Guido van Rossum(荷兰)
- **Python的命名:** 源于一个喜剧团Monty Python
- **Python的官网:** www.python.org
- **Python的版本:** 
  - Python v2.7（2020年结束维护）
  - Python v3.5（当前学习环境）
  - Python v3.8（最新版本）
- **目的**
  - 简洁而强大，与其他主要编程语言一样（当时C语言独霸天下，使用占比超50%，后来最高70%+）
  - 清晰而优雅，尽量使用纯英文单词以便于理解
  - 高效开发，并为大量非专业程序员提供日常轻量级使用
  - 开源

### 1.1.2. 应用
- 应用领域: 
数学（最早）、系统运维、网络编程、科学计算、人工智能，机器人、web开发、大数据及数据库编程、云计算、教育、游戏、图像、其他

### 1.1.3. 关于这门语言的评价
- **Python优缺点**: 
  - **优点**:  
  	1. 面向对象（Java，C++，Python）  
  	2. 免费
  	3. 简单易学
  	4. 可移植
  	5. 可混合编程（C/C++/Java/.net）
  	6. 开发效率高
  	7. 开源
  - **缺点**:  
  	1. 和C/C++相比执行速度不够快（最高的是C，其次C++）  
  	2. 不能封闭源代码

执行效率vs开发效率，两者几乎不能兼得。  
所以涉及效率的部分可以C/C++开发，这种特性使得Python被称为胶水语言。

### 1.1.4. 版本与兼容区别
#### 1.1.4.1. python3版本比python2的优势

一些示例：

- 数值计算更符合数学思维:  
  ```shell
  如: 整数相除中，“/”在python2中是地板除，python3中则是数学意义上的除法  
    python2: 1/2=0  
    python3: 1/2=0.5  
  ```

- 数据处理速度更快: 
  ```shell
  实例: 实测迭代300M大小的文件
  测试方法: 读取文件，for循环迭代每一行，再用for循环迭代每一个字符，pass填充语句
  结果: 
  python2平均花了20秒，二进制流花了17秒
  python3平均花了13秒，二进制流花了11秒
  ```

- 对于一些数值类型定义更明确:   
  python3会尽量减少一些BUG，如数值类型比较:   

  ```python
  $ python2
  >>> 1000 < 1500 < 2000
  True
  >>> 1000 < "1500" < 2000
  False

  $ python3
  >>> 1000 < 1500 < 2000
  True
  >>> 1000 < "1500" < 2000  # 主动抛出异常，避免人为错误
  Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  TypeError: '<' not supported between instances of 'int' and 'str'
  ```
  ...


## 1.2. Python的安装及环境搭建
### 1.2.1. Python 的安装:
  Windows / Mac OS X / Unix ...
### 1.2.2. Python的解释执行器

```shell
CPython (python)    ——C写的
Jython              ——Java写的
IronPython          ——.net
Pypy                ——python
```
## 1.3. Hello world: Python的运行
### 1.3.1. 在Linux中Python执行的方式
- 方法一: 命令行交互提示模式（交互模式）
  打开命令窗口: 
  ```python
  $ python3
  >>> print("hello")
  >>> quit()    #退出交互模式，exit()，或 Ctrl + D
  ```
- 方法二: 调用系统python程序执行文件（脚本模式）
  - 方式1: 命令行指定系统程序调用，去运行脚本文件（文件外去指定python程序运行脚本）
      1. 编写文本文件如下，存储为文件: hello.py
        ```python
        print("hello world!")
        print("today is friday!")
        ```
      2. 随后在同级目录下打开命令窗口运行命令: 
      ```bash
      $ python3 hello.py
      ```

  - 方式2: 脚本文件头指定调用程序路径，直接运行脚本（将文本文件直接作为执行文件，第一句写入解释语句，指定调用程序，该方法一般用于Linux下）
    1. 编写文本文件如下，存储为: hello.py 
    ```python
    #! /usr/bin/python3
    print("hello world!")
    print("today is friday!")
    ```
    2. 随后在同级目录下打开命令窗口运行命令: 
    ```bash
    $ chmod a+x hello.py   #给文件增加可执行权限。
    $ ./python.py		#执行程序。要求文件里须有解释语句 #! /usr/bin/python3
    ```

  <font  face="仿宋">
  一般而言常用运行方式有:<br>
  1.Linux/Win-cmd/Win-PowerShell/Other等命令行窗口运行脚本；<br>
  2.第三方软件sublime, vscode, pycharm等运行脚本。
  </font>
  <br>

### 1.3.2. 基本“输入”、“输出”
- 基本输入函数: input()
  - 返回  
    str。返回输入的字符串，自动删除末尾回车生成的\n。（若要保留字符，请见后续模块一章sys模块的使用）
  - 格式及用法:   
    ```python
    a = input("自定义输入提示语(可空)")
    print(a)
    ```
  - 使用方法: 交互界面输入内容，按回车结束，此时系统自动捕捉输入内容（字符串）
  
- 基本输出函数: print()
  - 返回:   
    None
  - 功能:   
    打印显示表达式结果于屏幕。如果是内容是一个表达式（如函数），则打印其“返回结果”。
  - 格式:
    ```python
    print(a , b , c , … , sep=" ",end="\n")
    ```
    a, b, c ... 为表达式（包括数字、字符串等）
    sep为输出间隔字符，默认为空格，可自定义
    end为末尾默认字符，默认为回车，可自定义

<font>小知识:</font> 
<font  face="仿宋">
交互模式下的print和表达式都会打印，有什么区别？
如：

```python
>>> 'hello'  # 表达式的返回值可视化
'hello'
>>> print('hello')  # print()函数打印
hello
>>> a='hello'  # 表达式的返回值被赋值到了a也就不打印了
>>> a=1+1; 2-1; 4-1  # 只打印最后一个数据对象的返回值
1
```

如何理解print和表达式中的打印？  
- “表达式打印” 是交互模式下，特有的功能。表达式操作数据对象，一般表达式的返回值结果在未绑定变量时则打印表达式处理后预返回的基本结果信息，当放在脚本执行时将不会打印。  
- “print()打印” 是一个函数执行功能，是一个功能语句，放在脚本执行仍然执行打印操作。
如图  
![](img/c1_p.png)  
——（摘自Python小课团队制作图片）
</font>

## 1.4. Python程序基本介绍
### 1.4.1. Python程序的组成

<font face="仿宋"><b>
程序由模块组成<br>
模块由语句，函数，类，数据等组成<br>
语句包含表达式<br>
表达式建立并处理数据对象<br>
</b></font>

#### 1.4.1.1. 语句和表达式

- <h4>语句和表达式基本理解</h4>

  - **表达式 expression**
    
    表达式，是由数值、运算符、分组符号（括号）、自由变量和约束变量等以能求得数据对象的有意义排列方法所得的组合。   
    （建立或操作数据对象的句子, 如`1 + 3`, `sum([1, 2, 3])`等）
    >表达式建立并操作数据对象;  
    >表达式运算完毕返回运算的最终结果，可赋值给变量。例如: 1+2+3就是表达式，运算完毕最终返回6，可赋值给变量;  
    >若计算结果值未赋值给变量，该行执行完后返回得到的数据对象一般将在内存销毁。 

  - **语句 statement**   

    由表达式、运算符、变量等组成的执行某件事的完整句子  
    （执行完整功能的句子, 如`i = 1 + 3`, `a = sum([1, 2, 3])`, `pass`等）
    > 语句一般可以这样理解，语句：`变量 = 表达式`。  
    > 当然一些功能性语句不满足上式：如`pass`/`break`/`continue`等功能性操作句子也是语句  
    > 表达式运算后结果能赋值给变量，语句则不能（可利用这一点测试并区分表达式和语句）  


- <b>Python3中哪些内容被称为表达式，哪些是语句？</b>   
  **表达式包括：**  
  算式，数值对象（数值、字符串、列表等），函数，类对象等。  
  **简单的区别方法：**  
  进入python交互模式界面。输入`a=表达式`或`print(表达式)`，按Enter后能正常运行的都是表达式，如果不能正常运行的，则为语句。表达式一般都有返回值，如函数至少返回为None。（这两者操作的实质都为赋值，赋值的前提是有数据对象返回。）

  - **示例1：表达式和语句简单区别方式**  
    以下内容哪些是表达式，哪些是语句？
    ```python
    12.5
    10+2.5
    "hello"
    [1,2,3]
    list
    print()
    i=10+2.5
    pass
    ```
    仅使用print测试（使用a=测试也一样，函数传参其实也类似于赋值操作）：
    ```python
    >>> print(12.5)     # 创建数值对象，返回该数值对象
    12.5

    >>> print(10+2.5)   # 创建两个数值对象，运算完毕返回最终结果对象
    12.5

    >>> print("hello")  # 创建字符串对象，返回该字符串对象
    hello

    >>> print([1,2,3])  # 创建列表对象，返回该列表对象
    [1, 2, 3]

    >>> print(list)     # list类对象(Python自带的类对象)，返回类对象类型
    <class 'list'>

    >>> print(print())  # 函数print()对象，该函数运算结束返回None
    None

    >>> print(i=10+2.5)  # 完整语句
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: 'i' is an invalid keyword argument for print()

    >>> print(pass)      # 完整语句
      File "<stdin>", line 1
        print(pass)
                ^
    SyntaxError: invalid syntax
    ```
    结论：只有最后两个是语句，其余都是表达式
  - **示例2：对于函数表达式的深刻理解**  
    如何理解如下表达式末尾打印None？
    ```python
    >>> print(print(666))  #函数，函数本身执行一次，返回的None再打印一次
    666
    None
    ```
    可以将以上式子拆解如下进行理解：
    ```python
    >>> a = print(666)  # 表达式print(666)运算，会打印666，随后将运算后结果赋值给a
    666
    >>> print(a)        # 打印a的值
    None
    ```
    如何理解print()？
    ```python
    >>> a1 = print(666)  # 表达式print(666)运算，会打印666，表达式最终创建返回None对象，随后将运算后结果赋值给a1
    666
    >>> a2 = None        # 表达式创建None对象，返回None对象，赋值给a2
    >>> b1 = 300 + 2000         # 创键300、2000对象，      运算完返回2300数值对象，赋值给b1
    >>> b1 = 300 + 1000 + 1000  # 创键300、1000、1000对象，运算完返回2300数值对象，赋值给b2
    ```
    第一句和第二句实际是等效的，最终创建并返回None对象，只是做的过程不同。
    第三句和第四句实际也是等效的，最终运算完创建并返回2300对象，只是做的过程不同。
    因而，`print()`就和创建`None`，运算`1+2`一样，都是表达式进行运算的过程，运算完毕最终返回某个结果。


#### 1.4.1.2. Python的中的各种标识符号
- 常见标识符：  

|               符号               |                             说明                             |
| :------------------------------: | :----------------------------------------------------------- |
|               `#`                | 注释一行，`#`开始到行尾。作用: 让注释内容不参加程序解释执行  |
|               `\`                | 字符串中的“\”表示转义符                                      |
|               `\`                | 语句末尾的“\”表示语句换行符                                  |
|               `;`                | 语句分隔符                                                   |
|               `:`                | 语句块的开始                                                 |
|               `,`                | 数据对象分割符                                               |
|              `( )`               | 元组类型表示，数据对象之间运算的优先级表示，还常用于隐式换行 |
|              `[ ]`               | 列表类型表示                                                 |
|              `{ }`               | 字典类型、集合类型等表示                                     |
|      `' '`<br> 或<br> `" "`      | 字符串类型表示                                               |
|  `''' '''`<br> 或<br> `""" """`  | 多行注释，字符串类型表示，函数,类,模块等文档说明             |
|               `=`                | 赋值运算符                                                   |
|           `>` `<` `==`           | 比较运算符                                                   |
| `+` `-` `*` `/`<br> `//` `%` `&` | 数值计算运算符                                               |
|               ...                |                                                              |

- 关于Python中的注释
  1. 单行注释  
      从`#`开始的位置一直到行末不再被编译器作为代码读入，用于人为注解标识。
      如：  
      ```python
      # 注释内容1，这段代码是做什么的
      a = [1, 2, 3]  # 注释内容2，这一步是做什么的
      ```

  2. 特殊注释  
      一般文件前两行为特殊注释:   
      > 第1行为解释执行器路径  
      > 第2行为当前文件的编码  
      如:   
      
      ```python
      #! /usr/bin/python3
      # -*- coding=utf-8 -*-
      ```

  3. 多行注释  
      以`'''`或`"""`一对三单引号的开始和结束的区域，作为注释内容。  
      当放于文件、函数、类等开始时，常被用作help文档，如模块(文件)文档，类文档，函数文档。  
      如numpy的包初始化文件`python\lib\site-packages\numpy\__init__.py`：
      ```python
      """
      NumPy
      =====

      Provides
        1. An array object of arbitrary homogeneous items
        2. Fast mathematical operations over arrays
        3. Linear Algebra, Fourier Transforms, Random Number Generation
      ...
      """
      ```
      通过`help(numpy)`便会在DESCRIPTION中将该文档显示出来


<span id='huanhang'></span>

- 关于Python中的换行: 
  - 换行规则
    ```
    一般一条语句一行；
    多条语句在一行中用“;”分隔（一般不采用，需遵循PEP8规则）；
    一条语句的换行在多行中用“\”连接，或在“括号”中进行单或多次换行。
    ```
  - 一条语句的换行  
    `\`，可实现显式换行，实现语句连贯  
    `()[]{}`，可实现隐式换行，实现语句连贯  

    ```python
    # 显式换行
    a, b = 1, \
           2
    print(a, b)  # 1 2
    
    # 隐式换行
    a, b = (1,
            2)
    print(a, b)  # 1 2
    ```

## 1.5. 对象、变量、赋值的基本概念

### 1.5.1. 对象——Python程序的基本单位
Python中一切皆对象（数值，字符串等）。  
如函数是函数对象，函数的参数是对象，函数中的多个对象，逗号分隔。  
`>>> 函数(对象1，对象2，对象3，…)  ## 如print`  

### 1.5.2. 变量——用于绑定对象的名字对象
- **变量基本概念:**   
变量是用来绑定数据对象的标识符  
变量可以绑定任何东西，如数据类型，函数，类实例等对象  
- **作用:**   
在内存中用于标识暂存数据以便后续使用。  
- **变量的数据类型:**   
变量的数据类型实质是绑定的对象的数据类型。它是动态的，随绑定对象变化。  
查看类型的函数type(x)。  

#### 1.5.2.1. 变量的定义
- **定义变量:**  （先定义后使用）  
  1.取名。  
  2.赋值创建: 第一次赋值时，创建的变量与对象“绑定”（见下一节）。

- **变量命名规则**  
    取名规则:  
    变量名必须是标识符: `[A-Za-z_][A-Za-z0-9_]*`  
    1.开头只能是下划线or字母；  
    2.由字母or下划线or数字构成；  
    3.大小写不同；  
    4.保留关键字。  
    （PEP8规则详细描述了取名规则，文件排版等规则，包含其他书写规则见官网文档，或附件PEP8编码规范。一般在日常使用中都用编译器相关插件完成一键排版）  

    合法的变量名示例:   
    `a  a1  b  bbb   _aaa_   _Abcdvara1b2c2`  
    不合法的变量名示例:   
    `1a   123   $ABC  +a  -b   #ab   @ab`  
    python 的关键字: ( `help("keywords")` 可以查看已经使用的关键字)   
    `True, False, None, is, del, if, elif等`  

<br>
<font face="仿宋">
python里面非字符串的所有符号尽量保证是英文的，特殊字符、中文符号等尽量存在于字符串。  
虽然Python3相较于Python2改进了编译器，可以使用汉字作为变量名，但尽量不要使用，因为保存的py文件编码方式不同，可能造成打开文件乱码(当然，也可以文件头指定文件编码方式)。
</font>

#### 1.5.2.2. 变量的删除（del函数解除变量绑定）
解除变量绑定，一般当引用计数为零时销毁其绑定对象。  
原理：Python内存管理和引用计数（为零时，对象删除）  
```python
>>> dir()
[..., '__name__', '__package__', '__spec__']
>>> a = 2000
>>> dir()
[..., '__name__', '__package__', '__spec__', 'a']
>>> del a
>>> dir()
[..., '__name__', '__package__', '__spec__']
```


### 1.5.3. 赋值——用于“绑定对象与变量”的操作
- 赋值（“绑定”）概念:   
  赋值/关联/绑定/引用: 变量和一个数据对象进行关联关系，从数据对象到变量进行单向绑定。  
- 赋值绑定作用  
  暂存数据。每行语句的表达式都会单独生成对象，若数据对象没有被变量绑定则运行完此语句可能销毁。  
- 赋值格式:   
  ```
  变量名 = 表达式建立的对象  
  （“=”是赋值运算符）  
  ```
- 其他变量赋值方式:   
  1）多重赋值
  ```python
  a = a1 = a2 = a3 = 123  # 多重赋值
  print(a, a1, a2, a3)  # 123 123 123 123
  ```
	2）多元赋值  
  (更多详情见后续章节中，数据容器-->序列的多重赋值)  
  ```python
  a, a1, a2, a3 = 1, 2, 3, 4
  print(a, a1, a2, a3)  # 1 2 3 4
  ```
  3）增量赋值  
  ```python
  x += 1  
  x -= 1  
  x *= 2  
  ...
  ```

  - 小知识——变量互换： x, y = y, x  
    ```python
    # 多元赋值交换变量方式不需要创建新的变量对象
    a, b, c = 1024, 2048, 4096
    print(id(a), id(b), id(c))  # 2210734229392 2210762967664 2210734229520
    b, a, c = a, b, c 
    print(id(b), id(a), id(c))  # 2210734229392 2210762967664 2210734229520

    # 经典交换算法: （该方法会创建变量新对象）
    a, b = 100, 200
    temp = a
    a = b
    b = temp
    ```

## 1.6. 认识事物本质——探索对象、变量及赋值的本质的方法
### 1.6.1. 如何查看帮助文档?

Python编程中非常重要的一个本领，查看帮助文档，该方法连接了不同人之间高效交流的桥梁。  
- `help(x)`函数

```bash
help(x)
# 可以查看关于x的信息，x可以是函数名、类名、类方法等
# 如: help(print)  # 可查看函数传参属性，如end="\n"

常用：
help(函数名)  # 可以查看函数帮助文档，如help(print)，help(pow)
help(类名)    # 可以查看类的帮助文档，如help(list)
help(模块)    # 查看模块的帮助文档
help(对象.方法)  # 查看某个方法文档

其他用法：
help("keywords")  # 查看所有关键字
help("modules")   # 查看所有可用模块
help("topics")    # 查看常见的topics
help("__main__")  # 查看当前文件帮助文档
```

- pydoc程序

```bash
$ pydoc -g  # 生成html帮助文档报表
```

### 1.6.2. 如何查看环境中的变量？

- 函数查看  

```python
help("__main__")  # 返回包含变量关系的帮助文档字符串
dir([对象])  # 返回指定对象内（默认为当前环境变量）定义的名字(属性，方法，)的列表
globals()   # 返回当前全局作用域内变量的字典
locals()    # 返回当前局部作用域内的变量的字典
```

- 类属性查看  
(暂作了解)  
`类.__dict__` 查看类对象实例的变量绑定关系，__dict__属性绑定一个存储此实例自身变量的字典

- 常见系统变量  
(暂作了解)  
`__name__`  当前执行模块(python程序文件)的主名称，一般当前主模块为`"__main__"`，使用的其他变量为变量名。  

**示例:**  

1. `help("__main__")` 查看本次运行所有的变量及绑定关系的方法  
    编辑py文件: test.py  
    ```python
    """
    help: 
    ********test doc自定义文档********
    """

    a = 2
    print('当前模块名：', __name__, "类型是", type(__name__))
    print(help(__name__))
    ```

    执行：
    ```shell
    $ python3 test.py
    当前模块名： __main__ 类型是 <class 'str'>
    Help on module __main__:

    NAME
        __main__

    DESCRIPTION
        help: 
        ********test doc自定义文档********

    DATA
        __annotations__ = {}
        a = 2

    FILE
        c:\\users\\jun\\desktop\\test.py

    None
    ```

2、dir([对象])   
示例: 
```python
>>> dir()
['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__']
>>> dir(list)
[..., 'append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
>>> L = [1,2]
>>> dir(L)
[..., 'append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
```

### 1.6.3. 如何查看对象基本属性？
如何理解基本属性？  
> 该数据对象是什么？【数据对象类型】  
> 该数据对象的从哪里来（运行位置）？【数据对象地址编号】  
> 该数据对象所绑定的变量和其他相同值变量区别，是否为同一个对象？【数据对象识别判断】  
#### 1.6.3.1. `type(obj)` 查看对象所属类型
返回对象的类型（基本类型总结见本章末）  
基本类型都可以用`type(obj)`判断:   
```python
>>> type(123)  # 数值
<class 'int'>
>>> type('123')  # 字符串
<class 'str'>
>>> type(None)   # None对象
<type(None) 'NoneType'>
>>> type([123])  # 列表
<class 'list'>
>>> type((123,)) # 元组
<class 'tuple'>
>>> type({123: None})  # 字典
<class 'dict'>
>>> type({123})  # 集合
<class 'set'>
...

>>> type('abc')==str  # 判断对象是否相等
True
```
#### 1.6.3.2. `id(obj)` 函数查看对象内存地址代号
  Python对象有唯一标识。函数id()可查看，id()返回对象的内存地址的代号（虚拟环境，非真实地址编号，不同于C语言）。  
  可用于查看对象存储于计算机内存的“地址”，以精确判断对象的存储性质。  

#### 1.6.3.3. `is`判断是否是同一个对象
is判断: 判断变量或对象是否为同一个对象  
- `is`，如 `a is b`
- `is not`，如 `a is not b`

（`a is b`实际等效于`id(a) == id(b)`）

为什么需要判断？表面值相同在内存中的数据对象不一定相同。    

---
- **示例：** 探索变量相同表面值在内存中是否为同一对象  

```python
>>> a, b = [], []
>>> a == b
True
>>> a is b  # 不是同一数据对象
False
>>> print(id(a), id(b))  # 因此在内存中的id也不同，它们分别在不同位置新建列表对象
1896198034248 1896198037448

>>> a, b = 257, 257
>>> a == b
True
>>> a is b
False
>>> print(id(a), id(b))
1896196729936 1896196727568
```
---
应用实例：`is`判断某个实例对象是否是某个类型
```python
>>> type(20) is int
True
>>> type([3, 5, 8]) is list
True
```

##### 1.6.4. 探索“小整数对象池”在内存中的存储规则:
<font color='red'><b>小整数对象池</b></font>：Python程序创建之初，便初始化-5到256的数在内存中，它们随程序运行周期永远存在，不会释放，且单份存在(在这个范围内不会创建新的范围内的数值对象)。  
也就是说，<font color="red">大于或小于该边界的数值对象创建会重新创建新对象。</font>  

```python
# 256的id号重新创建赋值不会改变，并且自始至终只有一个"256"对象
>>> a, b = 256, 256
>>> print(a==b, a is b, id(a), id(b))
True True 140705097695600 140705097695600
>>> del a,b
>>> a, b = 256, 256
>>> print(a==b, a is b, id(a), id(b))
True True 140705097695600 140705097695600

# 257的id号重新创建赋值会改变，会创建新的"257"对象
>>> a, b = 257, 257
>>> print(a==b, a is b, id(a), id(b))
True False 2767442848048 2767442849200
>>> del a,b
>>> a, b = 257, 257
>>> print(a==b, a is b, id(a), id(b))
True False 2767442849648 2767442847696
# 4个257id都不同
```

<span id='Understanding_assignment'></span>

### 1.6.5. 理解`对象`、`赋值`、`变量`的动态关系——赋值过程

<h4>赋值(绑定)本质</h4>

<font face="楷体">

分别创建`“变量对象”`和`“数据对象”`，从`“数据对象”`到`“变量对象”`单向赋值绑定。  

</font>

如：  
在赋值操作`a=1000; b=1000`的过程中，Python解释器大概做哪几个动作？  
>1.数据对象准备，检测内存中1000非系统必要保留对象，创建`“对象1:1000”`，创建`“对象2:1000”`  
>2.创建变量`“对象3:a”`、`“对象4:b”`  
>3.从`“对象1:1000”`到`“对象3:a”`单向绑定，从`“对象2:1000”`到`“对象4:a”`单向绑定，最终“a”、“b”分别绑定到了两个1000对象上。

在赋值操作`a=10; b=10`的过程中，Python解释器大概做哪几个动作？  
>1.数据对象准备，检测内存中有“10”属于小整数对象池，属于系统必要保留对象（无需创建）  
>2.创建变量对象“a”，“b”  
>3.从“10”到“a”单向绑定（联系），从“10”到“b”单向绑定，最终“a”、“b”都绑定到同一个对象“10”  



<h4>深入理解</h4>  

**问题一: 多重赋值的本质是什么？**  
例如：`a=[10]; b=a; c=b`，即a绑定到\[10\]，b绑定到a，c绑定到b，最后b和c都指向内存中的哪个数据对象呢？  
> 都指向了绑定的`数据对象[10]`。  
>
> 变量本身不保存任何数值。变量向另一个变量赋值(绑定)，实际过程是：当前变量查找去赋值的变量所对应的`数据对象`，然后将对应`数据对象`与当前变量进行赋值。  
>
> 由于赋值的单向性，多个`变量`可绑定到一个`数据对象`，而一个`变量`只能绑定一个`数据对象`。  

```python
c = b = a = [10]
# 以上一式等效于以下三式：
a = [10]
b = a
c = b

"""赋值绑定过程：

a = [10]
  数据对象[10]
   / 
  a  

b = a
  数据对象[10]
   / |
  a  b
c = b

  数据对象[10]
   / | \
  a  b  c

"""

# 验证：当数据对象从[10]增加为[10, 20]，
# 其他变量打印结果都改变，但最终他们的id不变。

>>> a = [10]; b = a; c = b;
>>> print(a, b, c, id(a), id(b), id(c))
[10] [10] [10] 1896198013512 1896198013512 1896198013512

>>> a+=[20]
>>> print(a, b, c, id(a), id(b), id(c))
[10, 20] [10, 20] [10, 20] 1896198013512 1896198013512 1896198013512
```

**问题二: 如何理解对象的创建与销毁？**  
在赋值操作`a=1000; a=2000; a=1000`的过程中，1000是否会被销毁？
> 会，在第二次赋值时，对象1000的引用计数从1变为0，非系统必要保留数值对象被销毁。  

```python
a = 1000
a = 2000  # 对象1000是否被销毁？
a = 1000  # 对象2000是否被销毁？
"""赋值绑定过程：

a = 1000
  数据对象1000
   /
  a

a = 2000
  [x]数据对象1000[x]  数据对象2000
                     /
                    a

a = 1000
  新数据对象1000  [x]数据对象2000[x]
            \         
             a
"""

验证：
>>> a = 1000; id(a)
2563691962960
>>> a = 2000; id(a)
2563691963024
>>> a = 1000; id(a)  # 第三次得到的id不同
2563691962992
# 证明1000被销毁，当然2000也被销毁了
```

在赋值操作`a=10; a=20; a=10`的过程中，10是否会被销毁？
> 不会，在第二次赋值时，仅改变了绑定联系。  
>
> 10原本会随着第二次赋值而销毁，回收。但10是小整数对象池中的对象，本次程序执行小整数对象池数值将 <font color="red">“永久”、“单份”</font> 保留于系统中，只有范围 *`[-5,256]`* 之外的数值对象才会遵循销毁规则——当引用计数为零。

```python
a = 10
a = 20  # 对象10是否被销毁？
a = 10  # 对象20是否被销毁？

b = 10
c = 10

"""赋值绑定过程：
a = 10
...  数据对象10  ...
             \
              a
a = 20
...  数据对象10  数据对象20  ...
                /
              a
a = 10
...  数据对象10  数据对象20  ...
             \         
              a
b = 10
...  数据对象10  数据对象20  ...
         |   \         
         b    a
c = 10
...  数据对象10  数据对象20  ...
      /   |  \         
     c    b   a
"""
验证：
>>> a = 10; id(a)
140705097687728
>>> a = 20; id(a)
140705097688048
>>> a = 10; id(a)  # id相同，说明10对象“永久”存在
140705097687728

>>> b = 10; id(b)  # id相同，说明10对象“单份”存在
140705097687728
>>> c = 10; id(c)  # id相同，说明10对象“单份”存在
140705097687728
```

## 1.7. Python中的基本数据类型及表示
茫茫大海，计算机是为处理和计算信息而服务，那么Python中的数据又如何分类存储并计算呢？

<b>Python3 中有六个标准的基本数据类型</b> :
<font face="仿宋">

- Number（数值: 整数int, 浮点数float，复数complex，布尔型bool）  
- String（字符串: str）  
- List（列表: list）  
- Tuple（元组: tuple）  
- Set（集合: set、frozenset）  
- Dictionary（字典: dict）  

其中，
- <b>不可变数据对象（4 个）</b>: 
  Number（数值*4）、String（字符串）、Tuple（元组）、frozenset固定集合
- <b>可变数据对象（3 个）</b>: 
  List（列表）、Dictionary（字典）、Set（集合）。  

除数值对象外，以上类型都属于<b>可迭代对象(iterable)</b>。
</font>

```python
>>> 1, 1.0, 1+0j, bool(1), "1", [1], (1,), {1}, {1: 1}
(1, 1.0, (1+0j), True, '1', [1], (1,), {1}, {1: 1})
```

<b>补充</b>:   
<font face="仿宋">
- 可变对象的区别方法为: 在创建的地址不变情况下，判断对象内是否有元素可以发生变化。  
- 字符串、列表、元组被合并称为序列, 所谓序列, 即成员有序排列, 可通过下标访问，切片。  

</font>
