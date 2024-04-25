# chapter3

- 程序示例：

  ```python
  name=input('What is your first name?\n')
  name2=input()
  print('Hello '+name.capitalize()+'!')
  #name.capitalize() make the first alpha of this string is capital(大写), others are lower-case
  print('Hello '+name2)
  ```

  + input()函数<font color=cornflowerblue>只是返回字符串</font>，如果需要结果为数字就必须使用数值转换

    ```python
    age=input('How old are you today? ')
    age10=int(age)+10
    print('In 10 years you will be ',age10,' years old')
    print('In 10 years you will be '+str(age10)+' years old')
    ```

- <font color=cornflowerblue>在屏幕上打印字符串</font>

  + 默认情况下，print在标准输出窗口中打印每个字符串，并用<font color=#b00303>空格</font>分隔它们，可以使用 `set='.'`修改字符串分隔符

  + 默认情况下，print打印完指定内容后添加一个<font color=#b00303>换行符</font>，即默认情况下，调用print后不能再同一行打印任何内容

  + 要在同一行打印所用文本，可将第一行的结束字符指定为空字符

    ```python
    print('jack','ate','no','fat')
    print('jack','ate','no','fat', set='-')
    
    print('jack','ate', end='')
    print(' no fat')
    ```

    