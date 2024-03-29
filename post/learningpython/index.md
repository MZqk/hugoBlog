<!--more-->
**本文仅为粗略地概括python编程的基本语法，若你有C二级的水平将可以轻易看懂。作为引导很容易了解到python基础，详细的最好能通过[官方文档](http://python.usyiyi.cn/translate/python_352/contents.html)学习。**
# Python
源程序编码
除去第一行需要添加运行环境#!/usr/local/bin/python2还需要说明编码方式以使程序能够识别中文输出
```python
# -*- coding: utf-8 -*-
```

## 数据结构
*python的数据类型不需要像C一样特别声明*
布尔值
*True* 
*False*
> 支持and、or和not运算

#### 常量
常量常用全部大写指明，python的优雅在于有规定语法但却没有强制约束，你仍可以对常量做改变
```
PI = 3.14159265359
```
#### 列表
list是一种有序的集合，可以随时添加和删除其中的元素。
```
list = [a,b,c,d]
```
#### 元组
tuple和list非常类似，但是tuple一旦初始化就不能修改
```
tupe = ('a','b','c','b')
```
#### 集合
set和dict类似，也是一组key的集合，但不存储value。由于key不能重复，所以，在set中，没有重复的key。
```
set = {'a','b','c','d'}
```
#### 字典
dict全称dictionary，在其他语言中也称为map，使用键-值（key-value）存储，具有极快的查找速度。
```
dict = {'a':1,'b':2,'c':3,'d':4 }
```
### 特性
#### 切片
取一个list或tuple的部分元素是非常常见的操作

```python
L = list(range(100))
[L[0], L[1], L[2]]
L[:10]
L[-10:]
L[10:20]
L[:10:2]
L[::5]
```

> [0,1,2]
> 
> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
> 
> [90, 91, 92, 93, 94, 95, 96, 97, 98, 99]
> 
> [10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
> 
> [0, 2, 4, 6, 8]
> 
> [0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95]

#### 迭代
如果给定一个list或tuple，我们可以通过for循环来遍历这个list或tuple，这种遍历我们称为迭代（Iteration）。

因为dict的存储不是按照list的方式顺序排列，所以，迭代出的结果顺序很可能不一样。默认情况下，dict迭代的是key

#### 列表生成器
列表生成式即ListComprehensions，是Python内置的非常简单却强大的可以用来创建list的生成式。

```python
[x * x for x in range(1, 11)]
[x * x for x in range(1, 11) if x % 2 == 0]
[m + n for m in 'ABC' for n in 'XYZ']
```

> [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
> 
> [4, 16, 36, 64, 100]
> 
> ['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']

### 生成器
在Python中，列表在循环的过程中不断推算出后续的元素,这种一边循环一边计算的机制，称为生成器：generator。

```python
g = (x * x for x in range(10))
#通过next()函数可依次调用元素的值
#同样可以使用循环的方式迭代出
```

### 迭代器
迭代器是一个可以记住遍历的位置的对象。迭代器对象从集合的第一个元素开始访问，直到所有的元素被访问完结束。迭代器只能往前不会后退。

## 控制流程
### if
```python
if x < 0:
    print (小于零)
elif x == 0:
    print (等于零)
elif x == 1:
    prin(等于1)
else:
    print(大于零)
```
if判断语句可结合elif用来替换‘case’或‘switch’语句
### for
常用遍历
```python
a=['a','b','c','d']
for i in range(len(a))
    print (i,a[i]) 
```
### while
```python
value = raw_input('Please input a number:' )
while:
    if value < 100:
        print 'Right'
    else:
        print 'Please input again'

```
### break、continue和else
> 从C语言引用过来，用在控制语句中跳出或延续
### pass
表示什么都不做，可用来构建最小类。（另外也可以用来当作占位符）
```python
class myclass:
    pass
```
## 函数
*函数嘛，基本编程语言都离不开它。函数能提高应用的模块性，和单一功能功能代码的重复利用率。我们在程序中很多语法本就个内建的函数，比如print()。*
### 内建函数
Python内置了很多有用的函数，我们可以直接调用。
### 定义函数
```python 
def printNum(number):
    """
    这是函数
    使用print.__doc__可以将其打印出
    """
    num = int(number)
    print(num)
```
### 装饰器

### 递归函数
在函数内部，可以调用其他函数。如果一个函数在内部调用自身本身，这个函数就是递归函数。
>通过定义的函数，我们将printNum函数定义为只打整数的print。
#### 闭包

### 匿名函数
所谓匿名，意即不再使用 def 语句这样标准的形式定义一个函数
```python
f = lambda x,y:x*y
print f(4,5)
#结果为4*5
```
### 装饰器

## 错误和异常
### 错误
我们说的错误指的是语法错误，也可以称作解析错误
### 异常
指的是在语法正常的情况下，表达式引发的错误。程序并不会因为其而崩溃，而是将这种异常的以报错的方式显示出来。既然我们知道了有异常一说（而且很多时候是无法避免的），那我们就该来处理这些异常。
```python
while Ture:
    try:
        x = int(input("Please enter a number"))
        break
    except ValueError:
        print("That was no vaild number!Please try again")    
```
*基本语法如上*
>我们需要输入一个整数，但是如果你要输入的不是整数会怎样？这时候就会提示错误（异常），而且提示如上就是ValueError。这里我们自行定义异常的提示结果。

### 异常处理
*由此我们就可以明白异常产生的一个原因，并且可以自行定义异常产生后处理。*
> 那如果我们不知道程序会出现怎样的错误的该如何？这时就可以直接使用expect来将其异常归纳起来统一处理。在expect下加入else则表示没有异常就执行else后的程序块。

### 抛出异常
> 为什么我们要抛出异常呢？

因为错误是class，捕获一个错误就是捕获到该class的一个实例。因此，错误并不是凭空产生的，而是有意创建并抛出的。Python的内置函数会抛出很多类型的错误，我们自己编写的函数也可以抛出错误。

### 自定义异常
>异常出现我们可以做自定义，通过创建新的异常except Error as e：来命名自己的异常。

### 异常清理行为
>最后来说的是异常的清理行为。假如我们在open了文件后出现异常导致没有close上文件，这样会引发一些不必要的问题。那么我们可以用try...finally来保证finally后的程序块必须执行，当然还有一种方法用with来代替try这是预定义的清理行为。

## 类
这是一个较麻烦的问题，但对于学过面向对象编程的人来说就较容易理解了。

## 附录
### 编码风格
>关于缩进符官网介绍的有三种，一个制表符、两个空格或者四个空格。注意这三种风格绝不能混用

**当然大多数人建议的尽量使用其中一种风格，并且长期使用它。而我的建议是我们就只把四个空格当作缩进符，因为Tab键存在平台之间的差异，虽然有时使用四个空格很是麻烦（那是因为你没有用到一款好的文本编辑器）。**

### 命名规则
*Python命名规则和大多数编程语言一样包含着数字、字母、下划线。（同样的首字符不能为数字）*

- 这里的命名规则并没有强制要求，你也可以灵活使用。
（比如整个项目中并没有使用多少全局变量的时候你就可以将其全部大写）

>关于变量
全使用小写字母，碰到多个单词合并成一个变量的时候可以使用_分隔

>关于函数
尽量小写，碰到多个单词合并的时候其后接单词使用大写

>关于类
首字母大写，多个单词合成时同函数的命名规则