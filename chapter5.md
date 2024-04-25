# chapter5

* 示例：

  + 函数头总是以关键字def打头，函数命名规则与变量命名规则相同

  ```python
  import math
  def area(radius):
      return math.pi*radius**2
  #求圆的面积函数
  print(area(1),area(5.5))
  ```

  + ```python
    import math
    def dis(x,y,a,b):
        s=(x-a)**2+(y-b)**2
        return math.sqrt(s)
    def rect_area(x,y,a,b):
        width=abs(x-a)
        height=abs(y-b)
        return width*height
    
    ```
  
* 全局变量

  + 在函数外面声明的变量称为全局变量，程序中的任何函数或代码都可以读取

  + 要访问全局变量，必须使用关键字global

  + 示例：

    ```python
    name='Jack'
    def say_hello():
        print('Hello '+name+'!')
    def change_name(new_name):
        name=new_name
    def change_name1(new_name):
        global name
        name=new_name
    say_hello()
    change_name('Piper')
    say_hello()
    change_name1('Barbie')
    say_hello()
    ```

* 使用main函数

  + 在编写的任何python程序中，通常知道应该使用一个函数main().
  + 根据约定，main()函数被认为式程序的起点
  + 使用main函数在python中，main只是一种约定，完全是可选的
  + ```python
    def main():
        pwd=input("What is the password?")
        if pwd=='apple':
            print('Logging on ...')
        else:
            print('Incorrect password.')
        print('All Done!')
    
    main()
    ```

    

* 按引用传递

  + 向函数传递参数时，python采用按引用传递的方式。传递参数时，函数将使用新变量名来引用原始值,函数结束返回，新变量自动删除，**传递参数不受影响**

* 默认值

  + 给参数指定默认值通常很有帮助

  + 函数可根据需要使用任意数量的默认参数，但**带默认值的参数不能位于没有默认值的参数前面**
  
    ```python
    def greet(name,greeting='Hello'):
        print(greeting,name+'!')
    
    greet('Bob')
    greet('Bob','Good Morning')
    ```

- 关键字参数

  + 示例

    ```python
    def shop(where='store',what='pasta',howmuch='10 pounds'):
        print('I want you to go to the ',where)
        print('and buy',howmuch,'of',what+'.')
    shop()
    shop(what='towels')
    shop(howmuch='a ton',what='towels')
    shop(howmuch='a ton',what='towels',where='bakery')
    
    ```
    
  + 关键字参数清晰地指出了参数值，有助于提高程序的可读性
  
  + 关键字参数的顺序无关紧要



## 模块

模块是一系列相关的函数和变量

#### 创建python模块

- 要创建模块，可以创建一个 `.py`文件，在其中包含用于完成任务的函数

- 模块是一个由函数组成的工具箱，用于编写其他程序，因此模块通常没有main()函数

- ```python
  """A collection of functions for printing basic shapes"""
  CHAR='*'
  def rectangle(height,weight):
      """Print a rectangle"""
      for row in range(height):
          for col in range(weight):
              print(CHAR,end='')
          print()
  
  
  def square(side):
      rectangle(side,side)
  
  def triangle(height):
      for row in range(height):
          for cor in range(1,row+2):
              print(CHAR,end='')
          print()
  
  ```

  

- ```python
  import shapes
  def main():
      print(dir(shapes))
      print(shapes.CHAR)
      print(shapes.square(5))
      print(shapes.triangle(3))
  
  main()
  ```



#### 名称空间

- 对于模块，很有用的一点是它们形成**名称空间**；
- 名称空间基本上是一组独特的变量名和函数名；
- 要让模块中的名称在模块外面可见，必须使用import语句；
- 模块可避免名称冲突，让程序员可以独立地进行开发
- 在使用模块时，尽量不使用 `from ... import *`语句