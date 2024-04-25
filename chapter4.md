# chapter4

- if/else语句

  + 示例：

    ```python
    pwd=input('what is the password ')
    if pwd=='apple':#note use of ==
        print('Logging on …')
    else:
        print('Incorrect password.')
    print('All done!')
    ```

  + <font color=brown>要在python中识别代码块，必须以同样的程序缩进代码的每一行</font>，以上示例中，两个代码块都缩进了四个空格

- if/elif语句

  + ```python
    age=int(input('How old are you? '))
    if age<=2:
        print('free')
    elif 2<age<13:
        print('child fare')
    else:
        print('adult fare')
    
    ```

- 条件表达式：

  + ```python
    food=input("What's your favourite food? ")
    reply='yuck' if food=='lamb' else 'yum'
    print(reply)
    ```

- 循环

  + for循环：

    ```python
    for i in range(10):
        print(i,end=' ')
        #print0~9
    ```

    ```python
    for i in range(10):
        print(i,end=' ')
        #print 5 6 7 8 9
    n=int(input('Enter an integer >=0: '))
    fact=1
    for i in range(2,n+1):
        fact=fact*i
    print(str(n)+' factorial is '+str(fact))
    ```
  
  + while循环(<font color=brown>注意一定要有初始化和递增语句</font>)：
  
    ```python
    i=0
    while i<10:
        print(i)
        i=i+1
    n=int(input('Enter an integer >=0: '))
    fact=1
    i=2
    while i<=n:
        fact=fact*i
        i=i+1
    print(str(n)+' factorial is '+str(fact))
    ```
    
  + 循环中的循环
  
    ```python
    for row in range(1,10):
        for col in range(1,10):
            prod=row*col
            if prod<10:
                print('*',end='')
            print(row*col,' ',end='')
        print()
    ```

