# chapter2

- **<font color=brown>字面量</font>**

  + 概念：在代码中，被写下来的固定的值;

  + 类似于0.5或3.0的浮点数,两者皆可以简写成.5和3.;

  + 一般而言，在可以使用整数的情况下，尽量<font color=cornflowerblue>不要使用浮点数</font>;

  + 在python中，一般使用 `1j`表示-1的平方根

  + python中常用的6种值：

    | 类型              | 描述                                        | 说明                                                         |
    | ----------------- | ------------------------------------------- | ------------------------------------------------------------ |
    | 数字（number)     | 支持：int,float(double),complex(复数)，bool | <font color=cornflowerblue>python对整数的长度没有限制，但浮点数依旧有大小限制</font> |
    | 字符串(String)    | 描述文本的一种类型                          | 无                                                           |
    | 列表（List）      | 有序的可变序列                              | python中使用最频繁的数据类型，有序记录数据                   |
    | 元组（Tuple）     | 有序的不可变序列                            | 可有序记录一堆不可变的python数据集合                         |
    | 集合（Set）       | 无序不重复集合                              | 可无序记录一堆不重复的python数据集合                         |
    | 字典（dictionary) | 无序Key-Value集合                           | 可无序记录一堆Key-Value型的python数据集合                    |

    ```python
    print(666)
    print(12.32)
    print("Hello world")
    ```

- <font color=brown>注释</font>

  + 单行注释：`#注释内容`
  + 多行注释：`"""注释内容"""`

- <font color=brown>变量</font>

  + 定义变量：变量名+变量值

    ```python
    money=50000000.00
    print("The rest of my money is:",money,"$")
    ```

  + python基本算数运算符（此处仅列出较为特殊的）

    | 名称 | 运算符 | 示例                          |
    | ---- | ------ | ----------------------------- |
    | 除法 | /      | 3/2==1.5                      |
    | 整除 | //     | 3//2==1                       |
    | 求余 | %      | 5.6%3.2==2.3999999999999999   |
    | 乘方 | **     | 7**3==343 （相当于7的三次方） |

    <font color=cornflowerblue>所有适用于整数的算数运算都可以用于浮点数</font>

- <font color=brown>其他数学函数</font>

  + math是python自带的编写好的代码组成的模块

  + 在可以使用数字的任何地方都可以使用这些函数，python自动执行函数，并将函数调用替换为返回值

  | 函数         | 描述                |
  | ------------ | ------------------- |
  | ceil(x)      | 大于或等于x的整数   |
  | cos(x)       | x的余弦             |
  | degrees(x)   | 将x的弧度转换为度数 |
  | exp(x)       | e的x次方            |
  | factorial(n) | 计算n的阶乘         |
  | log(x)       | 以e为底的x的对数    |
  | log(x,b)     | 以b为底的x的对数    |
  | pow(x,y)     | x的y次方            |
  | radians(x)   | 将x度转换为弧度数   |
  | sin(x)       | x的正弦             |
  | sqrt(x)      | x的平方根           |
  | tan(x)       | x的正切             |

  + 示例：

    ```python
    import math
    print(dir(math))
    #it can show all functions in square math
    ```
    
    
    
    ```python
    import math
    print(math.sqrt(5))
    ```
    
    ```python
    from math import *
    #There is no need to use math.log(25+5)
    print(log(25+5))
    ```

- <font color=brown>字符串</font>

  + 字符串字面量可以用3种主要方式表示：<font color=cornflowerblue>单引号，双引号，三引号</font>

  + 单引号和双引号的一个主要用途是，能够在字符串中包含字符"和'

  + `len()`函数可以放回字符串的长度

  + 可以通过字符串"相加"来将两个字符串拼接成一个新的字符串，示例：

    ```python
    print('hot'+' dog')
    print(10*'ha')
    print('hello,'+'world'+10*'!')
    ```

  + 打印文档字符串：大多数python内置函数都有简短的文档的字符串，标准模块（如math)中的大部分函数如此
  
    ```python
    import math
    print(math.tanh.__doc__)
    print(bin.__doc__)
    ```
  
- <font color=brown>类型转换</font>

  + 将整数和字符串转换为浮点数, 将浮点数转换为整数

    ```python
    print(float(3))
    print(float('3.2'))
    print(float('3'))
    print(int(8.64))
    print(round(8.64))
    print(round(8.5))
    ```

  + 将整数和浮点数转换为字符串,将字符串转换为数字

    ```python
    str(85)
    #'85'
    str(-9.78)
    #'-9.78'
    int('5')
    #5
    float('5.1')
    #5.1
    ```

  + python模块math提供了很多将小数部分删除的函数：`math.trunc(x),math.ceil(x),math.floor(x)`

  + 在python中，数字和字符串的一个重要特征是<font color=cornflowerblue>不可变</font>,不能以任何方式修改它们

  + 在python中，可以同时给多个变量赋值<font color=cornflowerblue>(将x,y,z以括号括起来，使得它们构成一个元组，从而它们在同一行被打印)</font>

    ```python
    x,y,z=1,'two',3.0
    print(x,y,z)
    ```

- <font color=brown>交换变量的值</font>

  多重赋值的一个重要用途是交换两个变量的值

  ```python
  a,b=5,9
  print(a,b)
  a,b=b,a
  print(a,b)
  ```

  



