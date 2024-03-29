#

# Python 语法

## 1. Python概述

如果您的工作主要是用电脑完成的，总有一天您会想能不能自动执行一些任务。比如，对大量文本文件执行查找、替换操作；利用复杂的规则重命名、重排序一堆照片文件；也可能您想编写一个小型数据库、或开发专用的图形界面应用，甚至是开发一个简单的游戏。

作为一名专业软件开发人员，您可能要处理 C/C++/Java 库，但编码、编译、测试、再编译这些开发流程太慢了；也许您正在给这些库开发测试套件，但总觉得这项工作 真是枯燥乏味。又或许，您开发了个使用扩展语言的软件，却不想为这个软件专门设计一种新语言。

那么，Python 正好能满足您的需要。

你可以针对这些任务编写 Unix shell 脚本或 Windows 批处理文件，但 shell 脚本擅长的是移动文件和改变文本数据，而不适合编写 GUI 应用或游戏。 你可以编写 C/C++/Java 程序，但即使只完成一个初始版程序也需要耗费很长的开发时间。 Python 则更为简单易用，同时支持 Windows, macOS 和 Unix 操作系统，并能帮助你更快速地完成工作。

Python 虽然简单易用，但它可是真正的编程语言，提供了大量的数据结构，也支持开发大型程序，远超 shell 脚本或批处理文件；Python 提供的错误检查比 C 还多；作为一种“非常高级的语言”，它内置了灵活的数组与字典等高级数据类型。正因为配备了更通用的数据类型，Python 比 Awk，甚至 Perl 能解决更多问题，而且，很多时候，Python 比这些语言更简单。

Python 支持把程序分割为模块，以便在其他 Python 程序中复用。它还内置了大量标准模块，作为开发程序的基础 —— 您还可以把这些模块当作学习 Python 编程的实例。这些模块包括 I/O、系统调用、套接字，甚至还包括 Tk 图形用户界面工作套件。

Python 是一种解释型语言，不需要编译和链接，可以节省大量开发时间。它的解释器实现了交互式操作，轻而易举地就能试用各种语言功能，编写临时程序，或在自底向上的程序开发中测试功能。同时，它还是一个超好用的计算器。

Python 程序简洁、易读，通常比实现同种功能的 C、C++、Java 代码短很多，原因如下：

- 高级数据类型允许在单一语句中表述复杂操作；
- 使用缩进，而不是括号实现代码块分组；
- 无需预声明变量或参数。

Python “可以扩展”：会开发 C 语言程序，就能快速上手为解释器增加新的内置函数或模块，不论是让核心程序以最高速度运行，还是把 Python 程序链接到只提供预编译程序的库（比如，硬件图形库）。只要下点功夫，就能把 Python 解释器和用 C 开发的应用链接在一起，用它来扩展和控制该应用。

顺便提一句，本语言的命名源自 BBC 的 “Monty Python 飞行马戏团”，与爬行动物无关（Python 原义为“蟒蛇”）。欢迎大家在文档中引用 Monty Python 小品短篇集，多多益善！

本教程的其他部分将利用各种示例，介绍 Python 语言、系统的功能，开始只是简单的表达式、语句和数据类型，然后是函数、模块，最后，介绍一些高级概念，如，异常、用户定义的类等功能。

### 解释器的运行环境

![image-20231117102624907](./Python.assets/image-20231117102624907.png)

**默认情况下，Python 源码文件的编码是 UTF-8**。这种编码支持世界上大多数语言的字符，可以用于字符串字面值、变量、函数名及注释 —— 尽管标准库只用常规的 ASCII 字符作为变量名或函数名，可移植代码都应遵守此约定。要正确显示这些字符，编辑器必须能识别 UTF-8 编码，而且必须使用支持文件中所有字符的字体。

如果不使用默认编码，则要声明文件的编码，文件的 *第一* 行要写成特殊注释。句法如下：

```python
# -*- coding: encoding -*-
```

其中，*encoding* 可以是 Python 支持的任意一种 [`codecs`](https://docs.python.org/zh-cn/3.10/library/codecs.html#module-codecs)。

比如，声明使用 Windows-1252 编码，源码文件要写成：

```python
# -*- coding: cp1252 -*-
```

*第一行* 的规则也有一种例外情况，源码以 UNIX "shebang" 行 开头。此时，编码声明要写在文件的第二行。例如：

```python
#!/usr/bin/env python3
# -*- coding: cp1252 -*-
```

这样就可以对其进行编码

## 2. 变量和数据类型

### 内置类型

https://docs.python.org/zh-cn/3.10/library/stdtypes.html

![image-20231117162042316](./Python.assets/image-20231117162042316.png)

#### 常见数据类型

- 常量：None（字典中未被赋值的key的value
- 逻辑值：True,False
- 空集：''、()、[]、{}、set()、range(0)
- 数字类型: int、float、complex
- 文本类型: str 
- 序列类型: list、 tuple、 range
  - example ↓
  - int, int, int, int...
  - int, str, int, int...
- 映射类型: dict
  - example ↓
  - int:str, int:str, int:str...
  - int:list, int:list, int:list...

> **每种数据类型都有各自的【常用内置函数】、【运算符复用】、【语义明确，不容易出错】**
>
> 自己编写类型需要更丰富的编程经验；
>
> 需要通用、高效、功能齐全的其他数据类型
>
> 从**非结构化数据**到**结构化数据**——列表、元祖
>
> - 列表可以修改；元祖不可以修改
>
> 从**非结构化数据**到**半结构化数据**——字典







### 变量

#### 命名和使用

​	在Python中使用变量时，需要遵守一些规则和指南。违反这些规则将引发错误，而指南旨在让你编写的代码更容易阅读和理解。请务必牢记下述有关变量的规则。

- 变量名只能包含**字母、数字和下划线**。变量名可以字母或下划线打头，但**不能以数字打头**， 例如，可将变量命名为mesage_1,但不能将其命名为1_message。

- 变量名**不能包含空格**，但可使用下划线来分隔其中的单词。例如，变量名greeting_message可行，但变量名greeting message会引发错误。

- **不要将Python关键字和函数名用作变量名**，即不要使用Python保留用于特殊用途的单词，如print。

  ![image-20231117161428256](./Python.assets/image-20231117161428256.png)

- 变量名应既简短又具有描述性。例如，name比n好，student_name比s_n好，name_length比length_of_persons_name好。

##### 好的命名习惯

1. 简短
2. 描述性强
3. 大小写敏感，多个单词用“_”连接
4. 尽量不用中文、1lL、0oO

​	要创建良好的变量名，需要经过一定的实践，在程序复杂而有趣时尤其如此。随着你编写的程序越来越多，并开始阅读别人编写的代码，将越来越善于创建有意义的变量名。

### 字符串

- 字符串有多种表现形式，用单引号（`'……'`）或双引号（`"……"`）标注的结果相同
- 反斜杠 `\` 用于转义，或者使用双引号

```python
>>> 'spam eggs'  # single quotes
'spam eggs'
>>> 'doesn\'t'  # 使用单引号进行转义...
"doesn't"
>>> "doesn't"  # ...或者使用双引号
"doesn't"
>>> '"Yes," they said.'	#单引号内部的双引号不需要转义
'"Yes," they said.'
>>> '"Isn\'t," they said.'
>>>print('"Isn\'t," they said.')
'"Isn\'t," they said.'
"Isn\'t," they said.
```

- print()函数输出的内容更简洁易读，它会**省略两边的引号，并输出转义后的特殊字符**：

```python
>>> print("\"Yes,\" they said.")
"Yes," they said.
>>> print('"Isn\'t," they said.')
"Isn't," they said.

>>> s = 'First line.\nSecond line.'  # \n 是换行
>>> s  		  # 不使用print(), \n被包含在输出中
'First line.\nSecond line.'
>>> print(s)  # 使用print(), \n才会被表达
First line.
Second line.
```

#### ASCII码

- ASCII码转字符：`chr(int)`  0-127

- 字符转ASCII码：`ord(str)`  单个可见ASCII字符串，不能中文和非ASCII码里的字符

```python
for i in range(33, 127):
    print(chr(i), end="")
# !"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\]^_`abcdefghijklmnopqrstuvwxyz{|}~

print(ord(")")) 
# 41
print(chr(41))  
# )
```



#### r

- 如果不希望前置 `\` 的字符转义成特殊字符，可以使用 *原始字符串*，在引号前添加 `r` 即可：

```python
>>> print('C:\some\name')  # here \n means newline!
C:\some
ame
>>> print(r'C:\some\name')  # note the r before the quote
C:\some\name
```

三引号"""

字符串字面值可以包含多行。 一种实现方式是使用三重引号：`"""..."""` 或 `'''...'''`。 字符串中将自动包括行结束符，但也可以在换行的地方添加一个 `\` 来避免此情况。 参见以下示例：

```python
print("""\
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
""")
```

输出如下（请注意开始的换行符没有被包括在内）：

```python
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
```



#### 拼接 + / * 

- 字符串可以用 **`+` 合并**（粘到一起），也可以用 **`*` 重复**：

```python
first_name = "talyor"
last_name = "swift"
full_name = first_name+" "+last_name
message = "Hello, this is " + full_name.title() + "!"
print(message) 
# Hello, this is Talyor Swift!
```

```python
>>> # 3 times 'un', followed by 'ium'
>>> 3 * 'un' + 'ium'
'unununium'
>>>'_' * 40
'________________________________________'
```

相邻的两个或多个字符串字面值（引号标注的字符）会自动合并：

```python
>>> 'Py' 'thon'
'Python'
```

拼接分隔开的长字符串时，这个功能特别实用：

```python
>>> text = ('Put several strings within parentheses '
...         'to have them joined together.')
>>> text
'Put several strings within parentheses to have them joined together.'
```

这项功能只能用于两个字面值，不能用于变量或表达式：

```python
>>> prefix = 'Py'
>>> prefix 'thon'  # can't concatenate a variable and a string literal
  File "<stdin>", line 1
    prefix 'thon'
           ^^^^^^
SyntaxError: invalid syntax
>>> ('un' * 3) 'ium'
  File "<stdin>", line 1
    ('un' * 3) 'ium'
               ^^^^^
SyntaxError: invalid syntax
```

合并多个变量，或合并变量与字面值，要用 `+`：

```
>>> prefix + 'thon'
'Python'
```

#### 索引

字符串支持 *索引* （下标访问），第一个字符的索引是 0。单字符没有专用的类型，就是长度为一的字符串：

```python
>>> word = 'Python'
>>> word[0]  # character in position 0
'P'
>>> word[5]  # character in position 5
'n'
```

索引还支持负数，用负数索引时，从右边开始计数：

```python
>>> word[-1]  # last character
'n'
>>> word[-2]  # second-last character
'o'
>>> word[-6]
'P'
```

注意，-0 和 0 一样，因此，负数索引从 -1 开始。

除了索引，字符串还支持 *切片*。索引可以提取单个字符，*切片* 则提取子字符串：

```python
>>> word[0:2]  # characters from position 0 (included) to 2 (excluded)
'Py'
>>> word[2:5]  # characters from position 2 (included) to 5 (excluded)
'tho'
```

切片索引的默认值很有用；省略开始索引时，默认值为 0，省略结束索引时，默认为到字符串的结尾：

```python
>>> word[:2]   # character from the beginning to position 2 (excluded)
'Py'
>>> word[4:]   # characters from position 4 (included) to the end
'on'
>>> word[-2:]  # characters from the second-last (included) to the end
'on'
```

注意，输出结果包含切片开始，但不包含切片结束。因此，`s[:i] + s[i:]` 总是等于 `s`：

```python
>>> word[:2] + word[2:]
'Python'
>>> word[:4] + word[4:]
'Python'
```

还可以这样理解切片，索引指向的是字符 *之间* ，第一个字符的左侧标为 0，最后一个字符的右侧标为 *n* ，*n* 是字符串长度。例如：

```python
 +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1
```

第一行数字是字符串中索引 0...6 的位置，第二行数字是对应的负数索引位置。*i* 到 *j* 的切片由 *i* 和 *j* 之间所有对应的字符组成。

对于使用非负索引的切片，如果两个索引都不越界，切片长度就是起止索引之差。例如， `word[1:3]` 的长度是 2。

索引越界会报错：

```python
>>> word[42]  # the word only has 6 characters
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
```

但是，**切片会自动处理越界索引**：

```python
>>> word[4:42]
'on'
>>> word[42:]
''
```

Python 字符串不能修改，是 immutable 的。因此，为字符串中某个索引位置赋值会报错：

> imumutable — 不可变对象：具有固定值的对象。不可变对象包括数字、字符串和元组。这样的对象不能被改变。如果必须存储一个不同的值，则必须创建新的对象。它们在需要常量哈希值的地方起着重要作用，例如作为字典中的键。

```python
>>> word[0] = 'J'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>> word[2:] = 'py'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```

要生成不同的字符串，应**新建一个字符串**：

```python
>>> 'J' + word[1:]
'Jython'
>>> word[:2] + 'py'
'Pypy'
```

##### s.index(x[, i[, j]])

*x* 在 *s* 中首次出现项的索引号（索引号在 *i* 或其后且在 *j* 之前）

```python
"abcdefg".index('d') # 3
```



#### 切片

- `s[i]`：s的第i项，起始为0
- `s[i:j]`：s从i到j的切片
- `s[i:j:k]`：s从i到j步长为k的切片

```python
s = "abcdefg hi"
#    0123456789 
print(s[0])
print(s[2])
print(s[-1])
print(s[1:4])
print(s[2:9:3]) #从2到9步长为3

a
c
i
bcd
cfh
```



#### 制表符

```python
print("Languages:\n\tPython\n\tC++\n\tJava")
#Languages:
#	Python
#	C++
#	Java
```

#### 字符串比较

```python
"""
字符串的比较操作：
    1. 运算符：>,>=,<,<=,==,!=
    2. 比较规则:首先比较两个字符串中的第一个字符，如果相等则继续比较下一个字符，依次比较下去，直到两个字符串中的字符不相等时，其比较结果就是两个字符串的比较结果，两个字符串中的所有后续字符将不再被比较
    3. 比较原理:两字符进行比较时，比较的是其ordinal value(原始值),调用内置函数ord可以得到指定字符的ordinal value（ASCII码）。与内置函数ord对应的是内置函数chr,调用内置函数chr时指定ordinal value可以得到其对应的字符
    4. == 与 is 的区别：
       == 比较的是value
       is 比较的是id
"""

print("hello" > "hel") # True
print("hello" > "interest")# False
# 第二个，解释：
print(ord("h"), ord("i"))  #104,105 104<105

a=b="123"
c="123"
print(a == b) # True
print(a is b) # True 
print(a == c) # True
print(a is c) # True 此处显示为true是因为，pycharm做了优化，“123”在驻留池中，a，b，c存储的都是对“123”的引用

```

```python
len("hello") == len("world")
# True
```



#### 常用函数

##### 求长度

内置函数 [`len()`](https://docs.python.org/zh-cn/3.10/library/functions.html#len) 返回字符串的长度：

```python
>>> s = 'supercalifragilisticexpialidocious'
>>> len(s)
34


```

##### 转换大小写

- s.title()

```python
s = "like"
print(s.title()) #以首字母大写的方式显示每个单词→Like 
```

- s.upper()

```python
s = "Like"
print(s.upper()) #以字母大写的方式显示每个单词→LIKE 
```

- s.lower()

```python
s = "LIKE"
print(s.lower()) #以字母小写的方式显示每个单词→like 
```

##### 删除空白

```python
favorite_language = ' python '
print(favorite_language.rstrip()+" 1")
print(favorite_language.lstrip()+" 1")
print(favorite_language.strip()+" 1")
# python 1
#python  1
#python 1
```


##### 数字转字符串

```python
age = 24
message = "Happy "+age+"th Birthday!"
print(message)
# Traceback (most recent call last):
#  File "D:/Python_Projects/Chapter 2.py", line 31, in <module>
#    message = "Happy "+age+"rd Birthday!"
# TypeError: can only concatenate str (not "int") to str

age = 24
message = "Happy "+str(age)+"th Birthday!"
print(message)
# Happy 24th Birthday!
```

##### f-string

f-string用大括{ }表示被替换字段，其中直接填入替换内容即可。

```python3
>>> name = "Huang Wei"
>>> f"Hello, my name is {name}"
'Hello, my name is Huang Wei'

>>> num = 2
>>> f"I have {num} apples"
'I have 2 apples'

>>> price = 95.5
>>> f"He has {price}$"
'He has 95.5$'

>>> x = 123
>>> print(f"{x}:{x}是变量x的值") 
123:123是变量x的值
```

- f-string的大括号{ }可以填入表达式或调用函数，Python会求出其结果并填入返回的字符串内。

```python3
>>> f"They have {2+5*2} apples"
'They have 12 apples'

>>> name = "Huang Wei"
>>> f"my name is {name.lower()}"
'my name is huang wei'

>>> import math
>>> f"Π的值为{math.pi}"
'Π的值为3.141592653589793'
```

- f-string中使用lambda匿名函数：可以做复杂的数值计算

```python3
>>> aa = 123.456
>>> f"{(lambda x:x*5-2)(aa):.2f}"
'615.28'

>>> bb = 8
>>> cc = 2
>>> f"{(lambda x,y:x+y)(bb,cc)}"
'10'
```

##### eval()

**eval()** 函数用来执行一个字符串表达式，并返回表达式的值。

**字符串表达式**可以包含变量、函数调用、运算符和其他 Python 语法元素。

```python
>>>x = 7
>>> eval( '3 * x' )
21
>>> eval('pow(2,2)')
4
>>> eval('2 + 2')
4
>>> n=81
>>> eval("n + 4")
85
```

```python
# 执行简单的数学表达式
result = eval("2 + 3 * 4")
print(result)  # 输出: 14

# 执行变量引用
x = 10
result = eval("x + 5")
print(result)  # 输出: 15

# 在指定命名空间中执行表达式
namespace = {'a': 2, 'b': 3}
result = eval("a + b", namespace)
print(result)  # 输出: 5
```

```python
# 简易计算器的实现
num1 = input("输入一个数字：")
num2 = input("输入另一个数字：")
op = input("输入运算符号：")
result = eval(f"{num1}{op}{num2}")
print(f"运算结果为{result}")
```



##### 统计子串次数

`str.count(sub[, start[, end]])`：返回子字符串sub在[start, end]范围内非重叠出现的次数

```python
"xyxyxyxyz".count('z') # 1
"xyxyxyxyz".count('xy')# 4
"xyxyxyxyz".count('a') # 0
"xyxyxyxyz".count('xy',2,5) # 1
#012345678 ,即xyx
"xyxyxyxyz".count('xy',3,5) # 0
#012345678 ,即yx
```

##### 是否是字母

`str.isalpha()`：如果字符串中的所有字符都是字母，且至少有一个字符，那么返回True, 否则返回False

```python
"xyxyxyxyz".isalpha() # True
```

##### 是否是字母数字

`str.isalnum()`：如果字符串中的所有字符都是字母或数字，且至少有一个字符，那么返回True, 否则返回False

```python
"xyxyxyxyz123".isalnum() # True
"x".isalnum() # True
"3".isalnum() # True
```

##### 用特定字符链接

`str.join(iterable)`：返回一个由 *iterable* 中的字符串拼接而成的字符串

```python
", ".join("abcdefg") # 'a, b, c, d, e, f, g'

"hello".join("world")
# 'whelloohellorhellolhellod'
```

##### 按照特定字符拆分

`str.split(sep=None, maxsplit=-1)`：返回一个由字符串内单词组成的列表，使用sep作为分隔字符串

```python
"a|b|c|d|e|".split("|")
# ['a', 'b', 'c', 'd', 'e', '']
"a|b|c|d|e".split("|")
# ['a', 'b', 'c', 'd', 'e']
```

##### 是否由某字符开始

`str.startswith(prefix[, start[, end]])`：如果字符串以指定的prefix开始，那么返回True, 否则返回False

```python
"xyz".startswith('x') # True
"abandon".startswith('abb') # False
```






### 数字

#### 整数

- \+  、- 、 * 、 **
  - `**` 比 `-` 的优先级更高, 所以 `-32` 会被解释成 `-(3**2)` ，因此，结果是 `-9`。要避免这个问题，并且得到 `9`, 可以用 `(-3)**2

```python
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> 5 ** 2  # 5 squared
25
>>> 2 ** 7  # 2 to the power of 7
128
```

- 除法运算：`/`返回浮点数。`//` 返回整数（忽略小数）
  - `//`也称为整数除法。 结果值是一个整数，但结果的类型不一定是 int。 
  - `//`是向下取整，即运算结果总是向负无穷的方向舍入: `1//2` 为 `0`, `(-1)//2` 为 `-1`, `1//(-2)` 为 `-1` 而 `(-1)//(-2)` 为 `0`。这一点和其他编程语言不同
- 计算余数：`%`

```python
>>> 17 / 3  # classic division returns a float
5.666666666666667
>>> (50 - 5*6) / 4
5.0
>>> 17 // 3  # floor division discards the fractional part
5
>>> 17 % 3  # the % operator returns the remainder of the division
2
>>> 5 * 3 + 2  # floored quotient * divisor + remainder
17
```

#### 浮点数

- 从很大程度上说,使用浮点数时都无需考虑其行为。你只需输入要使用的数字, Python通常都会按你期望的方式处理它们

```python
0.1 + 0.1 # 0.2
2 * 0.2 # 0.4
//结果包含的小数位数可能是不确定的
print(0.2+0.1)	#0.30000000000000004
print(3*0.1)	#0.30000000000000004
```

#### 复数

- 复数包含实部和虚部，分别以一个浮点数表示。 要从一个复数 *z* 中提取这两个部分，可使用 `z.real` 和 `z.imag`。 在数字字面值末尾加上 `'j'` 或 `'J'` 会生成虚数（实部为零的复数），你可以将其与整数或浮点数相加来得到具有实部和虚部的复数。

- *class* `complex`([*real*[, *imag*]])

  返回值为 `real + imag*1j` 的复数，或将字符串或数字转换为复数。如果第一个形参是字符串，则它被解释为一个复数，并且函数调用时必须没有第二个形参。第二个形参不能是字符串。每个实参都可以是任意的数值类型（包括复数）。如果省略了 *imag*，则默认值为零，构造函数会像 `int` 和 `float` 一样进行数值转换。如果两个实参都省略，则返回 `0j`。

```python
>>>complex(1,2)
(1+2j)
>>>complex(1,2)+complex(3,5)
(4+7j)
```

#### 类型转换

![image-20231117151837652](./Python.assets/image-20231117151837652.png)

```python

# 1. float() -- 转换成浮点型
num1 = 1						
print(float(num1))			    # 1.0
print(type(float(num1)))		# <class 'float'>
# 2. str() -- 转换成字符串类型
num2 = 10
print(type(str(num2)))			# <class 'str'>
# 3. tuple() -- 将⼀个序列转换成元组
list1 = [10, 20, 30]
print(tuple(list1))				# (10, 20, 30)
print(type(tuple(list1)))        # <class 'tuple'>
# 4. list() -- 将⼀个序列转换成列表
t1 = (100, 200, 300)
print(list(t1))					# [100, 200, 300]
print(type(list(t1)))			# <class 'list'>
# 5. eval() -- 将字符串中的数据转换成Python表达式原本类型
str1 = '10'
str2 = '[1, 2, 3]'
str3 = '(1000, 2000, 3000)'
print(type(eval(str1)))			# <class 'int'>
print(type(eval(str2)))			# <class 'list'>
print(type(eval(str3)))			# <class 'tuple'>
```







#### 常用函数

##### _

- 交互模式下，上次输出的表达式会赋给变量 `_`。把 Python 当作计算器时，用该变量实现下一步计算更简单，例如

```python
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _
113.0625
>>> round(_, 2)
113.06
```

最好把该变量当作只读类型。不要为它显式赋值，否则会创建一个同名独立局部变量，该变量会用它的魔法行为屏蔽内置变量。

##### abs(x)

返回一个数的绝对值

参数：x为一个数值类型

返回值：返回输入数值的绝对值，即一个非负数

示例：

```python
print(abs(-5)) # 输出 5
```

##### round(x[, n]) 

四舍五入到指定小数位

参数：x为一个数值类型，n为一个整型数字，表示要保留的小数位数。如果未提供n，则默认为0

返回值：返回x四舍五入后的结果

示例：

```python
print(round(3.14159, 2)) # 输出 3.14
```

##### pow(x, y) 

计算一个数的次方

参数：x和y分别为一个数值类型，表示x的y次幂

返回值：返回x的y次幂的结果

示例：

```python
    print(pow(2, 3)) # 输出 8
```

##### math.sqrt(x) 

计算一个数的平方根

参数：x为一个数值类型，代表要计算的数

返回值：返回√x

示例：

```python
import math
print(math.sqrt(25)) # 输出 5.0
```

##### math.floor(x) 

向下取整

参数：x为一个数值类型

返回值：返回≤x的最大整数

示例：

```python
import math
print(math.floor(3.9)) # 输出 3
```

##### math.ceil(x) 

向上取整

参数：x为一个数值类型

返回值：返回≥x的最小整数

示例：

```python
import math
print(math.ceil(3.1)) # 输出 4
```

##### max(iterable[, key=func]) 

返回一组数中的最大值

参数：iterable是一个可迭代对象，key是一个函数用来指定比较大小的规则。如果未提供key，则默认使用数值的大小比较规则

返回值：返回输入对象中的最大值

示例：

```python
print(max(1, 2, 3, 4, 5)) # 输出 5
```

##### min(iterable[, key=func]) 

返回一组数中的最小值

参数：iterable是一个可迭代对象，key是一个函数用来指定比较大小的规则。如果未提供key，则默认使用数值的大小比较规则

返回值：返回输入对象中的最小值

示例：

```python
    print(min(1, 2, 3, 4, 5)) # 输出 1
```

##### sum(iterable[, start=0]) 

对一组数求和

参数：iterable是一个可迭代对象，start是一个可选参数，表示求和的初始值。如果未提供start，则默认为0

返回值：返回输入对象的总和

示例：

```python
print(sum([1, 2, 3, 4, 5])) # 输出 15
```

##### divmod(x, y) 

返回两个数相除的商和余数

参数：x和y分别为一个数值类型，代表要进行除法运算的两个数

返回值：返回包含商和余数的元组

示例：

```python
print(divmod(10, 3)) # 输出 (3, 1)
```









### Python之禅

```python
import this
```

```python
The Zen of Python, by Tim Peters
# 你可以将余生都用来学习Python和编程的纷繁难懂之处,但这样你什么项目都完不成。不要企图编写完美无缺的代码;先编写行之有效的代码,再决定是对其做进一步改进,还是转而去编写新代码
Beautiful is better than ugly.
# 优美胜于丑陋（Python 以编写优美的代码为目标）。Python程序员笃信代码可以编写得漂亮而优雅。编程是要解决问题的,设计良好、高效而漂亮的解决方案都会让程序员心生敬意。随着你对Python的认识越来越深人,并使用它来编写越来越多的代码,有一天也许会有人站在你后面惊呼: “哇,代码编写得真是漂亮!"
Explicit is better than implicit.
# 明了胜于晦涩（优美的代码应当是明了的，命名规范，风格相似）
Simple is better than complex.
# 简洁胜于复杂（优美的代码应当是简洁的，不要有复杂的内部实现）。如果有两个解决方案,一个简单,一个复杂,但都行之有效,就选择简单的解决方案吧。这样,你编写的代码将更容易维护,你或他人以后改进这些代码时也会更容易。
Complex is better than complicated.
# 复杂胜于凌乱（如果复杂不可避免，那代码间也不能有难懂的关系，要保持接口简洁）。现实是复杂的,有时候可能没有简单的解决方案。在这种情况下,就选择最简单可行的解决方案吧。
Flat is better than nested.
# 扁平胜于嵌套（优美的代码应当是扁平的，不能有太多的嵌套）
Sparse is better than dense.
# 间隔胜于紧凑（优美的代码有适当的间隔，不要奢望一行代码解决问题）
Readability counts.
# 即便是复杂的代码,也要让它易于理解。开发的项目涉及复杂代码时,一定要为这些代码编,写有益的注释。
Special cases aren't special enough to break the rules.
Although practicality beats purity.
# 即便假借特例的实用性之名，也不可违背这些规则（这些规则至高无上）
Errors should never pass silently.
Unless explicitly silenced.
# 不要包容所有错误，除非你确定需要这样做（精准地捕获异常，不写 except:pass 风格的代码）
In the face of ambiguity, refuse the temptation to guess.
# 当存在多种可能，不要尝试去猜测
There should be one-- and preferably only one --obvious way to do it.
# 而是尽量找一种，最好是唯一一种明显的解决方案（如果不确定，就用穷举法）。如果让两名Python程序员去解决同一个问题,他们提供的解决方案应大致相同。这并不是说编程没有创意空间,而是恰恰相反!然而,大部分编程工作都是使用常见解决方案来解决简单的小问题,但这些小问题都包含在更庞大、更有创意空间的项目中。在你的程序中,各种具体细节对其他Python程序员来说都应易于理解。
Although that way may not be obvious at first unless you're Dutch.
# 虽然这并不容易，因为你不是 Python 之父（这里的 Dutch 是指 Guido ）
Now is better than never.
Although never is often better than *right* now.
# 做也许好过不做，但不假思索就动手还不如不做（动手之前要细思量）
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
#如果你无法向人描述你的方案，那肯定不是一个好方案；反之亦然（方案测评标准）
Namespaces are one honking great idea -- let's do more of those!
# 命名空间是一种绝妙的理念，我们应当多加利用（倡导与号召）
```

​	大多数语言都能以不同的风格被编写（或更准确地说，被格式化）；有些比其他的更具有可读性。 能让其他人轻松阅读你的代码总是一个好主意，采用一种好的编码风格对此有很大帮助。

​	Python 项目大多都遵循 [**PEP 8**](https://www.python.org/dev/peps/pep-0008) 的风格指南；它推行的编码风格易于阅读、赏心悦目。Python 开发者均应抽时间悉心研读；以下是该提案中的核心要点：

- 缩进，用 4 个空格，不要用制表符。

  4 个空格是小缩进（更深嵌套）和大缩进（更易阅读）之间的折中方案。制表符会引起混乱，最好别用。

- 换行，一行不超过 79 个字符。

  这样换行的小屏阅读体验更好，还便于在大屏显示器上并排阅读多个代码文件。

- 用空行分隔函数和类，及函数内较大的代码块。

- 最好把注释放到单独一行。

- 使用文档字符串。

- 运算符前后、逗号后要用空格，但不要直接在括号内使用： `a = f(1, 2) + g(3, 4)`。

- 类和函数的命名要一致；按惯例，命名类用 `UpperCamelCase`，命名函数与方法用 `lowercase_with_underscores`。命名方法中第一个参数总是用 `self` (类和方法详见 [初探类](https://docs.python.org/zh-cn/3.10/tutorial/classes.html#tut-firstclasses))。

- 编写用于国际多语环境的代码时，不要用生僻的编码。Python 默认的 UTF-8 或纯 ASCII 可以胜任各种情况。

- 同理，就算多语阅读、维护代码的可能再小，也不要在标识符中使用非 ASCII 字符。



## 3. 列表

> 列表让你能够在一个地方存储成组的信息，其中可以只包含几个元素，也可以包含数百万个元素。列表是最强大的Python功能之一，它融合了众多重要的编程概念。

### 定义

- 列表中可以存放一系列对象
- 存放的对象可以是**数字**、**字符串**也可以是**列表**
- 列表用方括号“[]”表示，每个对象称作列表的**元素**，元素之间使用逗号**“，”**分隔
- 列表中的元素**可以**在定义列表之后进行**修改**，也可以使用索引来访问一个或多个元素
- 列表也支持了**丰富的内置函数**



### 赋值与拷贝

#### 列表赋值

​	在Python中，列表属于可变对象，而对可变对象的**复制**其实就是将**列表的内存空间**（类似C中的指针）再次**指向新的变量名**，而不是诸如字符串这种不可变对象在复制时会创建新的内存空间进行赋值。即此时b和a指向的是同一片内存空间。

```python
x = [1,2]
y = [3,4]
a = [x,y]
b = a     # 列表赋值：相当于起别名，b是a的指针
b[0] = 'abc'
print(a)  # ['abc', [3, 4]]
print(b)  # ['abc', [3, 4]]
```

```python
x = [1,2]
y = [3,4]
a = [x,y]
b = a[:]     # 浅拷贝：相当于复制，b是a的一个副本
b[0] = 'abc'
print(a)  # [[1, 2], [3, 4]]
print(b)  # ['abc', [3, 4]]
```

#### 浅拷贝

当列表中的元素为不可变对象时，我们可以用以下方法对列表进行赋值：

```python
# 定义一个新列表
L0 = [1, 2, 3, 4, 5]
print(L0)
print('-'*40)
```

##### 利用切片

```python
L1 = L0[:]
L1[0] = 100
print(L0)
```

##### 利用copy模块

```python
import copy
L2 = copy.copy(L0)
L2[0] = 100
print(L0)
```

##### 利用list()

```python
L3 = list(L0)
L3[0] = 100
print(L0)
```

##### 利用列表方法extend

```python
L4 = []
L4.extend(L0)
L4[0] = 100
print(L0)
```

##### 利用列表推导

```python
L5 = [i for i in L0]
L5[0] = 100
print(L0)
```

可以看到最终的打印结果都是`[1, 2, 3, 4, 5]`，我们成功进行了列表的复制，但是如果要求列表中元素为不可变对象呢？ 因为**如果列表中的元素为可变对象，在复制时会发生对象的引用**，而不是新建内存空间进行引用，比如：

```python
L0 = [1, 2, [3], 4, 5]
print(L0)				# [1, 2, [3], 4, 5]
L2 = L0[:]
L2[2][0] = 100
print(L0)  				# [1, 2, [100], 4, 5]
```

可以看到，当列表L0中含有可变对象时，对复制后的L1进行改变其中可变对象元素L2[2]时，L0中的可变对象L0[2]也发生了改变，那么怎么实现真正的完全的拷贝呢？

#### 深拷贝

利用copy模块中的deepcopy进行深拷贝：

```python
import copy
L0 = [1, 2, [3], 4, 5]
print(L0)
L2 = copy.deepcopy(L0)
L2[2][0] = 100
print(L2)
print(L0)
```

示例结果：

```python
[1, 2, [100], 4, 5]
[1, 2, [3], 4, 5]
```



### 访问列表

> 列表是有顺序的，所以可以通过索引访问其中的元素

```python
bicycles = ['trek','cannondale','redline','specialized']
print(bicycles) #全部列表
print(bicycles[0]) #第1个
print(bicycles[0].title()) #按首字母大写输出
print(bicycles[1]) #第2个
print(bicycles[3]) #第4个
print(bicycles[-1]) #最后一个
print(bicycles[-2]) #倒数第2个
# ['trek', 'cannondale', 'redline', 'specialized']
# trek
# Trek
# cannondale
# specialized
# specialized
# redline
```

```python
bicycles = ['trek','cannondale','redline','specialized']
message = "My first ficycle was a " +bicycles[0].title()+"."
print(message)
# My first ficycle was a Trek.
```

### 添加元素


- 指定位置k插入XXX：list.insert(k, "XXX")

```python
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles) # ['honda', 'yamaha', 'suzuki']

motorcycles.insert(2,"ducati")
print(motorcycles) # ['honda', 'yamaha', 'ducati', 'suzuki']
```

- 末尾添加：list.append("XXX")

```python
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles) # ['honda', 'yamaha', 'suzuki']

motorcycles.append("ducati")
print(motorcycles) # ['honda', 'yamaha', 'suzuki', 'ducati']
```

- 末尾添加：list += [XXX]
- 扩展元素：list.extend(可迭代对象*)

```python
list_demo = ['a', 'b', 'c', 'd', 'e', ['f','g']]
print(type(list_demo))
print(list_demo)
list_demo.insert(0,"first")
print(list_demo)
list_demo.insert(-1,"last") # 即使在最后一个插入，也是插入到倒数第二个，想要插入到末尾，需要用append函数
print(list_demo)
list_demo.append("last_one") # 插入到末尾
print(list_demo)
list_demo.extend("last_one") # 将其视为可迭代对象（列表），逐个字符插入
print(list_demo)

# <class 'list'>
# ['a', 'b', 'c', 'd', 'e', ['f', 'g']]
# ['first', 'a', 'b', 'c', 'd', 'e', ['f', 'g']]
# ['first', 'a', 'b', 'c', 'd', 'e', 'last', ['f', 'g']]
# ['first', 'a', 'b', 'c', 'd', 'e', 'last', ['f', 'g'], 'last_one']
# ['first', 'a', 'b', 'c', 'd', 'e', 'last', ['f', 'g'], 'last_one', 'l', 'a', 's', 't', '_', 'o', 'n', 'e']
```



### 修改元素

- 直接按列表位置修改即可

```python
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles)# ['honda', 'yamaha', 'suzuki']
 
motorcycles[0] = 'ducati'
print(motorcycles)# ['ducati', 'yamaha', 'suzuki']
```

- `list.remove(元素)`移除列表的元素
- `list.reverse()`反转列表元素的顺序
- `list.pop(索引)`移除索引对应的元素并返回该元素，不指定索引除最后一个元素
- `list.copy()`复制列表
- `list.ciear()`清空列表

```python
list_demo = ['a', 'b', 'c', 'd', 'e', ['f','g']]
print(type(list_demo))
print(list_demo)
list_demo.insert(0,"first")
print(list_demo)
list_demo.insert(-1,"last") # 即使在最后一个插入，也是插入到倒数第二个，想要插入到末尾，需要用append函数
print(list_demo)
list_demo.append("last_one") # 插入到末尾
print(list_demo)
list_demo.remove("last_one") # 指定删除某元素(按值)
print(list_demo)
list_demo.reverse() # 翻转列表
print(list_demo)
list_demo.pop(2) #指定删除第3个元素（按序号）
print(list_demo)
list_demo.pop() #不指定，默认删除末尾元素
print(list_demo)
tmp = list_demo.copy()
print(tmp) 
list_demo.clear()
print(list_demo)

# <class 'list'>
# ['a', 'b', 'c', 'd', 'e', ['f', 'g']]
# ['first', 'a', 'b', 'c', 'd', 'e', ['f', 'g']]
# ['first', 'a', 'b', 'c', 'd', 'e', 'last', ['f', 'g']]
# ['first', 'a', 'b', 'c', 'd', 'e', 'last', ['f', 'g'], 'last_one']
# ['first', 'a', 'b', 'c', 'd', 'e', 'last', ['f', 'g']]
# [['f', 'g'], 'last', 'e', 'd', 'c', 'b', 'a', 'first']
# [['f', 'g'], 'last', 'd', 'c', 'b', 'a', 'first']
# [['f', 'g'], 'last', 'd', 'c', 'b', 'a']
# [['f', 'g'], 'last', 'd', 'c', 'b', 'a']
# []
```

为切片赋值可以改变列表大小，甚至清空整个列表：

```python
>>> letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> letters
['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> # replace some values
>>> letters[2:5] = ['C', 'D', 'E']
>>> letters
['a', 'b', 'C', 'D', 'E', 'f', 'g']
>>> # now remove them
>>> letters[2:5] = []
>>> letters
['a', 'b', 'f', 'g']
>>> # clear the list by replacing all the elements with an empty list
>>> letters[:] = []
>>> letters
[]
```



### 删除元素

- **指定值**删除：list.remove("XXX")
  - 从列表中**删除第一个值为 *x* 的元素**


```python
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles) 
too_expensive = 'yamaha'
motorcycles.remove("yamaha")
print(motorcycles) 
print("\nA "+too_expensive.title()+" is too expensive for me.")
# ['honda', 'yamaha', 'suzuki']
# ['honda', 'suzuki']

# A Yamaha is too expensive for me.
```

- **指定位置**删除：del list[k]

```python
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles) # ['honda', 'yamaha', 'suzuki']

del motorcycles[2]
print(motorcycles) # ['honda', 'yamaha']
```


- **末尾**删除：list.pop()
  - 移除列表中的一个元素（默认最后一个元素），并且返回该元素的值。
    - list.pop(2)：指定删除第3个元素
  - **append和pop就类似于栈的入栈和出栈操作。都在末尾进行**

```python
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles) # ['honda', 'yamaha', 'suzuki']

poped_motorcycle = motorcycles.pop() # 删除元素的同时返回被删除的元素
print(motorcycles)   # ['honda', 'yamaha']
print(poped_motorcycle) # suzuki
```

```python
last_owned = motorcycles.pop()
print("The last motorcycle I owned was a "+last_owned.title()+".")
# The last motorcycle I owned was a Suzuki.
```

- **清空**列表：list.clear()
  - 删除列表里的所有元素，相当于 `del a[:]` 。

### 举例

```python
>>> fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
>>> fruits.count('apple')
2
>>> fruits.count('tangerine')
0
>>> fruits.index('banana')
3
>>> fruits.index('banana', 4)  # Find next banana starting a position 4
6
>>> fruits.reverse()
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']
>>> fruits.append('grape')
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange', 'grape']
>>> fruits.sort()
>>> fruits
['apple', 'apple', 'banana', 'banana', 'grape', 'kiwi', 'orange', 'pear']
>>> fruits.pop()
'pear'
```

`insert`、`remove`、`sort` 等方法只修改列表，不输出返回值——返回的默认值为 `None` 。这是所有 Python 可变数据结构的设计原则。

还有，不是所有数据都可以排序或比较。例如，`[None, 'hello', 10]` 就不可排序，因为整数不能与字符串对比，而 *None* 不能与其他类型对比。有些类型根本就没有定义顺序关系，例如，`3+4j < 5+7j` 这种对比操作就是无效的。

### 组织列表（常用函数）

#### 合并

```python
>>> squares = [1, 4, 9, 16, 25]
>>> squares + [36, 49, 64, 81, 100] 
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

#### 排序

- 永久排序sort()

```python
cars = ['bmw','audi','toyota','subaru']
cars.sort()	# 字母表顺序
print(cars)  # ['audi', 'bmw', 'subaru', 'toyota']

cars.sort(reverse=True) # 字母表倒序
print(cars)   # ['toyota', 'subaru', 'bmw', 'audi']
```

- 临时排序sorted()
  - 只使用，不改变原有数据，不存储


```python
cars = ['bmw','audi','toyota','subaru']
print(cars)
print(sorted(cars))
print(cars)

# ['bmw', 'audi', 'toyota', 'subaru']
# ['audi', 'bmw', 'subaru', 'toyota']
# ['bmw', 'audi', 'toyota', 'subaru']
```

#### 翻转

- reverse()

```python
cars = ['bmw','audi','toyota','subaru']
cars.reverse()
print(cars) # ['subaru', 'toyota', 'audi', 'bmw']
```

#### 列表长度 / 元素个数

> Python计算列表元素数时从1开始，因此确定列表长度时，你不会遇到差一错误。

- len()

```python
cars = ['bmw','audi','toyota','subaru']
print(len(cars))  # 4
```

#### 索引错误

```python
cars = ['bmw','audi','toyota','subaru']
print(cars[4])

# Traceback (most recent call last):
#   File "D:/Python_Projects/Chapter 3.py", line 62, in <module> print(cars[4])
# IndexError: list index out of range
```

#### 嵌套列表

- 还可以嵌套列表（创建包含其他列表的列表），例如：

```python
>>> a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]
>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'
```



#### 计算 / 统计

```python
digits = [1,2,3,4,5,6,7,8,9,0]
print(min(digits)) # 0
print(max(digits)) # 9
print(sum(digits)) # 45

digits = [1,2,2,3,3,3,4,4,4,4]
digits.count(3) # 3
```

- 求平均：numpy.mean(digits)
- 计数：list.count(*x*)
  - 返回列表中元素 *x* 出现的次数，注意x不是下标





#### for循环输出


```python
magicians = ['alice', 'david', 'carolina']
for magician in magicians:  #从列表magicians中的名字中取出一个，将其存储在变量magician中
    print(magician)
# alice
# david
# carolina
```

- 编写for循环时，对于用于存储列表中每个值的临时变量，可指定任何名称。尽量选择有意义的名称。

```Python
for cat in cats:
for dog in dogs:
for item in list of items:
```

#### for循环（more）

```python
magicians = ['alice', 'david', 'carolina']
for magician in magicians: 
    print(magician.title()+",that was a great trick!")
    print("I can't wait to see your next trick, "+magician.title()+".\n")
    
# Alice,that was a great trick!
# I can't wait to see your next trick, Alice.
# 
# David,that was a great trick!
# I can't wait to see your next trick, David.
# 
# Carolina,that was a great trick!
# I can't wait to see your next trick, Carolina.
```

#### 创建数值列表

##### 使用函数range()

- range(a,b) 从指定的a开始，到达指定的b值前一个数停止
  - —— [a，b）
- 使用range()时， 如果输出不符合预期，请尝试将指定的值加1或减1。

```python
for value in range(1,6):
    print(value)
# 1
# 2
# 3
# 4
# 5
```

- 用list()函数输出一个列表

```python
numbers = list(range(1,6))
print(numbers)
# [1, 2, 3, 4, 5]
```

- 间隔：range()函数的第三个参数

```python
even_numbers = list(range(2,11,2))
print(even_numbers)
# [2, 4, 6, 8, 10]
```

- range()几乎能够==创建任何需要的数字集==

```python
squares = []
for value in range(1,11):
    # square = value**2
    # squares.append(square)
    squares.append(value**2)
print(squares)

# [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```


#### 列表解析

- 前面介绍的生成列表squares的方式包含三四行代码，而列表解析让你**只需编写一行代码就能生成这样的【列表】**。列表解析将for循环和创建新元素的代码合并成一行， 并自动附加新元素。
- 面向初学者的书籍并非都会介绍列表解析，这里之所以介绍列表解析，是因为等你开始阅读他人编写的代码时，很可能会遇到它们。

```python
# 功能同上
squares = [value**2 for value in range(1,11)]
print(squares)
```

- ==要能够生成属于自己的列表解析风格==needs practice

##### 举例

```python
# 输出0~100内的所有偶数
a=[]
for i in range(101):
    if i%2==0:
        a.append(i)
#----------------------------------------------#
a=[x for x in range(101) if x%2==0]
```

```python
# 获取文本中所有单词的第1个字符
text="My house is full of flowers"
first_charts=[]
for word in text.split():
    first_charts.append(word[0])
#-----------------------------------------------#
first_charts=[word[0] for word in text.split()]
```

```python
#list a=['1','2','3','i','8'],将a中所有能转化为数字的字符串转化为数字，不为数字的内容都转换成0
[int(i) if i.isdigit() else 0 for i in a]
# [1,2,3,0,8]
```



#### 使用列表的一部分

##### 切片

```python
players = ['charles','martina','michael','florence','eli']
print(players[1:3])  # ['martina', 'michael']
#同range()也是【左闭右开】区间

players = ['charles','martina','michael','florence','eli']
print(players[0:3]) # ['charles','martina', 'michael']

#没有指定起始索引，Python从列表开头开始提取
print(players[:3])  # ['charles','martina', 'michael']

#没有指定结束索引，Python列表提取至末尾元    
print(players[2:])  # ['michael','florence','eli']

#负索引返回离列表末尾相应距离的元素，因此可以输出列表末尾的任何切片
#打印最后三个，即使列表长度变化也是如此
print(players[-3:]) # ['michael','florence','eli']
```

##### 遍历切片

```python
players = ['charles','martina','michael','florence','eli']
print("Here are the first three players on my team:")
for player in players[:3]:
    print(player.title())
# Here are the first three players on my team:
# Charles
# Martina
# Michael
```

##### 用切片复制列表

- `copy_list = list[:]`
- 当然直接`copy_list = list`复制列表也是可以的

```python
my_foods = ['pizze','falafel','carrot cake']
friend_foods = my_foods[:]

my_foods.append('ice cream')
friend_foods.append('cannoli')

print("My favorite foods are:")
print(my_foods)
print("\nMy friends's favorite are:")
print(friend_foods)

# My favorite foods are:
# ['pizze', 'falafel', 'carrot cake', 'ice cream']
#
# My friends's favorite are:
# ['pizze', 'falafel', 'carrot cake', 'cannoli']
```

### 列表推导式

列表推导式创建列表的方式更简洁。常见的用法为，对序列或可迭代对象中的每个元素应用某种操作，用生成的结果创建新的列表；或用满足特定条件的元素创建子序列。

例如，创建平方值的列表：

```python
>>> squares = []
>>> for x in range(10):
...     squares.append(x**2)
...
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

注意，这段代码创建（或覆盖）变量 `x`，该变量在循环结束后仍然存在。下述方法可以无副作用地计算平方列表：

```python
squares = list(map(lambda x: x**2, range(10)))
```

或等价于：

```python
squares = [x**2 for x in range(10)]
```

上面这种写法更简洁、易读。

列表推导式的方括号内包含以下内容：一个表达式，后面为一个 `for` 子句，然后，是零个或多个 `for` 或 `if` 子句。结果是由表达式依据 `for` 和 `if` 子句求值计算而得出一个新列表。 举例来说，以下列表推导式将两个列表中不相等的元素组合起来：

```python
>>> [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

等价于：

```python
>>> combs = []
>>> for x in [1,2,3]:
...     for y in [3,1,4]:
...         if x != y:
...             combs.append((x, y))
...
>>> combs
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

注意，上面两段代码中，[`for`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#for) 和 [`if`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#if) 的顺序相同。

表达式是元组（例如上例的 `(x, y)`）时，必须加上括号：

```python
>>> vec = [-4, -2, 0, 2, 4]
>>> # create a new list with the values doubled
>>> [x*2 for x in vec]
[-8, -4, 0, 4, 8]
>>> # filter the list to exclude negative numbers
>>> [x for x in vec if x >= 0]
[0, 2, 4]
>>> # apply a function to all the elements
>>> [abs(x) for x in vec]
[4, 2, 0, 2, 4]
>>> # call a method on each element
>>> freshfruit = ['  banana', '  loganberry ', 'passion fruit  ']
>>> [weapon.strip() for weapon in freshfruit]
['banana', 'loganberry', 'passion fruit']
>>> # create a list of 2-tuples like (number, square)
>>> [(x, x**2) for x in range(6)]
[(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
>>> # the tuple must be parenthesized, otherwise an error is raised
>>> [x, x**2 for x in range(6)]
  File "<stdin>", line 1
    [x, x**2 for x in range(6)]
     ^^^^^^^
SyntaxError: did you forget parentheses around the comprehension target?
>>> # flatten a list using a listcomp with two 'for'
>>> vec = [[1,2,3], [4,5,6], [7,8,9]]
>>> [num for elem in vec for num in elem]
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

列表推导式可以使用复杂的表达式和嵌套函数：

```python
>>> from math import pi
>>> [str(round(pi, i)) for i in range(1, 6)]
['3.1', '3.14', '3.142', '3.1416', '3.14159']
```

### 嵌套的列表推导式

列表推导式中的初始表达式可以是任何表达式，甚至可以是另一个列表推导式。

下面这个 3x4 矩阵，由 3 个长度为 4 的列表组成：

```python
>>> matrix = [
...     [1, 2, 3, 4],
...     [5, 6, 7, 8],
...     [9, 10, 11, 12],
... ]
```

下面的列表推导式可以转置行列：

```python
>>> [[row[i] for row in matrix] for i in range(4)]
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

如上节所示，嵌套的列表推导式基于其后的 [`for`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#for) 求值，所以这个例子等价于：

```python
>>> transposed = []
>>> for i in range(4):
...     transposed.append([row[i] for row in matrix])
...
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

反过来说，也等价于：

```python
>>> transposed = []
>>> for i in range(4):
...     # the following 3 lines implement the nested listcomp
...     transposed_row = []
...     for row in matrix:
...         transposed_row.append(row[i])
...     transposed.append(transposed_row)
...
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

**实际应用中，最好用内置函数替代复杂的流程语句**。此时，[`zip()`](https://docs.python.org/zh-cn/3.10/library/functions.html#zip) 函数更好用：

```python
>>> list(zip(*matrix))
[(1, 5, 9), (2, 6, 10), (3, 7, 11), (4, 8, 12)]
```

## 4. 元组

> **值不可被修改的列表。**相比于列表，元组是更简单的数据结构。如果需要存储的一组值在程序的整个生命周期内都不变，可使用元组。列表适合用于存储在**程序运行期间可能变化的数据集**。列表是可以修改的，这对处理网站的用户列表或游戏中的角色列表至关重要。然而，有时候你需要创建一系列不可修改的元素，元组可以满足这种需求。Python将不能修改的值称为不可变的，而**不可变的列表**被称为元组。
>
> 序列分为:可变序列和不可变序列
>
> - **列表**属于可变序列
> - **元组**、**字符串**属于不可变序列
> - 不可变序列中，append()、 pop()、 insert() 等修改序列元素的函数均无法使用
> - 列表是`list0=[1,2,3]`，元组是`tuple0=(1,2,3)`
> - 对不应变化的值提供了一定程度的保护

### 序列的通用操作

![image-20231117191553557](./Python.assets/image-20231117191553557.png)

> 只要对原有内容有修改，那元组都用不了：
>
> 1. 元组和列表创建之后，元组不可修改，列表可修改
> 2. **元组执行效率高**，
>    列表执行效率低（定义好之后无须修改，所以不会占用很多内存）

### 创建元组

- 可以使用圆括号“()”定义元组
- 可以使用tuple()函数创建元组
- 将range()、列表、字符串转换为元组

#### 定义元组

```python
str_1 = [x for x in range(1,6)]
str_2 = [1,2,3,4,5]
str_3 = '''lisi'''
list_1 = tuple(str_1)
list_2 = tuple(str_2)
list_3 = tuple(str_3)
print(type(list_1))
print(list_1)
print(type(list_2))
print(list_2)
print(type(list_3))
print(list_3)

tuple_demo1 = (1,2,4,8,16,32, 64, 128, 256, 512, 1024)
tuple_demo2 = tuple([2**i for i in range(0,11) ])
print(type(tuple_demo1))
print(tuple_demo1)
print(type(tuple_demo2))
print(tuple_demo2)

# <class 'tuple'>
# (1, 2, 3, 4, 5)
# <class 'tuple'>
# (1, 2, 3, 4, 5)
# <class 'tuple'>
# ('l', 'i', 's', 'i')
# <class 'tuple'>
# (1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024)
# <class 'tuple'>
# (1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024)
```

```python
dimesions = (200,50)
print(dimesions[0]) # 200
print(dimesions[1]) # 50

# 元组是不可改变的，无法被赋值
dimesions[0] = 250
# Traceback (most recent call last):
#   File "D:/Python_Projects/Chapter 4.py", line 63, in <module>
#     dimesions[0] = 250
# TypeError: 'tuple' object does not support item assignment
```

#### 遍历元组

```python
dimesions = (200,50,30,10)
for dimesion in dimesions:
    print(dimesion)
# 200
# 50
# 30
# 10
```

#### 修改元组

- 虽然不能修改元组的元素，但可以给存储元组的变量赋值。因此，如果要修改前述矩形的尺寸，可重新定义(赋值)整个元组:

```python
dimesions = (200,50,30,10)
print("Origianl dimesions:")
for dimesion in dimesions:
    print(dimesion)
    
dimesions = (400,100)
print("\nModified dimesions:")
for dimesion in dimesions:
    print(dimesion)

# Origianl dimesions:
# 200
# 50
# 30
# 10
# 
# Modified dimesions:
# 400
# 100
```



### 删除元组

- 使用del
- 



```python
# 1、增加元素 报错
tuple_demo = ('x', 'y', 'z')
print(tuple_demo.append('a'))
# AttributeError: 'tuple' object has no attribute 'append'

# 2、删除元素 报错
tuple_demo = ('x', 'y', 'z')
print(tuple_demo.remove('z'))
# AttributeError: 'tuple' object has no attribute 'remove'

# 3、元素索引操作
tuple_demo = ('x', 'y', 'z')
print(tuple_demo.insert(3, 'a'))
# AttributeError: 'tuple' object has no attribute 'insert'

# 索引：
tuple_demo = ('x', 'y', 'z')
for i in range(len(tuple_demo)):
    print(tuple_demo[i])
# x
# y
# z
```



## 5. 集合

集合是由不重复元素组成的无序容器。基本用法包括成员检测、消除重复元素。集合对象支持合集、交集、差集、对称差分等数学运算。

创建集合用花括号或 [`set()`](https://docs.python.org/zh-cn/3.10/library/stdtypes.html#set) 函数。注意，创建空集合只能用 `set()`，不能用 `{}`，`{}` 创建的是空字典，下一小节介绍数据结构：字典。

`set()`取集合后的元素是无序的

```python
color = ('r', 'g', 'b', 'g', 'b', 'b') # 初始tuple
new_color = set(color) # 用set筛选不重复的元素
print(new_color) # {'g', 'b', 'r'}


new_color_2 = tuple(new_color) # 再将其转换成tuple
print(new_color_2) # ('g', 'b', 'r')
```

以下是一些简单的示例

```python
basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
print(basket)                  # 重复的部分会被去掉
print('orange' in basket)      # 快速成员判定
print('crabgrass' in basket)
# 对两个单词中的唯一字母的集合运算
a = set('abracadabra')
b = set('alacazam')
print(a)                        # 集合a中用到的字母
print(a - b)                    # 集合a中用到且不再b中的字母
print(a | b)                    # 在集合a或者集合b中的字母
print(a & b)                    # 既在集合a中又在集合b中的字母
print(a ^ b)                    # 在集合a或者b中，但不都在二者里的字母

# {'pear', 'apple', 'orange', 'banana'}
# True
# False
# {'r', 'b', 'a', 'd', 'c'}
# {'d', 'r', 'b'}
# {'r', 'z', 'b', 'a', 'l', 'd', 'm', 'c'}
# {'a', 'c'}
# {'r', 'd', 'z', 'l', 'b', 'm'}
```

与 [列表推导式](https://docs.python.org/zh-cn/3.10/tutorial/datastructures.html#tut-listcomps) 类似，集合也支持推导式：

```python
a = {x for x in 'abracadabra' if x not in 'abc'}
print(a) # {'d', 'r'}
```

### 常用操作

`len(s)`：返回集合s的元素数量
`x in s`：检测x是否为s中的成员
`set <= other`：检测集合set中的每个元素是否在other中
`set < other`：检测集合set是否为other的真子集

```python
color = ('r', 'g', 'b', 'g', 'b', 'b') 
new_color = set(color) # 用set筛选不重复的元素
print(new_color)
print(len(new_color)) # 3
print('r' in new_color) # True
print({'r','g','b'} <= new_color) # True
print({'r','g','b'} < new_color)  # False
```

其他内置函数：add()、remove()、pop()、clear()都能实现对集合的原地修改

```python
color = ('r', 'g', 'b', 'g', 'b', 'b') 
new_color = set(color) # 用set筛选不重复的元素

new_color.add('t')
print(new_color)
new_color.remove('b')
print(new_color)
new_color.pop()
print(new_color)
new_color.clear()
print(new_color)

# {'t', 'g', 'b', 'r'}
# {'t', 'g', 'r'}
# {'g', 'r'}
# set()
```





## 6. 字典

> 映射与字典：
>
> - 映射是可变类型
> - 映射**只有一种**数据类型：字典
> - 整数1和浮点数1.0会被当做相同的键
>
> 在Python中，字典是一系列**键-值对**。每个键都与一个值相关联，你可以使用键来访问与之相关联的值。**键不能重复**，因此无法哈希的类型，如列表、字典等，不可作为键来使用；**与键相关联的值**可以是数字、字符串、列表乃至字典。事实上，可将任何Python对象用作字典中的值。
>
> 键值对是两个相关联的值。指定键时，Python将返回与之相关联的值。键和值之间用冒号分隔，而键值对之间用逗号分隔。在字典中，你想存储多少个键值对都可以。

```python
alien_0 = {'color':'green','points':5}
```

### 定义字典

1. 使用花括号定义: `{ 'one': 1, 'two' : 2 }`
2. 使用类型构造器: `dict(one=1, two=2)`
3. 使用字典推导式: `{ x: x**2 for x in range(10) }`

```python
tel = {'jack': 4098, 'sape': 4139}
tel['guido'] = 4127
# 输出字典
print(tel)               # {'jack': 4098, 'sape': 4139, 'guido': 4127}
print(tel['jack'])       # 4098
# 删除字典中的键
del tel['sape'] 
print(tel)               # {'jack': 4098, 'guido': 4127}
# 修改字典中键的值  
tel['guido'] = 4128
print(tel)               # {'jack': 4098, 'guido': 4128}
# 将字典转换成列表
print(list(tel))         # ['jack', 'guido']
print(sorted(tel))       # ['guido', 'jack']
# 查询字典中的键存在与否
print('guido' in tel)    # True
print('jack' not in tel) # False
```



### 使用字典

#### 访问字典

- 访问全部字典内容，直接`dict`
- 访问字典的所有键：`dict.key()`
- 访问字典的所有值：`dict.value()`
- 访问某个键key1的值：
  - `dict(key1)`
  - `dict.get(key1)`

```python
# 访问列表里的所有元素
mail_list = {'tom': 'tom@gmail.com', 'jerry': 'jerry@foxmail.com', 'john': 'john@163.com'}

# 全部
mail_list.items() 
# dict_items([('tom', 'tom@gmail.com'), ('jerry', 'jerry@foxmail.com'), ('john', 'john@163.com')])

# 键
mail_list.keys() 
# dict_keys(['tom', 'jerry', 'john'])

# 值
mail_list.values() 
# dict_values(['tom@gmail.com', 'jerry@foxmail.com', 'john@163.com'])

#某键的值
mail_list.get('tom') 
# 'tom@gmail.com'
```

#### 添加键值对

- 直接指定`dict[key] = value`
- `dict.update(key = value)`

```python
mail_list = {'tom': 'tom@gmail.com', 'jerry': 'jerry@foxmail.com', 'john': 'john@163.com'}
mail_list['zhangsan'] = 'zhangsan@163.com'
mail_list.update(lisi ='lisi@163.com')
for key, value in mail_list.items():
    print(key,":",value)

# tom : tom@gmail.com
# jerry : jerry@foxmail.com
# john : john@163.com
# zhangsan : zhangsan@163.com
# lisi : lisi@163.com
```



#### 修改字典中的值

```python
alien_0 = {'color': 'green'}
print("The alien is "+alien_0['color']+".")
alien_0['color'] = 'yellow'
print("The alien is now "+alien_0['color']+".")
# The alien is green.
# The alien is now yellow.
```

```python
alien_0 = {'x_position': 0, 'y_position': 25, 'speed': 'fast'}
print("Original x-position: " + str(alien_0['x_position']))

# 向右移动外星人
# 据外星人当前速度决定将其移动多远
if alien_0['speed'] == 'slow':
    x_increment = 1
elif alien_0['speed'] == 'medium':
    x_increment = 2
else:
    # 这个外星人的速度一定很快
    x_increment = 3
    # 或者直接改变外星人的行为
    alien_0['speed'] = 'very fast'

alien_0['x_position'] = alien_0['x_position'] + x_increment
print("New x-position: " + str(alien_0['x_position']))
print("The alien's speed state is: "+ alien_0['speed'])
# Original x-position: 0
# New x-position: 3
# The alien's speed state is: very fast
```

#### 删除字典

- `del dict[key]`：删除字典中的key键和它的值

```python
test_dict = {"Runoob" : 1, "Google" : 2, "Taobao" : 3, "Zhihu" : 4} 
  
# 输出原始的字典
print ("字典移除前 : " + str(test_dict)) 
  
# 使用 del 移除 Zhihu
del test_dict['Zhihu'] 
  
# 输出移除后的字典
print ("字典移除后 : " + str(test_dict)) 
  
# 移除没有的 key 会报错
#del test_dict['Baidu']

# 字典移除前 : {'Runoob': 1, 'Google': 2, 'Taobao': 3, 'Zhihu': 4}
# 字典移除后 : {'Runoob': 1, 'Google': 2, 'Taobao': 3}
```



#### 由类似对象组成的字典

```python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'c++'
}
print("Edward's favorite language is "+
      favorite_languages['edward'].title()+".")
# Edward's favorite language is Ruby.
```

### 遍历字典

#### 遍历所有键值对

```python
bin = { x: 2**x for x in range(11) }
for key,value in bin.items():
    print(key,":",value)
# 0 : 1
# 1 : 2
# 2 : 4
# 3 : 8
# 4 : 16
# 5 : 32
# 6 : 64
# 7 : 128
# 8 : 256
# 9 : 512
# 10 : 1024
```



```python
user_0 = {
    'username': 'efermi',
    'first': 'enrico',
    'last': 'fermi'
}
for key, value in user_0.items():
    print("Key: " + key)
    print("Value: " + value+"\n")

# Key: username
# Value: efermi
# 
# Key: first
# Value: enrico
# 
# Key: last
# Value: fermi
```

> 注意，即便遍历字典时，键值对的返回顺序也与存储顺序不同。Python**不关心键值对的存储顺序**，而只跟踪键和值之间的关联关系。

#### 遍历字典中的所有键

```python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'c++'
}
for name in favorite_languages.keys():
    print(name.title())
# Jen
# Sarah
# Edward
# Phil
```

```python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'c++'
}
friends = ['phil', 'sarah']
for name in favorite_languages.keys():
    print(name.title())
    if name in friends:
        print("   Hi " + name.title() +
              ", I see your favorite language is " +
              favorite_languages[name].title() + "!")
if 'erin' not in favorite_languages.keys():
    print("Erin, please take our poll !")
# Jen
# Sarah
#    Hi Sarah, I see your favorite language is C!
# Edward
# Phil
#    Hi Phil, I see your favorite language is C++!
# Erin, please take our poll !
```

- 遍历字典时，会默认遍历所有的键，因此，如果将上述代码中的for name in favorite_languages.keys(): 替换为 for name in favorite languages:，输出将不变。
- 如果显式地使用方法keys()可让代码更容易理解，你可以选择这样做，但如果你愿意，也可省略它。

#### 【按顺序】遍历字典中的所有键

- 字典总是明确地记录键和值之间的关联关系，但获取字典的元素时，获取顺序是不可预测的。这不是问题，因为通常你想要的只是获取与键相关联的正确的值。要以特定的顺序返回元素，一种办法是在for循环中对返回的键进行排序。为此，可使用函数sorted()来获得按特定顺序排列的键列表的副本:

```python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'c++'
}
for name in sorted(favorite_languages.keys()):
    print(name.title()+ "，thank you for taking the poll.")
# Edward，thank you for taking the poll.
# Jen，thank you for taking the poll.
# Phil，thank you for taking the poll.
# Sarah，thank you for taking the poll.
```

#### 遍历字典中的所有值

```python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'c++'
}
print("The following languages have been mentioned:")
for language in favorite_languages.values():
    print('\t'+language.title())
# The following languages have been mentioned:
# 	Python
# 	C
# 	Ruby
# 	C++
```

- 这种做法提取字典中所有的值，而没有考虑是否重复。涉及的值很少时，这也许不是问题，但如果被调查者很多，最终的列表可能包含大量的重复项。为剔除重复项，可使用集合( set)。集合类似于列表，但每个元素都必须是独一无二的:

```python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c++',
    'edward': 'ruby',
    'phil': 'c++'
}
print("The following languages have been mentioned:")
for language in set(favorite_languages.values()):
    print('\t'+language.title())
# The following languages have been mentioned:
# 	Python
# 	C++
# 	Ruby
```

### 内置函数

- `len(dict)`：返回字典的项数
- `key in dict`：判断键是否在字典中
- `dict.pop()`：如果键存在且在字典中，移除该键，**返回该键对应的值**
  - 也就是删除并使用，比get多了一个删除
- `dict.popitem()`：移除字典的末尾键值对并**返回该键值对**

```python
mail_list = {'tom': 'tom@gmail.com', 'jerry': 'jerry@foxmail.com', 'john': 'john@163.com'}
print(len(mail_list))           # 3
print('tom' in mail_list)       # True
print(mail_list.get('john'))    # john@163.com
print(mail_list.pop('john'))    # john@163.com
print(mail_list.popitem())      # ('jerry', 'jerry@foxmail.com')
```

### 高级用法

#### 嵌套

##### 列表&字典

```python
{
    'red':[255,0,0],
    'green':[0,255,0],
    'blue':[0,0,255]
}

[
    { 'color':'red', 'value':[255,0,0] },
    { 'color':'green', 'value':[0,255,0] },
    { 'color':'blue', 'value':[0,0,255] }
]
```



```python
alien_0 = {'color':'green','point':5}
alien_1 = {'color':'yellow','point':10}
alien_2 = {'color':'red','point':15}
aliens = [alien_0,alien_1,alien_2]
for alien in aliens:
    print(alien)
# {'color': 'green', 'point': 5}
# {'color': 'yellow', 'point': 10}
# {'color': 'red', 'point': 15}
```

```python
aliens = []
score = 1
for alien_number in range(30):
    if score % 3 != 0:
        new_alien = {'color':'green','points': score,'speed':'slow'}
    else:
        new_alien = {'color': 'yellow', 'points': score, 'speed': 'slow'}
    aliens.append(new_alien)
    score = score + 1

for alien in aliens[0:9]:
    if alien['color'] == 'green':
        alien['color'] = 'yellow'
        alien['speed'] = 'medium'
        alien['points'] = 10
    elif alien['color'] =='yellow':
        alien['color'] = 'red'
        alien['speed'] = 'fast'
        alien['points'] = 15
#显示前5个外星人
for alien in aliens[:9]:
    print(alien)
print("...")
#显示创建了多少个外星人
print("Total number of aliens: "+str(len(aliens)))

# {'color': 'yellow', 'points': 10, 'speed': 'medium'}
# {'color': 'yellow', 'points': 10, 'speed': 'medium'}
# {'color': 'red', 'points': 15, 'speed': 'fast'}
# {'color': 'yellow', 'points': 10, 'speed': 'medium'}
# {'color': 'yellow', 'points': 10, 'speed': 'medium'}
# {'color': 'red', 'points': 15, 'speed': 'fast'}
# {'color': 'yellow', 'points': 10, 'speed': 'medium'}
# {'color': 'yellow', 'points': 10, 'speed': 'medium'}
# {'color': 'red', 'points': 15, 'speed': 'fast'}
# ...
# Total number of aliens: 30
```

##### 在字典中存储列表

- 每当需要在字典中将一个键关联到多个值时，都可以在字典汇中嵌套一个列表。

```python
pizza = {
    'crust': 'thick',
    'toppings': ['mushrooms', 'extra cheese'], # 在字典中存储列表
}

print("You ordered a "+ pizza['crust'] +"-crust pizza"+ "with the following toppings:")

for topping in pizza['toppings']:
    print("\t" + topping)

# You ordered a thick-crust pizzawith the following toppings:
# 	mushrooms
# 	extra cheese
```

```python
favorite_languages = {
    'jen': ['python','ruby'],
    'sarah':['c'],
    'edward': ['ruby','go'],
    'phil':['python','haskell'],
}
for name, languages in favorite_languages.items():
# 这里name自动对应键，languages自动对应值
    print("\n"+name.title()+"'s favorite languages are: ")
    for language in languages:
        print("\t"+language.title())
# Jen's favorite languages are: 
# 	Python
# 	Ruby
# 
# Sarah's favorite languages are: 
# 	C
# 
# Edward's favorite languages are: 
# 	Ruby
# 	Go
# 
# Phil's favorite languages are: 
# 	Python
# 	Haskell
```

###### 【理解这个案例】按格式输出

```python
keys= ['id', 'name', 'pwd']
values = [[2, 3],['123', '456'],['djks1321','48hbdsk']]
b = dict(zip(keys,values))
# print(b)
# print(len(b.get('id'))) # 获取[2,3]中元素个数
print("id |  name |  pwd ")
for i in range(len(b.get('id'))):
    print(b['id'][i], " | ", b['name'][i], " | ", b['pwd'][i])

# id |  name |  pwd 
# 2  |  123  |  djks1321
# 3  |  456  |  48hbdsk
```

##### 在字典中存储字典

```PYTHON
users = {
    'aeinstein':{
        'first':'albert',
        'last':'einstein',
        'location':'princeton',
    },
    'mcurie':{
        'first': 'marie',
        'last': 'curie',
        'location': 'paris',
    },
}
for username, user_info in users.items():
    print("\nUsername: "+ username)
    full_name = user_info['first']+" " +user_info['last']
    location = user_info['location']
    print("\tFull name: "+full_name.title())
    print("\tLocation: "+location.title())
# Username: aeinstein
# 	Full name: Albert Einstein
# 	Location: Princeton
# 
# Username: mcurie
# 	Full name: Marie Curie
# 	Location: Paris
```

#### zip()

- 利用zip()函数合并两个列表为字典
  `字典= dict(zip(列表1,例表2))`

```python
keys = ['a', 'b', 'c']
values = [1, 2, 3]
dictionary = dict(zip(keys, values))
print(dictionary) # {'a': 1, 'b': 2, 'c': 3}
```

```python
keys= ['id', 'name', 'pwd']
values = [[2, 3],['123', '456'],['djks1321','48hbdsk']]
b = dict(zip(keys,values))
# print(b)
# print(len(b.get('id'))) # 获取[2,3]中元素个数
print("id |  name |  pwd ")
for i in range(len(b.get('id'))):
    print(b['id'][i], " | ", b['name'][i], " | ", b['pwd'][i])

# id |  name |  pwd 
# 2  |  123  |  djks1321
# 3  |  456  |  48hbdsk
```



#### dict.setdefault()

- Python 字典 `setdefault() `函数和 `get()`方法类似，如果键不存在于字典中，将会添加键并将值设为默认值。

- `dict.setdefault(key[, default])`

  如果字典存在键key，返回它对应的值

  如果不存在，插入default的键key，并返回default

```python
mail_list = {'tom': 'tom@gmail.com', 'jerry': 'jerry@foxmail.com', 'john': 'john@163.com'}
tom_mail = mail_list.setdefault('tom','tom@163.com')
print(tom_mail)  # tom@gmail.com
print(mail_list) # {'tom': 'tom@gmail.com', 'jerry': 'jerry@foxmail.com', 'john': 'john@163.com'}
#可以看到，虽然你想要设置tom的邮箱为tom@163.com，但是setdefault方法不让你设置，他会告诉你说，tom已经存在了，并且有值，将值返回给你。这样更加安全。

keli_mail = mail_list.setdefault('keli','keli@163.com')
print(keli_mail) # keli@163.com
print(mail_list) # {'tom': 'tom@gmail.com', 'jerry': 'jerry@foxmail.com', 'john': 'john@163.com', 'keli': 'keli@163.com'}
# 如果插入的是不存在的键，那就可以插入，并且把值返回给你
```





## 7. 流程控制语句

### if语句

```python
if 判断条件：
    执行语句……
else：
    执行语句……
```

```python
cars = ['audi','bmw','subaru','toyota']

for car in cars:
    if car == 'bmw':
        print(car.upper())
    else:
        print(car.title())
# Audi
# BMW
# Subaru
# Toyota
```





#### 条件测试

##### “不区分大小写”

```python
>>> car = 'Audi'
>>> car.lower() == 'audi'
True
>>> car
'Audi'
```

​	网站采用类似的方式让用户输入的数据符合特定的格式。例如，网站可能使用类似的测试来确保用户名是独一无二的，而并非只是与另一个用户名的大小写不同。用户提交新的用户名时，将把它转换为小写，并与所有既有用户名的小写版本进行比较。执行这种检查时，如果已经有用户名'john' (不管大小写如何)，则用户提交用户名'John'时将遭到拒绝。

##### 检查是否不相等

```python
requested_topping = 'mushrooms'
if requested_topping != 'anchovies':
    print("Hold the anchovies!")
# Hold the anchovies!
```

##### and = &&

##### or = ||

```python
age_0 = 22
age_1 = 18
age_0 >= 21 or age_1>=21 # True
age_0 >= 21 and age_1 >=21 # False
```

##### in  、not in

```python
locations = ['上海','南京','苏州']
if '北京' in locations:
    print("去过北京了")
else:
    print("下次去北京")
# 下次去北京
```

```python
banned_users = ['andrew','carolina','david']
user = 'marie'
if user not in banned_users:
    print(user.title()+", you can post a response if you wish")
# Marie, you can post a response if you wish
```

#### if-elif-else

- else是一条包罗万象的语句，只要不满足任何if或elif中的条件测试，其中的代码就会执行，这**可能会引入无效甚至恶意的数据**。如果知道最终要测试的条件，应考虑使用一个elif代码块来代替else代码块。这样，你就可以肯定，仅当满足相应的条件时，你的代码才会执行。
- ——如果确定条件的所有范围，直接明确会比包含某些特殊情况要好——**能用elif确定范围就不要用else**

```python
age = 12
if age < 4:
    price = 0 
elif age <18:
    price = 5
elif age <65:
    price = 10
elif age >=65:
    price = 5
print("Your admission cost is $"+str(price)+".")
```

#### 使用if语句处理列表

##### 检查特殊元素

```python
requested_toppings = ['mushrooms', 'green peppers', ' extra cheese' ]
for requested_topping in requested_toppings:
    if requested_topping == 'green peppers':
        print("Sorry, we are out of green peppers right now.")
    else:
        print("Adding "+ requested_topping +".")
print("\nFinished making your pizza!")
# Adding mushrooms.
# Sorry, we are out of green peppers right now.
# Adding  extra cheese.
# 
# Finished making your pizza!
```

```python
requested_toppings = []
if requested_toppings:
    for requested_topping in requested_toppings:
        print("Adding "+ requested_topping +".")
    print("\nFinshed making your pizza!")
else:
    print("Are you sure you want a plain pizza?")
# Are you sure you want a plain pizza?
```

##### 使用多个列表

```python
available_toppings = ['mushrooms', 'olives', 'green peppers',
                      'pepperoni', 'pineapple', 'extra cheese']
requested_toppings = ['mushrooms', 'french fries', 'extra cheese']
for requested_topping in requested_toppings:
    if requested_topping in available_toppings:
        print("Adding " + requested_topping + ".")
    else:
        print("Sorry, we don't have " + requested_topping + ".")
print("\nFinished making your pizza!")
# Adding mushrooms.
# Sorry, we don't have french fries.
# Adding extra cheese.
# 
# Finished making your pizza!
```





### while循环

```python
while 判断条件(condition)：
    执行语句(statements)……

```

```python
count = 0
while (count < 3):
   print ('The count is:', count)
   count = count + 1
 
print ("Good bye!")
# The count is: 0
# The count is: 1
# The count is: 2
# Good bye!
```

```python
# continue 和 break 用法
 
i = 1
while i < 10:   
    i += 1
    if i%2 > 0:     # 非双数时跳过输出
        continue
    print (i)         # 输出双数2、4、6、8、10
 
i = 1
while 1:            # 循环条件为1必定成立
    print (i)         # 输出1~5
    i += 1
    if i > 5:     # 当i大于10时跳出循环
        break
```



```python
>>> # Fibonacci series:
... # the sum of two elements defines the next
... a, b = 0, 1
>>> while a < 10:
...     print(a)
...     a, b = b, a+b
...
0
1
1
2
3
5
8
```

#### 循环的退出方法

- 循环结束，正常退出
- 执行出错，异常退出
- 使用标志退出
- 使用break、 continue 语句退出
- 条件不满足，不执行循环
- 死循环，不退出

##### 让用户选择何时退出

```python
prompt = "\nTell me something, and I will repeat it back to you: "
prompt += "\nEnter 'quit' to end the program."
message = ""
while message != 'quit':
    message = input(prompt)
    if message != 'quit':
        print(message)
______________________________或者______________________________
prompt = "\nTell me something, and I will repeat it back to you: "
prompt += "\nEnter 'quit' to end the program."
active = True
while active:
    message = input(prompt) # 将要打印的字符放到变量中，这样可以使逻辑更清晰
    if message == 'quit':
        active = False
    else:
        print(message)
# Tell me something, and I will repeat it back to you:
# Enter 'quit' to end the program.hello
# hello
#
# Tell me something, and I will repeat it back to you:
# Enter 'quit' to end the program.???
# ???
#
# Tell me something, and I will repeat it back to you:
# Enter 'quit' to end the program.quit
#
# Process finished with exit code 0
```

#### 使用while循环来处理列表和字典

```python
list1= [1,2,3,4,5]
while list1:
    print(list1.pop())
# 5
# 4
# 3
# 2
# 1
```



##### 在列表之间移动元素

```python
# 首先，创建一个待验证用户列表
# 和一个用于存储已验证用户的空列表
unconfirmed_users = ['alice', 'brian', 'candace']
confirmed_users = []
# 验证每个用户，直到没有未验证用户为止
# 将每个经过验证的列表都移到已验证用户列表中
while unconfirmed_users:
    current_user = unconfirmed_users.pop()
    print("Verifying user: " + current_user.title())
    confirmed_users.append(current_user)
# 显示所有已验证用户
print("\nThe following users have been confirmed: ")
for confirmed_user in confirmed_users:
    print(confirmed_user.title())
# Verifying user: Candace
# Verifying user: Brian
# Verifying user: Alice
# 
# The following users have been confirmed: 
# Candace
# Brian
# Alice
```

##### 删除包含特定值的所有列表元素

- 在第3章中，我们使用函数remove()来删除列表中的特定值，这之所以可行，是因为要删除的值在列表中只出现了一次。如果要删除列表中所有包含特定值的元素，该怎么办呢?

```python
pets = ['dog','cat','dog','goldfish','cat','rabbit','cat']
print(pets)
while 'cat' in pets:
    pets.remove('cat')
print(pets)
# ['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
# ['dog', 'dog', 'goldfish', 'rabbit']
```

##### 使用用户输入来填充字典

```python
responses = {}
# 设置一个标志，指出调查是否继续
polling_active = True
while polling_active:
    # 提示输入被调查者的名字和回答
    name = input("\nWhat is your name?")
    response = input("which mountain would you like to climb someday? ")
    # 将答卷存储在字典中
    responses[name] = response
    # 看看是否还有人要参与调查
    repeat = input("Would you like to let another person respond? (yes/ no) ")
    if repeat == 'no':
        polling_active = False
# 调查结束，显示结果.
print("\n--- Poll Results ---")
for name, response in responses.items():
    print(name + " would like to climb " + response + ".")
# What is your name?like
# which mountain would you like to climb someday? ximalaya
# Would you like to let another person respond? (yes/ no) yes
# 
# What is your name?wang
# which mountain would you like to climb someday? qinling
# Would you like to let another person respond? (yes/ no) no
# 
# --- Poll Results ---
# like would like to climb ximalaya.
# wang would like to climb qinling.
```

### for循环

​	Python 的 `for` 语句与 C 或 Pascal 中的不同。Python 的 `for` 语句不迭代算术递增数值（如 Pascal），或是给予用户定义迭代步骤和暂停条件的能力（如 C），而是**迭代列表或字符串等任意序列**，元素的迭代顺序与在序列中出现的顺序一致。 

```python
# Measure some strings:
words = ['cat', 'window', 'defenestrate']
for w in words:
    print(w, len(w))

# cat 3
# window 6
# defenestrate 12
```

遍历集合时修改集合的内容，会很容易生成错误的结果。因此不能直接进行循环，而是**应遍历该集合的副本**或**创建新的集合**：

```python
# Create a sample collection
users = {'Hans': 'active', 'Éléonore': 'inactive', '景太郎': 'active'}

# Strategy:  Iterate over a copy
for user, status in users.copy().items():
    if status == 'inactive':
        del users[user]

# Strategy:  Create a new collection
active_users = {}
for user, status in users.items():
    if status == 'active':
        active_users[user] = status
```

#### else子句

循环语句支持 `else` 子句；[`for`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#for) 循环中，可迭代对象中的元素全部循环完毕，或 [`while`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#while) 循环的条件为假时，执行该子句；[`break`](https://docs.python.org/zh-cn/3.10/reference/simple_stmts.html#break) 语句终止循环时，不执行该子句。 请看下面这个查找素数的循环示例：

```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(n, 'equals', x, '*', n//x)
            break
    else:
        # loop fell through without finding a factor
        print(n, 'is a prime number')
# 2 is a prime number
# 3 is a prime number
# 4 equals 2 * 2
# 5 is a prime number
# 6 equals 2 * 3
# 7 is a prime number
# 8 equals 2 * 4
# 9 equals 3 * 3
```

（没错，这段代码就是这么写。仔细看：`else` 子句属于 [`for`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#for) 循环，**不属于** [`if`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#if) 语句。）

```python
movie1 = { "name":"Friends", "language":"En", "Sessions":10, "Other name":"Six of One" }
for title in movie1.keys():
    print(title.title())
    # Name
    # Language
    # Sessions
    # Other Name
for value in movie1.values():
    print(value)
    # Friends
    # En
    # 10
    # Six of One
for i in enumerate(movie1.items()):
    print(i)
    # (0, ('name', 'Friends'))
    # (1, ('language', 'En'))
    # (2, ('Sessions', 10))
    # (3, ('Other name', 'Six of One'))
```



#### 枚举enumerate()

enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中

```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
list(enumerate(seasons))
# [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
list(enumerate(seasons, start=1)) # 下标从 1 开始
# [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]

```

```python
i = 0
seq = ['one', 'two', 'three']
# 传统for循环的枚举
# for element in seq:
#     print (i, seq[i])
#     i += 1

# enumerate()函数的枚举
for i, element in enumerate(seq):
    print (i, element)

# 0 one
# 1 two
# 2 three
```



### break语句

`break` 语句和 C 中的类似，用于跳出最近的 `for` 或 `while` 循环。

循环语句支持 `else` 子句；`for` 循环中，可迭代对象中的元素全部循环完毕，或 `while` 循环的条件为假时，执行该子句；`break` 语句终止循环时，不执行该子句。 请看下面这个查找素数的循环示例：

```python
>>> for n in range(2, 10):
...     for x in range(2, n):
...         if n % x == 0:
...             print(n, 'equals', x, '*', n//x)
...             break
...     else:
...         # loop fell through without finding a factor
...         print(n, 'is a prime number')
...
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3
```

（没错，这段代码就是这么写。仔细看：`else` 子句属于 `for` 循环，**不属于** `if` 语句。）

与 `if` 语句相比，循环的 `else` 子句更像 `try` 的 `else` 子句： `try` 的 `else` 子句在未触发异常时执行，循环的 `else` 子句则在未运行 `break` 时执行。

```python
prompt = "\nPlease enter the name of a city you have visited: "
prompt += "\n(Enter 'quit' when you are finished.)"
while True:
    city = input(prompt)
    if city == 'quit':
        break
    else:
        print("I'd love to go to " + city.title() +"!")
# Please enter the name of a city you have visited: 
# (Enter 'quit' when you are finished.)new york
# I'd love to go to New York!
# 
# Please enter the name of a city you have visited: 
# (Enter 'quit' when you are finished.)san francisco
# I'd love to go to San Francisco!
# 
# Please enter the name of a city you have visited: 
# (Enter 'quit' when you are finished.)quit
# 
# Process finished with exit code 0
```

### continue语句

`continue` 语句也借鉴自 C 语言，表示继续执行循环的下一次迭代：

```python
>>> for num in range(2, 10):
...     if num % 2 == 0:
...         print("Found an even number", num)
...         continue
...     print("Found an odd number", num)
...
Found an even number 2
Found an odd number 3
Found an even number 4
Found an odd number 5
Found an even number 6
Found an odd number 7
Found an even number 8
Found an odd number 9
```

```python
current_number = 0
while current_number < 10:
    current_number += 1
    if current_number % 2 == 0:
        continue
    print(current_number)
# 1
# 3
# 5
# 7
# 9
```

### pass语句

> C语言中，可以定义一个空函数而不会报错，但python中定义一个没有任何操作的函数，需要使用pass语句

`pass` 语句不执行任何操作。语法上需要一个语句，但程序不实际执行任何动作时，可以使用该语句。例如：

```python
>>> while True:
...     pass  # Busy-wait for keyboard interrupt (Ctrl+C)
...
```

下面这段代码创建了一个最小的类：

```python
>>> class MyEmptyClass:
...     pass
...
```

`pass` 还可以用作函数或条件子句的占位符，让开发者聚焦更抽象的层次。此时，程序直接忽略 `pass`：

```python
>>> def initlog(*args):
...     pass   # Remember to implement this!
...
```







### match语句

> match语句需要Python 3.10及以上版本支持
>
> match语句更擅长字面值比较，if语句更擅长数值比较

match语句接受一个表达式，并将其值与作为一个或多个case块给出的连续模式进行比较。这表面上类似于C、Java或JavaScript(以及许多其他语言)中的**switch语句**，但它更类似于Rust或Haskell等语言中的模式匹配。只有第一个匹配的模式被执行，它还可以从值中提取组件(序列元素或对象属性)到变量中。

最简单的形式是将一个目标值与一个或多个字面值进行比较：

```python
def http_error(status):
    match status:
        case 400:
            return "Bad request"
        case 404:
            return "Not found"
        case 418:
            return "I'm a teapot"
        case _:
            return "Something's wrong with the internet"
```

注意最后一个代码块：“变量名” `_` 被作为 *通配符* 并必定会匹配成功。 如果没有 case 语句匹配成功，则不会执行任何分支。

使用 `|` （“ or ”）在一个模式中可以组合多个字面值：

```python
case 401 | 403 | 404:
    return "Not allowed"
```

模式的形式类似解包赋值，并可被用于绑定变量：

```python
# point is an (x, y) tuple
match point:
    case (0, 0):
        print("Origin")
    case (0, y):
        print(f"Y={y}")
    case (x, 0):
        print(f"X={x}")
    case (x, y):
        print(f"X={x}, Y={y}")
    case _:
        raise ValueError("Not a point")
```

请仔细研究此代码！ 第一个模式有两个字面值，可以看作是上面所示字面值模式的扩展。但接下来的两个模式结合了一个字面值和一个变量，而变量 **绑定** 了一个来自目标的值（`point`）。第四个模式捕获了两个值，这使得它在概念上类似于解包赋值 `(x, y) = point`。

如果使用类实现数据结构，可在类名后加一个类似于构造器的参数列表，这样做可以把属性放到变量里：

```python
class Point:
    x: int
    y: int

def where_is(point):
    match point:
        case Point(x=0, y=0):
            print("Origin")
        case Point(x=0, y=y):
            print(f"Y={y}")
        case Point(x=x, y=0):
            print(f"X={x}")
        case Point():
            print("Somewhere else")
        case _:
            print("Not a point")
```

可在 dataclass 等支持属性排序的内置类中使用位置参数。还可在类中设置 `__match_args__` 特殊属性为模式的属性定义指定位置。如果它被设为 ("x", "y")，则以下模式均为等价的，并且都把 `y` 属性绑定到 `var` 变量：

```python
Point(1, var)
Point(1, y=var)
Point(x=1, y=var)
Point(y=var, x=1)
```

读取模式的推荐方式是将它们看做是你会在赋值操作左侧放置的内容的扩展形式，以便理解各个变量将会被设置的值。 只有单独的名称（例如上面的 `var`）会被 match 语句所赋值。 带点号的名称 (例如 `foo.bar`)、属性名称（例如上面的 `x=` 和 `y=`）或类名称（通过其后的 "(...)" 来识别，例如上面的 `Point`）都绝不会被赋值。

模式可以任意地嵌套。例如，如果有一个由点组成的短列表，则可使用如下方式进行匹配：

```python
match points:
    case []:
        print("No points")
    case [Point(0, 0)]:
        print("The origin")
    case [Point(x, y)]:
        print(f"Single point {x}, {y}")
    case [Point(0, y1), Point(0, y2)]:
        print(f"Two on the Y axis at {y1}, {y2}")
    case _:
        print("Something else")
```

为模式添加成为守护项的 `if` 子句。如果守护项的值为假，则 `match` 继续匹配下一个 case 语句块。注意，值的捕获发生在守护项被求值之前：

```python
match point:
    case Point(x, y) if x == y:
        print(f"Y=X at {x}")
    case Point(x, y):
        print(f"Not on the diagonal")
```

match 语句的其他特性：

- 与解包赋值类似，元组和列表模式具有完全相同的含义，并且实际上能匹配任意序列。 但它们不能匹配迭代器或字符串。

- 序列模式支持扩展解包操作：`[x, y, *rest]` 和 `(x, y, *rest)` 的作用类似于解包赋值。 在 `*` 之后的名称也可以为 `_`，因此，`(x, y, *_)` 可以匹配包含至少两个条目的序列，而不必绑定其余的条目。

- 映射模式：`{"bandwidth": b, "latency": l}` 从字典中捕获 `"bandwidth"` 和 `"latency"` 的值。与序列模式不同，额外的键会被忽略。`**rest` 等解包操作也支持。但 `**_` 是冗余的，不允许使用。

- 使用 `as` 关键字可以捕获子模式：

  ```python
  case (Point(x1, y1), Point(x2, y2) as p2): ...
  ```

  将把输入的第二个元素捕获为 `p2` (只要输入是包含两个点的序列)

- 大多数字面值是按相等性比较的，但是单例对象 `True`, `False` 和 `None` 则是按标识号比较的。

- 模式可以使用命名常量。 这些命名常量必须为带点号的名称以防止它们被解读为捕获变量:

  ```python
  from enum import Enum
  class Color(Enum):
      RED = 'red'
      GREEN = 'green'
      BLUE = 'blue'
  
  color = Color(input("Enter your choice of 'red', 'blue' or 'green': "))
  
  match color:
      case Color.RED:
          print("I see red!")
      case Color.GREEN:
          print("Grass is green")
      case Color.BLUE:
          print("I'm feeling the blues :(")
  ```

### range函数

内置函数 `range()` 常用于遍历数字序列，该函数可以生成算术级数：

```python
>>> for i in range(5):
...     print(i)
...
0
1
2
3
4
```

生成的序列不包含给定的终止数值；`range(10)` 生成 10 个值，这是一个长度为 10 的序列，其中的元素索引都是合法的。range 可以不从 0 开始，还可以按指定幅度递增（递增幅度称为 '步进'，支持负数）：

```python
>>> list(range(5, 10))
[5, 6, 7, 8, 9]

>>> list(range(0, 10, 3))
[0, 3, 6, 9]

>>> list(range(-10, -100, -30))
[-10, -40, -70]
```

`range()` 和 `len()` 组合在一起，可以按索引迭代序列：

```python
>>> a = ['Mary', 'had', 'a', 'little', 'lamb']
>>> for i in range(len(a)):
...     print(i, a[i])
...
0 Mary
1 had
2 a
3 little
4 lamb
```

如果只输出 range，会出现意想不到的结果：

```python
>>> range(10)
range(0, 10)
```

`range()` 返回对象的操作和列表很像，但其实这两种对象不是一回事。迭代时，该对象基于所需序列返回连续项，并没有生成真正的列表，从而节省了空间。

这种对象称为可迭代对象 iterable，函数或程序结构可通过该对象获取连续项，直到所有元素全部迭代完毕。`for` 语句就是这样的架构，`sum()` 是一种把可迭代对象作为参数的函数：

```python
>>> sum(range(4))  # 0 + 1 + 2 + 3
6
```

下文将介绍更多返回可迭代对象或把可迭代对象当作参数的函数。 在 数据结构 这一章节中，我们将讨论有关 `list()` 的更多细节。



## 8. 输入输出/文件

> ```python
> while True:
> 	print("按s键保存数据")
> 	print("按|键读取数据")
> 	print("按q键退出程序")
> 	keyboard = input("请输入控制指令")
> 	do something...
> ```
>
> 输入也经常用于循环中，实现暂停循环的功能

### 输入

#### input()

- 函数input()接受一个参数：即**要向用户显示的提示或说明，让用户知道该如何做**。在这个
  示例中，Python运行第1行代码时，用户将看到提示Tell me something, and I will repeat it back to you: 程序等待用户输人，并在用户按回车键后继续运行。输人存储在变量message中，接下来的print(message)将输人呈现给用户:

```python
message = input("Tell me something, and I will repeat it back to you: ")
print(message)
# Tell me something, and I will repeat it back to you: Hello World!
# Hello World!
```

```python
prompt  = "If you tell us who you are, we can personalize the messages you see."
prompt += "\nWhat is your first name? "
name = input(prompt)
print("\nHello, "+name+"!")

# If you tell us who you are, we can personalize the messages you see.
# What is your first name? Like
# 
# Hello, Like !
```

##### 使用input()来获取数值输入

```python
height = input("How tall are you, in meters? ")
height = float(height)  # input函数直接输入得到的是字符串，做比较时得转换成数值
print(height)
if height >= 1.2:
    print("\nYou're tall enough to ride!" )
else:
    print("\nYou'll be able to ride when yor're a little older")
```

##### 求模

```python
number = input("Enter a number, and I'll tell you if it's even or odd: ")
number = int(number)  # input函数直接输入得到的是字符串，做数值计算时得转换成数值

if number % 2 == 0:
    print("\nThe number " + str(number) + " is even.")
else:
    print("\nThe number " + str(number) + " is odd.")
# Enter a number, and I'll tell you if it's even or odd: 52
# 
# The number 52 is even.
```

#### 命令行参数

编写命令行参数的一般逻辑

```python
import argparse
parser = argparse.ArgumentParser(description="这个程序的用途")
parser.add_argument("要添加的参数和参数描述")
args = parser.parse_args()
```

- `args`用于接收参数并进行处理
- 执行方式`python name.py 参数`

```python
import argparse
# 执行方式  python3 ./38-1.py -number 100
parser = argparse.ArgumentParser(description="这个程序用来演示参数处理")
# -number 表示 number 参数是可选参数
parser.add_argument( "-number", help="输入一个数字")
args = parser.parse_args()
print(f"你输入的number参数是 {args.number} ")


# python 38-1.py -number 210
# 你输入的number参数是 210 

# python ./38-1.py -h
# usage: 38-1.py [-h] [-number NUMBER]
# 
# 这个程序用来演示参数处理
# 
# options:
#   -h, --help      show this help message and exit
#   -number NUMBER  输入一个数字
```

##### 强制转换参数类型和设置默认值

```python
parser.add_argument( "-number1", type=int, default=10 )
```

```python
import argparse
# 执行方式  python3 38-1.py -number 100
parser = argparse.ArgumentParser(description="这个程序用来演示参数处理")
# -number 表示 number 参数是可选参数
parser.add_argument( "-number1", type=int,  default=10, help="输入一个数字")
parser.add_argument( "-number2", type=int,  default=20, help="输入一个数字")
args = parser.parse_args()
print(f"你输入的两数之和是 {args.number1+args.number2} ")

# python3 38-2.py -number1 30 -number2 20
# 你输入的两数之和是 50 
```



### 输出

#### 三种输出格式

1. 百分号%：用于定义格式和精度

   ```python
   # %常用格式:
   # %s格式化字符串
   # %d格式化整数
   # %f浮点数
   "%-5.3d" %(123.456)
   '123  '# 3后面有两个占位符
   ```

   ```python
   "%s is %s than %s" %("Beautiful", "better", "ugly")
   ```

2. format()函数

   ```python
   "{1} is {2} than {0}".format( "udhy", "Beautiful", "better")
   "{B} is {b} than {u}".format(u = "ugly", B = "Beautiful", b = "better")
   # 'Beautiful is better than ugly'
   ```

3. **f-strings**

   ```python
   u= "ugly"; B = "Beautiful"; b = "better"
   f"{B} is {b} than{u}"
   ```

   

#### print()

- `print()` 函数输出给定参数的值。与表达式不同（比如，之前计算器的例子），它能处理多个参数，包括浮点数与字符串。它输出的字符串不带引号，且各参数项之间会插入一个空格，这样可以实现更好的格式化操作：

  ```python
  i = 256*256
  print('The value of i is', i)
  # The value of i is 65536
  ```

- `print()`默认会在末尾回车，也可以使用end来自定义

  ```python
  a, b = 0, 1
  while a < 100:
       print(a, end=', ')
       a,b = b, a+b
  # 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 
  ```


#### f-strings

- 通过定义好的格式进行输出

- F-strings是Python3.6新增的字符串格式化功能

- 比百分号和str.format()更友好

- 采用了早期为字符串添加关键字方式，如"u"、"r"、 "b"

- 计算功能

  - F-strings的`{}`中可以实现数字计算、字符串连接、函数执行等计算任务

  - 嵌入的内容可解释执行

    ```python
    f"{1+2}"        # 3 
    f"{'a'+'b'}"    # ab
    f"{print('c')}" # c
    ```

  - 宽度和精度调整格式：

    ```python
    f"{对象:宽度.精度类型}"
    ```

    ```python
    number = 123.456
    f"{number:20}"
    # '             123.456'
    
    f"{number:010}"
    # '000123.456'
    
    f"{number:4f}" # 指定类型后，默认保存小数点后6位
    # '123.456000'
    
    f"{number:.2f}"
    # '123.46'
    ```

### 文件

#### 打开文件open()

- 打开文件是文件的第一步操作
- Python使用open()函数实现了文件打开
- `open()` 返回一个 file object ，最常使用的是两个位置参数和一个关键字参数：`open(filename, mode, encoding=None)`

```python
f = open('workfile', 'w', encoding="utf-8")
```

- 第一个实参是文件名字符串

- 第二个实参是包含**描述文件使用方式**字符的字符串。*mode* 的值包括 `'r'` ，表示文件只能读取；`'w'` 表示只能写入（现有同名文件会被覆盖）；`'a'` 表示打开文件并追加内容，任何写入的数据会自动添加到文件末尾。`'r+'` 表示打开文件进行读写。*mode* 实参是可选的，省略时的默认值为 `'r'`。

- 通常情况下，文件是以 *text mode* 打开的，也就是说，你从文件中读写字符串，这些字符串是以特定的 *encoding* 编码的。如果没有指定 *encoding* ，默认的是与平台有关的。因为 UTF-8 是现代事实上的标准，除非你知道你需要使用一个不同的编码，否则建议使用 `encoding="utf-8"` 。

- 在处理文件对象时，最好使用 [`with`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#with) 关键字。优点是，子句体结束后，文件会正确关闭，即便触发异常也可以。而且，使用 `with` 相比等效的 [`try`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#try)-[`finally`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#finally) 代码块要简短得多：

  ```python
  with open('workfile', encoding="utf-8") as f:
      read_data = f.read()
  
  # We can check that the file has been automatically closed.
  f.closed
  ```

  如果没有使用 [`with`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#with) 关键字，则应调用 `f.close()` 关闭文件，即可释放文件占用的系统资源。

  > 调用 `f.write()` 时，未使用 `with` 关键字，或未调用 `f.close()`，即使程序正常退出，也**可能** 导致 `f.write()` 的参数没有完全写入磁盘。

  通过 [`with`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#with) 语句，或调用 `f.close()` 关闭文件对象后，再次使用该文件对象将会失败。

  ```python
  f.close()
  f.read()
  # Traceback (most recent call last):
  #   File "<stdin>", line 1, in <module>
  # ValueError: I/O operation on closed file.
  ```

#### 文件编码

- 计算机普及之后，各个国家有不同的标准，比如中国制定的GBK编码，一直被Windows沿用

- 为了避免编码混乱，后续产生了统一的Unicode 编码

- 其中最广泛使用的UTF-8就是Unicode的一种实现方式

- Windows默认使用GBK编码

- Linux和macOS使用UTF-8编码

  



#### 文件对象的方法

##### 文件路径处理

```python
file_handler = open("tmp/afile")
# 改变路径
import os
os.chdir("/tmp")
file_handler = open("afile")
```

##### 读取文件

读取文件内容，可以采用多个函数或语句实现:

- ```python
  >>> cat test.txt
  111
  222
  333
  
  aaa
  bbb
  ccc
  ```

- `read([size])`返回指定size大小的内容，如果不指定size,将返回整个文件

  ```python
  f = open('./test.txt', mode='r', encoding='UTF-8')
  data = f.read() # 直接原样读取全部数据
  print(data)
  # 111
  # 222
  # 333
  
  # aaa
  # bbb
  # ccc
  ```

- `readline()`返回一行数据

  ```python
  f = open('./test.txt', mode='r', encoding='UTF-8')
  data = f.readline() # 读取一行数据
  print(data)
  # 111
  ```

- `readlines([size])`返回指定size 行数，如果不指定size，将返回全部文件；也可以用`list(f)`

  ```python
  f = open('./test.txt', mode='r', encoding='UTF-8')
  data = f.readlines() # 读取所有数据，放在列表里
  # data = list(f) # 效果同f.readlines()
  print(data)
  # ['111\n', '222\n', '333\n', '\n', 'aaa\n', 'bbb\n', 'ccc']
  ```

- 【更常用】`for line in file` 从文件中**读取多行时，可以用循环遍历整个文件对象**。这种操作能高效利用内存，快速，且代码简单：

  ```python
  f = open('./test.txt', mode = 'r', encoding='UTF-8')
  for data in f:
      print(data)
  f.close()
  # 111
  #
  # 222
  #
  # 333
  #
  #
  #
  # aaa
  #
  # bbb
  #
  # ccc
  # 
  
  f = open('./test.txt', mode = 'r', encoding='UTF-8')
  for data in f:
      print(data, end='')
  f.close()
  # 111
  # 222
  # 333
  
  # aaa
  # bbb
  # ccc
  ```

##### 写入文件

文件写入由`write()`函数实现，写入方式由`open()`函数控制。不同的open()函数打开模式，执行写入时，写入的位置和结果也不同:

- `mode = "r"`，报错: `io.UnsupportedOperation: not writable`
- `mode = "w"`或`mode = "w+"`**覆盖写入内容**，返回写入字符数量
- `mode="a"`或`mode="a+"`在文件结尾**追加写入内容**



#### 关闭文件

- `close()`函数可以告知内核，文件在内存中有更新。如果不及时关闭，一方面写入文件数据很多，**降低性能**；另一方面，写入的**数据可能会丢失**。
- `write()`函数写入后，必须显式`close()`
- `read-`族函数读取后，不必`close()`但建议关闭，避免文件描述符耗尽
- `open()`失败，不必`close()`

#### with语句

- with语句可以使打开和关闭文件保持一致性， 即：

  **使用with语句打开的文件，离开with语句块作用域会自动关闭**

- ```python
  with open(文件) as 文件描述符:
  	文件读写操作
  # with语句块结束，自动关闭文件
  ```

- ```python
  with open('./test.txt', mode='r', encoding='UTF-8') as f:
      data = f.read()
  
  print(f.read())  # ValueError: I/O operation on closed file.
  ```

  





## 9. 函数

### 内置函数

[Python 解释器内置了很多函数和类型，任何时候都能使用](https://docs.python.org/zh-cn/3.10/library/functions.html)

![image-20231117155714974](./Python.assets/image-20231117155714974.png)

### 定义函数

```python
# 含参函数定义
def func([args]):
    对args进行处理
    [return xxx]
# 函数调用
func(variables)
```

- 只要是合法的标识符即可（同变量命名）
- 为了提高可读性，建议函数名由一个或多个有意义的单词组成，单词之间用下划线_分隔，字母全部小写

下列代码创建一个可以输出限定数值内的斐波那契数列函数：

```python
 # write Fibonacci series up to n
def fib(n):   
    '''Print a Fibonacci series up to n.'''
    a, b = 0, 1
    while a < n:
        print(a, end=' ')
        a, b = b, a+b
    print()

# Now call the function we just defined:
fib(2000)
# 0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

定义函数使用关键字 `def`，后跟函数名与括号内的形参列表。函数语句从下一行开始，并且必须缩进。

函数内的第一条语句是字符串时，该字符串就是**文档字符串**（介绍该函数是干嘛的），也称为 *docstring*。利用文档字符串可以自动生成在线文档或打印版文档，还可以让开发者在浏览代码时直接查阅文档；Python 开发者最好养成**在代码中加入文档字符串的好习惯**。

> 可以用help()查看函数的文档，只要把文档字符串紧接着放在函数的声明行的后面，它就可以被help识别了。

#### 形参列表

- 在函数名后面的括号内，多个形参用逗号分隔，可以没有参数
- 参数可以有默认值，**可以用等号=直接指定默认值，有默认值的参数必须排最后**
- 没有默认值的参数，在调用的时候必须指定
- 形参也可以没有，但是括号不能省略
- 调用有默认值的参数要指定名字
- 

#### 返回值

- 返回值可以没有，直接**省略return**这句话
- 返回值可以是一个或多个，用逗号分隔，组合成一个元组
- 返回值还可以是表达式
  

函数定义在当前符号表中把函数名与函数对象关联在一起。解释器把函数名指向的对象作为用户自定义函数。还可以使用其他名称指向同一个函数对象，并访问访该函数：

```python
>>> fib
<function fib at 10042ed0>
>>> f = fib
>>> f(100)
0 1 1 2 3 5 8 13 21 34 55 89
```

`fib` 不返回值，因此，其他语言不把它当作函数，而是当作过程。事实上，没有 [`return`](https://docs.python.org/zh-cn/3.10/reference/simple_stmts.html#return) 语句的函数也返回值，只不过这个值比较是 `None` （是一个内置名称）。一般来说，解释器不会输出单独的返回值 `None` ，如需查看该值，可以使用 [`print()`](https://docs.python.org/zh-cn/3.10/library/functions.html#print)：

```python
>>> fib(0)
>>> print(fib(0))
None
```

编写不直接输出斐波那契数列运算结果，而是返回运算结果列表的函数也非常简单：

```python
def fib2(n):  # return Fibonacci series up to n
    """Return a list containing the Fibonacci series up to n."""
    result = []
    a, b = 0, 1
    while a < n:
        result.append(a)    # see below
        a, b = b, a+b
    return result

f100 = fib2(100)    # call it
f100                # write the result
# [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
```

#### 一个例子

```python
# 函数定义
def myfunc(arg1, arg2, arg3=None):
    ''' 
    This is a example for python documentation.
    这是一个为python函数提供文档的例子。
    arg1: 第一个参数的说明
    arg2: 第二个参数的说明
    arg3: 第三个参数的说明（这个参数有默认值）
    v1, v2, v3: 返回值的说明 
    '''
    v1 = arg1 + arg2
    v2 = arg1 * arg2
    if arg3 is None:
        v3 = arg1 + arg2
    else:
        v3 = arg1 + arg2 + arg3
    return v1, v2, v3
# 函数调用
v1, v2, v3 = myfunc(5, 3, arg3=4)
print(v1, v2, v3)    #8 15 12
 
# 使用arg3的默认值调用函数
v1, v2, v3 = myfunc(5, 3)
print(v1, v2, v3)    #8 15 8
 
# 忽略一个返回值
v1, v2, _ = myfunc(5, 3)
print(v1, v2, v3)    #8 15 8
 
# 看看返回值是元组tuple，在返回的过程中被自动解包
print(type(myfunc(5,3)))    #<class 'tuple'>
```



### 函数的参数

- 函数的参数是参数与外部可变的输入之间交互的通道。
- 函数的参数名称应该满足标识符命名规范，应该有明确的含义，可通过参数名称知道每个参数的含义。
- 在函数定义下面的注释中逐个注明函数（和返回值）的含义，以便用户即使不甚了解函数中的具体内容也能正确无误的使用它。
- **实参：实际参数，从外面传递来的实际的参数**
- **形参：形式参数，在函数内部它形式上的名字**
- 调用函数时，实参按照【顺序位置】与形参绑定，称为**位置参数**（Positional Argument）
- 也可以在调用时，写明实参与形参的对应关系，称作传递**关键字参数**（Keyword Argument），这时候位置信息被忽略了.
  - 关键字实参是传递给函数的名称`键值-对`。你直接在实参中将名称和值关联起来了，因此向函数传递实参时不会混淆(不会得到名为Hamster的harry这样的结果)。关键字实参让你无需考虑函数调用中的实参顺序，还清楚地指出了函数调用中各个值的用途。
- 使用关键字实参时，务必准确地指定函数定义中的形参名。
- 同时传递位置参数与关键字参数，应该**先传递位置参数**，再传递关键字参数!
- 函数定义的时候，可以指定默认值，但带**默认值的参数必须列在参数列表的最后**

```python
# 举一个小栗子，计算纸箱子的体积
def cube_volume(length, width, height = 0.25):
    '''
    计算纸箱子的体积(单位：m)
    length: 长；    width: 宽
    height: 高（默认参数0.25）
    v: 返回值，纸箱的体积，单位m**3
    '''
    if length <= 0:
        print('length must larger than 0!')
        return 0
    if width <= 0:
        print('width must larger than 0!')
        return 0
    if height <= 0:
        print('height must larger than 0!')
        return 0
    v = length*width*height
    print('length = %.2f; width = %.2f; height = %.2f; cube volume = %.2f' % \
          (length, width, height, v))
    return v
 
# 使用位置参数调用
v = cube_volume(1, 2, 3)
# 使用关键字参数调用
v = cube_volume(width = 1, height = 2, length = 3)
# 位置参数和关键字参数混用
v = cube_volume(1, height = 2, width = 3)
 
# 关键字参数在位置参数之前会报错
# v = cube_volume(width = 1, 2, 3) # SyntaxError: positional argument follows keyword argument
```



#### 位置参数

函数调用时，根据函数定义的参数（形参）的 位置 来传递参数。第1个实参赋值给第1个形参，第1个实参赋值给第2个形参 。

```python
def mul(a,b,c):
    print(a*b*c)
    
def welcome(username):
    print('欢迎',username,'光临')    
    
# 调用时，根参数的位置传递参数
mul(1,2,3)
welcome('郭靖')
# 6
# 欢迎 郭靖 光临
```

```python
def describe_pet(animal_type, pet_name):
    "显示宠物的信息"
    print("\nI have a "+animal_type+".")
    print("My "+animal_type+"'s name is "+pet_name.title()+".")

describe_pet('hamster', 'harry')
describe_pet('dog', 'willie')
# I have a hamster.
# My hamster's name is Harry.
# 
# I have a dog.
# My dog's name is Willie.
```

```python
def address_book(name, *telphone, alias_name=None, **custom):
    print(f"name: {name}, tel: {telphone}, aname: {alias_name}, custom:{custom}")

address_book("wilson")
address_book("wilson",1234,4567,5678)
address_book("wilson",1234,4567,5678,home="Guangdong")
address_book("wilson",1234,4567,5678,alias_name='w',aaa="bbb", home="Guangdong")
# name: wilson, tel: (), aname: None, custom:{}
# name: wilson, tel: (1234, 4567, 5678), aname: None, custom:{}
# name: wilson, tel: (1234, 4567, 5678), aname: None, custom:{'home': 'Guangdong'}
# name: wilson, tel: (1234, 4567, 5678), aname: w, custom:{'aaa': 'bbb', 'home': 'Guangdong'}
```



#### 关键字参数

- 不再是按照位置给出参数，而是把参数名字也带进来

`kwarg=value` 形式的 [关键字参数](https://docs.python.org/zh-cn/3.10/glossary.html#term-keyword-argument) 也可以用于调用函数。函数示例如下：

```python
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    print("-- This parrot wouldn't", action, end=' ')
    print("if you put", voltage, "volts through it.")
    print("-- Lovely plumage, the", type)
    print("-- It's", state, "!")
```

该函数接受一个必选参数（`voltage`）和三个可选参数（`state`, `action` 和 `type`）。该函数可用下列方式调用：

```python
parrot(1000)                                          # 1 positional argument
parrot(voltage=1000)                                  # 1 keyword argument
parrot(voltage=1000000, action='VOOOOOM')             # 2 keyword arguments
parrot(action='VOOOOOM', voltage=1000000)             # 2 keyword arguments
parrot('a million', 'bereft of life', 'jump')         # 3 positional arguments
parrot('a thousand', state='pushing up the daisies')  # 1 positional, 1 keyword
# 最后一个输入的输出效果↓
#-- This parrot wouldn't voom if you put a thousand volts through it.
#-- Lovely plumage, the Norwegian Blue
#-- It's pushing up the daisies !
```

以下调用函数的方式都无效：

```python
parrot()                     # required argument missing
parrot(voltage=5.0, 'dead')  # non-keyword argument after a keyword argument
parrot(110, voltage=220)     # duplicate value for the same argument
parrot(actor='John Cleese')  # unknown keyword argument
```

函数调用时，**关键字参数必须跟在位置参数后面**。所有传递的关键字参数都必须匹配一个函数接受的参数（比如，`actor` 不是函数 `parrot` 的有效参数），关键字参数的顺序并不重要。这也包括必选参数，（比如，`parrot(voltage=1000)` 也有效）。不能对同一个参数多次赋值，下面就是一个因此限制而失败的例子：

```python
>>> def function(a):
...     pass
...
>>> function(0, a=0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: function() got multiple values for argument 'a'
```

最后一个形参为 `**name` 形式时，接收一个字典（详见 [映射类型 --- dict](https://docs.python.org/zh-cn/3.10/library/stdtypes.html#typesmapping)），该字典包含与函数中已定义形参对应之外的所有关键字参数。`**name` 形参可以与 `*name` 形参（下一小节介绍）组合使用（`*name` 必须在 `**name` 前面）， `*name` 形参接收一个 [元组](https://docs.python.org/zh-cn/3.10/tutorial/datastructures.html#tut-tuples)，该元组包含形参列表之外的位置参数。例如，可以定义下面这样的函数：

```python
def cheeseshop(kind, *arguments, **keywords):
    print("-- Do you have any", kind, "?")
    print("-- I'm sorry, we're all out of", kind)
    for arg in arguments:
        print(arg)
    print("-" * 40)
    for kw in keywords:
        print(kw, ":", keywords[kw])
```

该函数可以用如下方式调用：

```python
cheeseshop("Limburger", "It's very runny, sir.",
           "It's really very, VERY runny, sir.",
           shopkeeper="Michael Palin",
           client="John Cleese",
           sketch="Cheese Shop Sketch")
```

输出结果如下：

```python
-- Do you have any Limburger ?
-- I'm sorry, we're all out of Limburger
It's very runny, sir.
It's really very, VERY runny, sir.
----------------------------------------
shopkeeper : Michael Palin
client : John Cleese
sketch : Cheese Shop Sketch
```

注意，关键字参数在输出结果中的顺序与调用函数时的顺序一致。

#### 默认值参数

为参数指定默认值。调用函数时，可以使用比定义时更少的参数，例如：

- 使用默认值时，在形参列表中必须先列出没有默认值的形参，再列出有默认值的实参。这让Python依然能够正确地解读位置实参。

```python
def foo3(argv1=100, argv2=200, argv3=300):
    print(argv1)
    print(argv2)
    print(argv3)
    
foo3("one", "two", "three")
# one
# two
# three
foo3("one", "three", "two")
# one
# three
# two
foo3(argv1="one", argv3="three", argv2="two")
# one
# two
# three
foo3("one", argv3="three", argv2="two")
# one
# two
# three

# 上面的例子是说，对于多个参数，如果位置是正确的，不用加argv=，如果是错误的，也行，但得指定哪一个参数，需要用argv=
```

```python
def describe_pet(pet_name, animal_type='dog'):
    """显示宠物的信息"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")


describe_pet(pet_name='willie')
describe_pet('willie') # 这样也行，因此pet_name得放在第一个位置
# I have a dog.
# My dog's name is Willie.
```

```python
def ask_ok(prompt, retries=4, reminder='Please try again!'):
    while True:
        ok = input(prompt)
        if ok in ('y', 'ye', 'yes'):
            return True
        if ok in ('n', 'no', 'nop', 'nope'):
            return False
        retries = retries - 1
        if retries < 0:
            raise ValueError('invalid user response')
        print(reminder)
```

该函数可以用以下方式调用：

- 只给出必选实参：`ask_ok('Do you really want to quit?')`
- 给出一个可选实参：`ask_ok('OK to overwrite the file?', 2)`
- 给出所有实参：`ask_ok('OK to overwrite the file?', 2, 'Come on, only yes or no!')`

本例还使用了关键字 [`in`](https://docs.python.org/zh-cn/3.10/reference/expressions.html#in) ，用于确认序列中是否包含某个值。

默认值在 *定义* 作用域里的函数定义中求值，所以：

```python
i = 5

def f(arg=i):
    print(arg)

i = 6
f()
```

上例输出的是 `5`。

**重要警告：** 默认值只计算一次。默认值为列表、字典或类实例等可变对象时，会产生与该规则不同的结果。例如，下面的函数会累积后续调用时传递的参数：

```python
def f(a, L=[]):
    L.append(a)
    return L

print(f(1))
print(f(2))
print(f(3))
```

输出结果如下：

```python
[1]
[1, 2]
[1, 2, 3]
```

不想在后续调用之间共享默认值时，应以如下方式编写函数：

```python
def f(a, L=None):
    if L is None:
        L = []
    L.append(a)
    return L
```

##### 等效的函数调用

```Python
# 函数定义
def describe_pet(pet_name, animal_type= 'dog' ):
    if animal_type == 'dog':
        print("汪汪！") 
    if animal_type =='hamster':
        print("唧唧！")

# 函数调用    
# 一条名为Willie的小狗
describe_pet('willie')
describe_pet(pet_name= 'willie')
#一只名为Harry的仓鼠
describe_pet('harry','hamster' )
describe_pet(pet_name='harry', animal_type= 'hamster')
describe_pet(animal_type='hamster', pet_name= 'harry')

# 汪汪！
# 汪汪！
# 唧唧！
# 唧唧！
# 唧唧！
```



#### 可变对象

- 如果参数是可变对象（如列表），函数内部对此对象的修改会在函数执行后仍然有效
- 如果默认参数是可变对象，函数内部修改了此对象后，函数默认值也发生了改变!
- 实际函数**传递进去的是地址，函数体不会将地址传递出来**，但地址对应的值发生了变化。

```python
# 对列表的乘方运算
def pow_list(x, p):
    '''
    power of a list
    x: list
    p: power
    not return value
    '''
    for i in range(len(x)):
        x[i] **= p
    
    #这样会输出乘方后的值，但不会改变x列表里的值
    #因为在计算时将x中的值传入了新的参数进行计算
    #for i in x:
    #    i **= p
    #    print(i)
    #print(x)
 
x = [1,2,3,5,7,9,10,12]
pow_list(x,2)
print(x)
# 可见函数内部对列表x中元素的更改，当函数退出之后依然有效
```

利用可变对象的特点，可以制作一种隐藏的**参数记录器**

```python
# 隐藏的参数记录器
def growing_list(x, y=[]):
    y.append(x)
    print(y)
# 重复执行growing_list(‘a’)会发生什么结果？
growing_list(2)         #[2]
growing_list('张三')    #[2, '张三']
growing_list(22333)     #[2, '张三', 22333]
```

#### 参数收集（不定个数的参数）

- 参数收集，指定是可以往函数内传递不定个数的参数，例如有时候传递3个，有时候传递5个，有时候传递10个，等等。
- 传递不定个数的参数，要在定义参数时，加上一个星号“*”（形参为空的tuple）。
- 带星号的参数可以位于参数列表的任意位置（不一定是开头也不一定是结尾），python要求一个函数只能有一个带星参数。

```python
# 不定个数的数字求和
def my_sum(*t):
    # 带星号的输入参数被当作元组处理
    print(t, type(t))
    sum = 0
    for s in t:
        sum += s
    return sum
# 事实上该函数接受了不定个数的输入参数
my_sum(1,2,3,4,2233)
```

- 如果带星参数后面还有别的参数，则它们必须要用关键字参数的方式传递，否则python不知道它们到底是啥，都会给收集到带星参数里。

```python
# 不定个数的数字乘方后求和
def pow_sum(*t, p):
    # 带星号的输入参数被当作元组处理
    print(t, type(t))
    sum = 0
    for s in t:
        sum += s**p
    return sum
# 最后一个参数p，需要指定关键字传递
pow_sum(1,2,3,4,2233,p=2)
# 如果不指定关键字传递呢？会报错
# pow_sum(1,2,3,4,2233,2)
```

解决一个实际问题

```python
# 不定个数的数字加权求和
# 权重随着数字的个数而发生变化
def weighted_sum(x1,x2,*y):
    sum = 0
    n = len(y)
    weight = 1/3/n
    for i in y:
        sum += weight*i
    return sum+1/3*x1+1/3*x2
 
weighted_sum(1,2,3)           # 2.0
weighted_sum(1,2,3,22,44,55)   # 11.333333333333332
weighted_sum(1,2,3,4,5,6)     # 2.5
```

#### **参数收集（收集关键字参数）**

- python除了带一个星号的参数，还支持带两个星号的参数。它的功能是收集关键字参数。
- 一个函数，至多可以带一个一星参数（收集位置参数），加上一个二星参数（收集关键字参数）。
- 二星参数在函数内部以字典的形式存在。
- 二星参数必须在参数列表的末尾，它后面不能再有别的关键字参数和位置参数了。

```python
# 测试一星参数和两星参数
def test_star(a, b, c, *onestar, **twostar):
    print('a = %d; b = %d; c = %d' % (a, b, c))
    print(onestar, type(onestar))
    print(twostar, type(twostar))
 
test_star(1, 2, 3, 4, 5, 6, s1 = 7, s2 = 8, s3 = 9)
# a = 1; b = 2; c = 3
# (4, 5, 6) <class 'tuple'>
# {'s1': 7, 's2': 8, 's3': 9} <class 'dict'>

# 换个顺序呢？
test_star(1, 2, 3, 4, 5, 6, s1 = 7, s2 = 8, s3 = 9, a = 10, b = 11, c = 12)
# TypeError: test_star() got multiple values for argument 'a'
# 报错了，二星参数后面不能再传递关键字参数了（当然位置参数也不行）
```

- **“参数收集”功能，会让带星参数尽量少的收集，把更多参数留给正常的位置参数和关键字参数**

```python
# 如果有默认参数，要注意可能引起的bug
def test_star(a, b, c, p = 5, *onestar, **twostar):
    print('a = %d; b = %d; c = %d; p = %d' % (a, b, c, p))    #a = 1; b = 2; c = 3; p = 4
    print(onestar, type(onestar))            #(5, 6) <class 'tuple'>
    print(twostar, type(twostar))            #{'s1': 7, 's2': 8, 's3': 9} <class 'dict'>
 

test_star(1, 2, 3, 4, 5, 6, s1 = 7, s2 = 8, s3 = 9)
# a = 1; b = 2; c = 3; p = 4
# (5, 6) <class 'tuple'>
# {'s1': 7, 's2': 8, 's3': 9} <class 'dict'>
# 会传递一个p=4进去，而不是设想的，onestar=(4,5,6)
```

#### 逆向参数收集（炸开参数）

- 在参数外部定义好了的列表、元组、字典等，可以在传参的时候被“炸开”，其中的内容被自动分配到参数列表中
- “炸”列表或者元组，需要在前面添加一个星号。
- “炸”字典，需要在前面添加两个星号。

```python
# 炸参数例子
def zha(a,b,c):
    print(a,b,c)
# 炸元组
z = (1,2,3)            #1 2 3
zha(*z)
# 炸列表
z = [4,5,6]            #4 5 6
zha(*z)
# 炸字典
z = {'a':7,'b':8,'c':9}    #7 8 9
zha(**z)
# 炸字典
z = {'c':7,'a':8,'b':9}    #8 9 7
zha(**z)
 
# 如果炸开后参数个数或Key不匹配，会报错
# z = {'c':7,'a':8}
# zha(**z)
# zha() missing 1 required positional argument: 'b'
```

#### 参数的内存管理

- python的参数传递，传递的是参数值而非参数地址。参数值被复制后传递进函数。
- 对于数值类型的参数（整型、浮点、复数等），在函数内改变参数值，函数外面不受影响。
- 对于容器类型的参数（列表、字典、字符串等），在函数内改变了容器里的内容，在函数的外面也可以体现出来。

```python
# 传递数值类型参数
# 在函数内修改，在函数外面不受影响
def mod_para1(a,b):
    print('In mod_para1, before modification: a = %d; b = %d' % (a,b))    #a = 2; b = 8
    a *= 2
    b += 4
    print('In mod_para1, after modification: a = %d; b = %d' % (a,b))    #a = 4; b = 12
a = 2
b = 8
print('Out of mod_para1, before modification: a = %d; b = %d' % (a,b))    #a = 2; b = 8
mod_para1(a,b)
print('Out of mod_para1, after modification: a = %d; b = %d' % (a,b))    #a = 2; b = 8

# Out of mod_para1, before modification: a = 2; b = 8
# In mod_para1, before modification: a = 2; b = 8
# In mod_para1, after modification: a = 4; b = 12
# Out of mod_para1, after modification: a = 2; b = 8
```

- **传递容器类型参数**
- **在函数内修改，在函数外面也能体现，也可以用这种方法向外界传递信息**
- **如果不希望容器类型中的内容被修改，请手动使用`copy.copy()`、`copy.deepcopy()`方法**

```python
# 列表通过函数传参时，被改动了数据
def mod_para2(x):
    print('In mod_para2, before modification: x = ' + str(x))
    for i in range(len(x)):
        x[i] *= 2
    print('In mod_para2, after modification: x = ' + str(x))
x = [i for i in range(10)]
print('Out of mod_para2, before modification: x = ' + str(x))
mod_para2(x)
print('Out of mod_para2, after modification: x = ' + str(x))
import copy
A = [1,2,3]; B = copy.copy(A)
mod_para2(B); print(A,B)
# Out of mod_para2, before modification: x = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
# In mod_para2, before modification: x = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
# In mod_para2, after modification: x = [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
# Out of mod_para2, after modification: x = [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
# In mod_para2, before modification: x = [1, 2, 3]
# In mod_para2, after modification: x = [2, 4, 6]
# [1, 2, 3] [2, 4, 6]
```

#### 函数中变量的作用域

- 创建于函数外部，它是全局（Global）的，它在这个py文件内部的任何地方可见。
- 创建于函数内部，它是局部（Local）的，它只能在函数内部才能访问，在函数外部不可见。
- 全局变量和局部变量重名，函数内会访问到局部变量，函数外访问到全局变量。
- 函数内部能访问全局变量，但不能修改！
- 如果非要在函数内部修改全局变量，需要声明（不推荐这么干！）

```python
gv1 = 1
def test():
    # gv1=2
    print('在函数内部访问全局变量：gv1 = %d' % gv1)    #1
    # gv1=2
test()
print('在函数外部访问全局变量：gv1 = %d' % gv1)    #1
```

- 上面的例子，会在gv1 = 2的前一行，报错，看起来匪夷所思。
- 事实上，这属于python对全局变量的“遮蔽”（hide）操作。在python的函数内部对不存在的变量赋值时，默认会重新定义局部变量。也就是说，在整个函数的内部，gv1都被重新定义了，这一操作会影响整个函数，因此会在它的上一行报错。
- 为了访问被遮蔽的全局变量，需要使用globals()函数，将全局变量以字典的形式输出。（globals()['全局变量名']）——或者可以简单认为出全局变量通过globals()中的字典存储
- 目前得知python3.10以后是不会报错了，但这种操作方法我们一般是不推荐的！

```python
# 访问被遮蔽的全局变量
gv1 = 1
def test():
    # 用globals函数访问被遮蔽的全局变量
    print('在函数内部访问全局变量：gv1 = %d' % globals()['gv1'])
    gv1 = 2 
    print('在函数内部访问修改后的全局变量：gv1 = %d' % gv1)
test()
print('在函数外部访问全局变量：gv1 = %d' % gv1) # 函数内部修改的其实是同名局部变量，全局变量没有被修改。
```

- 正常的做法是，只要有定义全局变量，函数内部的局部变量就不应该和它重名！
- 可以用global语句，在函数内部声明全局变量，经过声明的全局变量在函数内部可以访问和修改。

```python
# 测试全局变量
gv1 = 1
def test():
    global gv1 #全局变量我来撑控
    print('在函数内部访问全局变量：gv1 = %d' % gv1)    #1
    gv1+=1
test()
print('在函数外部访问全局变量：gv1 = %d' % gv1)    #2
```

#### 获取指定范围内的变量

- python提供了多个方法可以让我们访问到每个变量的“名字”和他们持有的“值”
- 变量在内存的某处保存着“名字”-“值”对儿
- **globals()**: 返回全局范围内所有变量组成的字典, globals()[“名字”]
- **locals()**: 返回当前函数范围内的所有变量组成的字典
- vars(object): 获取指定对象范围内的所有变量组成的字典（如果不传入object参数，vars和locals的作用完全相同）
- 如果在全局范围内（在函数外部）调用locals()，则它的行为和globals()一样，也会列出全局范围内所有变量
- 一般来说，上述函数所列出的变量字典，都不应该被修改！但事实上它们可以被修改！！不推荐使用这种方式修改变量。

### 函数的嵌套

- python可以在函数的内部定义函数，多个函数相互嵌套。在其它函数内部的函数称为“**局部函数**”。
- 局部函数是对外隐藏的，只能封闭在定义它的那一个函数的内部使用。
- python的函数也可以作为返回值，如果把局部函数作为返回值，就可以在其它函数中使用了。

**一个栗子（利用局部函数实现多种平均值的切换）**

```python
# 利用局部函数实现多种平均值的切换
def mymean(x, mtype = 'arithmetic'):
    '''计算列表x的平均值,用mtype定义计算哪种平均值,默认为算术平均值(arithmetic mean)    '''
    def arithmetic(x): 
        ''' 算术平均值(arithmetic mean)  '''
        m = sum(x)/len(x);    return m
    def geometric(x): 
        '''几何平均值(geometric mean) '''
        p = 1.;  n = len(x)
        for i in range(n):      p *= x[i]
        m = p ** (1/n);       return m
    def harmonic(x): 
        ''' 调和平均值(harmonic mean) '''
        s = 0.;      n = len(x)
        for i in range(n):        s += 1/x[i]
        m = 1/(s/n);        return m
    if mtype == 'arithmetic':    return arithmetic
    elif mtype == 'geometric':    return geometric
    elif mtype == 'harmonic':     return harmonic
    else:        return arithmetic

x = (1,3,5,7,9)
print(mymean(x))      # <function mymean.<locals>.arithmetic at 0x7f9924282e60>，返回的是一层函数
print(mymean(x)(x))   # 5.0
print(mymean(x,mtype='harmonic')(x))   # 2.7975133214920076
```

- 类似于函数内局部变量遮蔽全局变量，局部函数内的变量也会遮蔽它所在函数的局部变量。
- 因此使用局部函数时，同样要注意变量名的问题，不同层次的函数变量名应该不同。
- 如果要访问上一层函数的局部变量，在局部函数中应该用nonlocal声明（类比于用global声明全局变量）。

```python
# 局部函数内的变量与函数内的局部变量相冲突，这个程序会报错
def test1():
    fv = 1
    def test2():
        # print('局部函数内打印上层函数中的局部变量：%d' % fv) # 会在这里报错
        fv = 2
        print('局部函数内打印上层函数中的局部变量（更改后）：%d' % fv)    #2        
    test2()
    print('上层函数内打印局部变量（更改后）：%d' % fv)    #1        
    return fv
print('上层函数外打印局部变量（更改后）：%d' % test1())    #1
```

**使用nolocal声明的方式可以使用/更改全局变量**

```python
# 局部函数内的变量与函数内的局部变量相冲突，应该改成这样就不报错了
def test1():
    fv = 1
    def test2():
        nonlocal fv # 用nonlocal声明，把fv声明为上一层函数的变量
        print('局部函数内打印上层函数中的局部变量：%d' % fv)    #1
        fv = 2
        print('局部函数内打印上层函数中的局部变量（更改后）：%d' % fv)    #2    
        
    test2()
    print('上层函数内打印局部变量（更改后）：%d' % fv)    #2
    return fv
 
print('上层函数外打印局部变量（更改后）：%d' % test1())    #2
```

### 函数的高级内容

- python中万物皆对象**，函数也是对象**。函数可以赋值给变量，可以作为函数的参数，也可以作为函数的返回值。
- python中以函数作为对象的用法，可以类比于c语言中的函数指针，但比函数指针灵活的多，也更不容易出错。

```python
# 以第三章栗子中mymean函数为例
# 将函数赋值给变量f
f = mymean2('arithmetic')
# 打印出来看看
print(f)
# 测试一下
x = list(range(1,10))
m = f(x)
print(m)
# 也可以像上面的例子一样，连起来写
print(mymean2('geometric')(x))
```

#### 函数作为函数的形参

- 有时候需要定义一个函数，让它内部的大致流程都固定下来，但其中某些部件可以替换：类似于汽车换发动机，电脑换显卡。
- 这种“可替换式”的程序设计方式，在python中可以方便的通过将函数作为形参的方式来实现。

#### 使用函数作为返回值

- 将一个函数对象（可以是局部函数，也可以是别的地方定义的函数）作为返回值，适合“部件替换式”程序设计中，判断使用哪个部件。
- 具体实现方式参见第三章局部变量栗子中的代码

```python
# 以第三章栗子中mymean函数为例
# 编写另一个程序，对列表中的数字进行变换，变成均值为1的另一个列表
# 均值，可以是算术平均值、几何平均值、调和平均值
def mynormalize(x, mtype):
    f = mymean(mtype)
    m = f(x)
    return [i/m for i in x]
 
x = list(range(1,10))
mtype = 'geometric'
print(mymean(mtype)(x))
print(mynormalize(x, mtype))
```

#### 递归

- 在一个函数里面调用它自己，称为递归。
- 递归可以视作一种隐式的循环，不需要循环语句控制也可实现重复执行某段代码。
- 递归在大型复杂程序中非常有用，在数值和非数值算法中都能大显身手！
- 使用递归的时候要注意，当一个函数不断调用自己的时候，必须保证在某个时刻函数的返回值是确定的，即不再调用自己。

```python
# 斐波那契数列（Fibonacci sequence）
# 在现代物理、准晶体结构、化学等领域，斐波纳契数列都有直接的应用
def Fibonacci(n):
    '''    Fibonacci sequence
    f(0)=1, f(1) = 1, f(n) = f(n-1)+f(n-2)    '''
    if n == 0 or n == 1:        return 1
    else:      return Fibonacci(n-1) + Fibonacci(n-2)
# 测试一下，注意n不要设的太大，python的递归效率是比较低的，太大会死机
print(Fibonacci(5))
# 斐波那契数列，前20位
print('Fibonacci sequence:')
for i in range(20):
    print('%d: %d' % (i,Fibonacci(i)))
```

### 局部函数与lambda

- lambda表达式是现代编程语言引入的一种函数实现方式，它可以在一定程度上代替局部函数。
- 对于局部函数，它的名字只在函数内部有意义，在函数外部看不到它的名字。即便使用返回值的形式传出来了，它的名字并没有被同时传出来。
- 从命名的意义上讲，局部函数都是“隐姓埋名”的，出了这个函数就没人知道它的名字。
- lambda表达式就相当于匿名函数。

```python
# 一行中的hello world
greeting = lambda: print('Hello lambda!')
greeting()  # Hello lambda!

# lambda表达式可以放在数组里面，批量运行
L = [lambda x: x**2, lambda x: x**3, lambda x: x**4]
for p in L:
    print(p(3))
# 9
# 27
# 81
```

```python
pairs = [(1, 'one'), (3, 'three'), (2, 'two'), (4, 'four')]
pairs.sort(key=lambda pair: pair[0])    # [(1, 'one'), (2, 'two'), (3, 'three'), (4, 'four')]
pairs.sort(key=lambda pair: pair[1])    # [(4, 'four'), (1, 'one'), (3, 'three'), (2, 'two')]
```



#### 用lambda表达式代替局部函数

```python
# 用lambda表达式代替局部函数
def mymean2(mtype = 'arithmetic'):
    '''    返回计算平均值所用的函数，用mtype定义计算哪种平均值，默认为算术平均值（arithmetic mean）    '''
    # 由于lambda表达式只能写一行，这里用numpy和scipy的现成的函数来实现
    import numpy as np
    import scipy.stats as st
    a = np.array(x)
    if mtype == 'arithmetic': # 算术平均值（arithmetic mean）
        return lambda a: np.mean(a)
    elif mtype == 'geometric':# 几何平均值（geometric mean）
        return lambda a: st.gmean(a)
    elif mtype == 'harmonic': # 调和平均值（harmonic mean）
        return lambda a: st.hmean(a)
    else:        # 默认：算术平均值（arithmetic mean）
        return lambda a: np.mean(a)
 
x = list(range(1,10))
print(x)        # [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(mymean2('arithmetic')(x))    # 5.0
print(mymean2('geometric')(x))     # 4.147166274396913
print(mymean2('harmonic')(x))      # 3.181371861411138
```

#### 常见数学方法的内部函数

```python
# 判断所有元素是否为True，相当于多重的and
help(all)
print(all([3>2,6<9]))                # True
# 任意一个元素是否为True，相当于多重的or
help(any)
print(any([3>2,6<9]))                # True
# 最大值和最小值
help(max)
help(min)
print(max([1,2,5,3]))                # 5
print(min([1,2,5,3]))                # 1
# 四舍五入(到小数点后第n位)
help(round)
print(round(3.1415926,3))            # 3.142
# 所有元素相加 
help(sum)
print(sum([1,2,3]))                  # 6
print(sum([1,2,3],5))                # 11
# 乘幂
help(pow)
print(pow(6,2))                      # 36
print(pow(6,2,5))                    # 1, 6^2 mod 5
# 带余除法
help(divmod)
print(divmod(6,2))                   # (3, 0)
# 绝对值
help(abs)
print(abs(-2.56))                    # 2.56
```











### 不定长参数

#### 特殊参数

默认情况下，参数可以按位置或显式关键字传递给 Python 函数。为了让代码易读、高效，最好限制参数的传递方式，这样，开发者只需查看函数定义，即可确定参数项是仅按位置、按位置或关键字，还是仅按关键字传递。

函数定义如下：

```python
def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):
      -----------    ----------     ----------
        |             |                  |
        |        Positional or keyword   |
        |                                - Keyword only
         -- Positional only
```

`/` 和 `*` 是可选的。这些符号表明形参如何把参数值传递给函数：位置、位置或关键字、关键字。关键字形参也叫作命名形参。

##### 位置或关键字参数

函数定义中未使用 `/` 和 `*` 时，参数可以按位置或关键字传递给函数。

##### 仅位置参数

此处再介绍一些细节，特定形参可以标记为 *仅限位置*。*仅限位置* 时，形参的顺序很重要，且这些形参不能用关键字传递。仅限位置形参应放在 `/` （正斜杠）前。`/` 用于在逻辑上分割仅限位置形参与其它形参。如果函数定义中没有 `/`，则表示没有仅限位置形参。

`/` 后可以是 *位置或关键字* 或 *仅限关键字* 形参。

##### 仅限关键字参数

把形参标记为 *仅限关键字*，表明必须以关键字参数形式传递该形参，应在参数列表中第一个 *仅限关键字* 形参前添加 `*`。

##### 函数示例

请看下面的函数定义示例，注意 `/` 和 `*` 标记：

```python
>>> def standard_arg(arg):
...     print(arg)
...
>>> def pos_only_arg(arg, /):
...     print(arg)
...
>>> def kwd_only_arg(*, arg):
...     print(arg)
...
>>> def combined_example(pos_only, /, standard, *, kwd_only):
...     print(pos_only, standard, kwd_only)
```

第一个函数定义 `standard_arg` 是最常见的形式，对调用方式没有任何限制，可以按位置也可以按关键字传递参数：

```python
>>> standard_arg(2)
2

>>> standard_arg(arg=2)
2
```

第二个函数 `pos_only_arg` 的函数定义中有 `/`，仅限使用位置形参：

```python
>>> pos_only_arg(1)
1

>>> pos_only_arg(arg=1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: pos_only_arg() got some positional-only arguments passed as keyword arguments: 'arg'
```

第三个函数 `kwd_only_args` 的函数定义通过 `*` 表明仅限关键字参数：

```python
>>> kwd_only_arg(3)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: kwd_only_arg() takes 0 positional arguments but 1 was given

>>> kwd_only_arg(arg=3)
3
```

最后一个函数在同一个函数定义中，使用了全部三种调用惯例：

```python
>>> combined_example(1, 2, 3)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: combined_example() takes 2 positional arguments but 3 were given

>>> combined_example(1, 2, kwd_only=3)
1 2 3

>>> combined_example(1, standard=2, kwd_only=3)
1 2 3

>>> combined_example(pos_only=1, standard=2, kwd_only=3)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: combined_example() got some positional-only arguments passed as keyword arguments: 'pos_only'
```

下面的函数定义中，`kwds` 把 `name` 当作键，因此，可能与位置参数 `name` 产生潜在冲突：

```python
def foo(name, **kwds):
    return 'name' in kwds
```

调用该函数不可能返回 `True`，因为关键字 `'name'` 总与第一个形参绑定。例如：

```python
>>> foo(1, **{'name': 2})
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: foo() got multiple values for argument 'name'
>>>
```

加上 `/` （仅限位置参数）后，就可以了。此时，函数定义把 `name` 当作位置参数，`'name'` 也可以作为关键字参数的键：

```python
def foo(name, /, **kwds):
    return 'name' in kwds
>>> foo(1, **{'name': 2})
True
```

换句话说，仅限位置形参的名称可以在 `**kwds` 中使用，而不产生歧义。

##### 小结

以下用例决定哪些形参可以用于函数定义：

```python
def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):
```

说明：

- 使用仅限位置形参，可以让用户无法使用形参名。形参名没有实际意义时，强制调用函数的实参顺序时，或同时接收位置形参和关键字时，这种方式很有用。
- 当形参名有实际意义，且显式名称可以让函数定义更易理解时，阻止用户依赖传递实参的位置时，才使用关键字。
- 对于 API，使用仅限位置形参，可以防止未来修改形参名时造成破坏性的 API 变动。

#### 任意实参列表

调用函数时，使用任意数量的实参是最少见的选项。这些实参包含在元组中（详见 [元组和序列](https://docs.python.org/zh-cn/3.10/tutorial/datastructures.html#tut-tuples) ）。在可变数量的实参之前，可能有若干个普通参数：

```python
def write_multiple_items(file, separator, *args):
    file.write(separator.join(args))
```

*variadic* 参数用于采集传递给函数的所有剩余参数，因此，它们通常在形参列表的末尾。`*args` 形参后的任何形式参数只能是仅限关键字参数，即只能用作关键字参数，不能用作位置参数：

```python
>>> def concat(*args, sep="/"):
...     return sep.join(args)
...
>>> concat("earth", "mars", "venus")
'earth/mars/venus'
>>> concat("earth", "mars", "venus", sep=".")
'earth.mars.venus'
```

#### 解包实参列表

函数调用要求独立的位置参数，但实参在列表或元组里时，要执行相反的操作。例如，内置的 [`range()`](https://docs.python.org/zh-cn/3.10/library/stdtypes.html#range) 函数要求独立的 *start* 和 *stop* 实参。如果这些参数不是独立的，则要在调用函数时，用 `*` 操作符把实参从列表或元组解包出来：

```python
>>> list(range(3, 6))            # normal call with separate arguments
[3, 4, 5]
>>> args = [3, 6]
>>> list(range(*args))            # call with arguments unpacked from a list
[3, 4, 5]
```

同样，字典可以用 `**` 操作符传递关键字参数：

```python
>>> def parrot(voltage, state='a stiff', action='voom'):
...     print("-- This parrot wouldn't", action, end=' ')
...     print("if you put", voltage, "volts through it.", end=' ')
...     print("E's", state, "!")
...
>>> d = {"voltage": "four million", "state": "bleedin' demised", "action": "VOOM"}
>>> parrot(**d)
-- This parrot wouldn't VOOM if you put four million volts through it. E's bleedin' demised !
```

#### 文档字符串

以下是文档字符串内容和格式的约定。

第一行应为对象用途的简短摘要。为保持简洁，不要在这里显式说明对象名或类型，因为可通过其他方式获取这些信息（除非该名称碰巧是描述函数操作的动词）。这一行应以大写字母开头，以句点结尾。

文档字符串为多行时，第二行应为空白行，在视觉上将摘要与其余描述分开。后面的行可包含若干段落，描述对象的调用约定、副作用等。

Python 解析器不会删除 Python 中多行字符串字面值的缩进，因此，文档处理工具应在必要时删除缩进。这项操作遵循以下约定：文档字符串第一行 *之后* 的第一个非空行决定了整个文档字符串的缩进量（第一行通常与字符串开头的引号相邻，其缩进在字符串中并不明显，因此，不能用第一行的缩进），然后，删除字符串中所有行开头处与此缩进“等价”的空白符。不能有比此缩进更少的行，但如果出现了缩进更少的行，应删除这些行的所有前导空白符。转化制表符后（通常为 8 个空格），应测试空白符的等效性。

下面是多行文档字符串的一个例子：

```python
>>> def my_function():
...     """Do nothing, but document it.
...
...     No, really, it doesn't do anything.
...     """
...     pass
...
>>> print(my_function.__doc__)
Do nothing, but document it.

    No, really, it doesn't do anything.
```

#### 函数注解

[函数注解](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#function) 是可选的用户自定义函数类型的元数据完整信息。

[标注](https://docs.python.org/zh-cn/3.10/glossary.html#term-function-annotation) 以字典的形式存放在函数的 `__annotations__` 属性中，并且不会影响函数的任何其他部分。 形参标注的定义方式是在形参名后加冒号，后面跟一个表达式，该表达式会被求值为标注的值。 返回值标注的定义方式是加组合符号 `->`，后面跟一个表达式，该标注位于形参列表和表示 [`def`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#def) 语句结束的冒号之间。 下面的示例有一个必须的参数，一个可选的关键字参数以及返回值都带有相应的标注:

```python
>>> def f(ham: str, eggs: str = 'eggs') -> str:
...     print("Annotations:", f.__annotations__)
...     print("Arguments:", ham, eggs)
...     return ham + ' and ' + eggs
...
>>> f('spam')
Annotations: {'ham': <class 'str'>, 'return': <class 'str'>, 'eggs': <class 'str'>}
Arguments: spam eggs
'spam and eggs'
```

```python
def greet_user(username):
    "显示简单的问候语"
    print("Hello, "+ username.title() +"!")

greet_user('jesse')
# Hello, Jesse!
```

### 类型提示（type hint)

> 类型提示仅能对开发人员起到提示作用，不能用于类型检查

偶尔看到一些代码在定义函数时，在def那一行后面会加一个`->`。有个专门的名词叫 **type hint， 即类型提示**。

```python
def add(a:int, b:int) -> int:
    return a+b
```

意思是：**告诉你期待的输入类型和输出类型**。上面代码期待的类型为int。

其实就是变量类型的动态定义和静态定义的区别。同样一个函数可以**不加->表示动态定义和加->表示静态定义**。

​    对于上面左边函数，对n的数据类型不一定为int，也可以为float等等......而右边限定了只能int，这就是动静态的区别。

我试着寻找这两者的区别和各自优势。有以下发现：

​    1. 将动态类型函数改为静态类型函数**并不能使计算加快**；

​    2. 就算你静态限定了int，输入为float的时候也不会报错，输出也不会变成期待的int类型。所以在使用上，动静态类型并没有区别。

那么这个type hint看起来是比较鸡肋。

它的用处有以下：

​    1. 增加代码可读性；

    2. 比较容易用其他语言改写。

```python
def twoSum(num1: int, num2: int=100) -> int:
    sum = num1 + num2
    return sum
 
if __name__ == "__main__":
    # __annotations__是函数的保留属性，保存的是函数声明中的注释内容，比如我们使用的对参数"num1"，"num2"和返回值的建议类型。
    print(twoSum.__annotations__) # {'num1': <class 'int'>, 'num2': <class 'int'>, 'return': <class 'int'>}

    # 正常用法。
    print(twoSum(3,20))   # 23
    # 注释内容后可以跟等号"=",意思为未传入实参时，该参数获得的默认值
    print(twoSum(1))      # 101

    # 该解释说明符并非强制检查，我们传入了两个str实参，并不会报错，而是继续进行函数中的加法运算。
    print(twoSum('I love ','Arsenal'))  # I love Arsenal
    # 如果传入的两个实参无法进行函数中规定的运算，则会正常报错。
    print(twoSum('Arsenal'))            # TypeError: can only concatenate str (not "int") to str

```

### 返回值

```python
def get_formatted_name(first_name, last_name):
    """返回整洁的姓名"""
    full_name = first_name + ' ' + last_name
    return full_name.title()

musician = get_formatted_name('jimi', 'hendrix')
print(musician)
# Jimi Hendrix
```

```python
def get_formatted_name(first_name, last_name, middle_name=''):	# 注意参数位置
    """返回整洁的姓名"""
    if middle_name:
        full_name = first_name + ' ' + middle_name + ' ' + last_name
    else:
        full_name = first_name + ' ' + last_name
    return full_name.title()

musician = get_formatted_name('jimi', 'hendrix')
print(musician)
musician = get_formatted_name('john', 'hooker ', 'lee')
print(musician) 
# Jimi Hendrix 
# John Lee Hooker 
```

#### 返回字典

```python
def build_person(first_name, last_name):
    """返回一个字典，其中包含有关一个人的信息"""
    person = {'first': first_name, 'last': last_name}
    return person

musician = build_person('jimi', 'hendrix')
print(musician)
# {'first': 'jimi', 'last': 'hendrix'}


# 加入可选形参，年龄
def build_person(first_name, last_name, age=''):
    """返回一个字典，其中包含有关一个人的信息"""
    person = {'first': first_name, 'last': last_name}
    if age:
        person['age'] = age
    return person

musician = build_person('jimi', 'hendrix', age = 24)
# musician = build_person('jimi', 'hendrix', 24)  # "age=" 可省略
print(musician)
# {'first': 'jimi', 'last': 'hendrix', 'age': 24}
```

#### 加入循环

```python
def get_formatted_name(first_name, last_name,age=''):
    """返回整洁的姓名"""
    full_name = first_name + ' '+last_name
    return full_name.title()

while True:
    print("\nPlease tell me your name:")
    print("(enter 'q' at any time to quit.)")
    f_name = input("First name:")
    if f_name == 'q':
        break
    l_name = input("Last name:")
    if l_name == 'q':
        break
    formatted_name = get_formatted_name(f_name,l_name)
    print("\nHello, " + formatted_name+"!")
    
# Please tell me your name:
# (enter 'q' at any time to quit.)
# First name:li
# Last name:ke
# 
# Hello, Li Ke!
# 
# Please tell me your name:
# (enter 'q' at any time to quit.)
# First name:wu
# Last name:suying
# 
# Hello, Wu Suying!
# 
# Please tell me your name:
# (enter 'q' at any time to quit.)
# First name:q 
```

### 传递列表

```python
def greet_users(names):
    """向列表中的每位用户都发出简单的问候"""
    for name in names:
        msg = "Hello, "+ name.title()+"!"
        print(msg)
usernames = ['hannah', 'ty','margot']
greet_users(usernames)
# Hello, Hannah!
# Hello, Ty!
# Hello, Margot!
```

#### 在函数中修改列表

```python
# 首先创建一个列表，其中包含一些要打印的设计
def print_models(unprinted_designs, completed_models):
    # 模拟打印每个设计，直到没有未打印的设计为止
    # 打印每个设计后，都将其移到列表completed_models中
    while unprinted_designs:
        current_design = unprinted_designs.pop()
        # 模拟根据设计制作3D打印模型的过程
        print("Printing model: " + current_design)
        completed_models.append(current_design)


def show_completed_models(completed_models):
    # 显示打印好的所有模型
    print("\nThe following models have been printed:")
    for completed_model in completed_models:
        print(completed_model)


unprinted_designs = ['iphone case', 'robot pendant', 'dodecahedron']
completed_models = []

print_models(unprinted_designs,completed_models)
show_completed_models(completed_models)
print(unprinted_designs)
# Printing model: dodecahedron
# Printing model: robot pendant
# Printing model: iphone case
#
# The following models have been printed:
# dodecahedron
# robot pendant
# iphone case
# []
```

#### 切片表示法

```python
function_name(list_name[:])
# 切片表示法[:]创建列表的副本
```

```python
# 上面的处理中，把unprinted_designs中的元素pop出去，就改变了列表
# 切片表示法[:]创建列表的副本，将列表的副本传递给函数。类似C语言里的引用，不会改变原来的列表
print_models(unprinted_designs[:],completed_models)
print(unprinted_designs)
# The following models have been printed:
# dodecahedron
# robot pendant
# iphone case
# ['iphone case', 'robot pendant', 'dodecahedron']
```

### 传递任意数量的实参

```python
def make_pizza(*toppings):
    """概述要制作的披萨(打印出每一份披萨的配料)"""
    print("\nMaking a pizza with the following toppings:")
    for topping in toppings:
        print("- "+ topping)

make_pizza('pepperoni')
make_pizza('mushrooms','green peppers','extra cheese')

# Making a pizza with the following toppings:
# - pepperoni
#
# Making a pizza with the following toppings:
# - mushrooms
# - green peppers
# - extra cheese
```

#### 结合使用位置实参和任意数量实参

```python
def make_pizza(size, *toppings):
    """概述要制作的披萨"""
    print("\nMaking a " + str(size) +
          "-inch pizza with the following toppings:")
    for topping in toppings:
        print("- " + topping)


make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
# Making a 16-inch pizza with the following toppings:
# - pepperoni
# 
# Making a 12-inch pizza with the following toppings:
# - mushrooms
# - green peppers
# - extra cheese
```

#### 使用任意数量的关键字实参

- 形参**user_info中的两个星号让Python创建一个名为user_info的空字典，并将收到的所有名称-值对都封装到这个字典中。在这个函数中，可以像访问其他字典那样访问user_info中的名称-值对。

```python
def build_profile(first, last, **user_info):
    """创建一个字典，其中包含我们知道的有关用户的一切"""
    profile = {}
    profile['first_name'] = first
    profile['last_name'] = last
    # 可简写成下面的写法
    # profile = {'first_name': first, 'last_name': last}
    for key, value in user_info.items():
        profile[key] = value
    # 我们遍历字典user_info中的键-值对，并将每个键值对都加入到字典profile中
    return profile

user_profile = build_profile('albert', 'einstein',
                             location='princeton',
                             field='physics')
print(user_profile)

# {'first_name': 'albert', 'last_name': 'einstein', 
# 'location': 'princeton', 'field': 'physics'}
```

> 编写函数时，你可以以各种方式**混合使用位置实参、关键字实参和任意数量的实参**。知道这些实参类型大有裨益，因为阅读别人编写的代码时经常会见到它们。**要正确地使用这些类型的实参并知道它们的使用时机**，需要经过一定的练习。就目前而言，牢记使用最简单的方法来完成任务就好了。继续往下阅读，就会知道在各种情况下哪种方法的效率是最高的。



### 高阶函数

#### map



#### filter



#### reduce

> reduce需要通过fuctools库导入

### 装饰器

> TL;DR
>
> 采用了闭包的思路（内外函数嵌套，内函数引用外函数作用域下的非全局变量，外函数返回内函数的引用），在不改变原函数代码的前提下为函数增添新的功能

函数是Python中的**第一类对象** ，可以把函数**赋值给变量**，对该变量进行调用，可实现原函数的功能。
（变量——函数——函数式编程）

Python中，作用域的概念仅仅存在于：当变量在Module(模块)、Class(类)、def(函数) 中定义的时候

理解这一点至关重要！ 对于LEGB原则准确、快速的理解很有帮助。

再说的直白点，作用域存在于 def和 class之内的缩进代码块 .py后缀Python文件中！

#### 1、闭包

要想了解装饰器，首先要了解一个概念，闭包。什么是闭包，一句话说就是，在函数中再嵌套一个函数，并且引用外部函数的变量，这就是一个闭包了。光说没有概念，直接上一个例子。

```python
def outer(x):
    def inner(y):
        return x + y
    return inner

print(outer(6)(5))
-----------------------------
>>>11
```

如代码所示，在outer函数内，又定义了一个inner函数，并且inner函数又引用了外部函数outer的变量x，这就是一个闭包了。在输出时，outer(6)(5),第一个括号传进去的值返回inner函数，其实就是返回6 + y，所以再传第二个参数进去，就可以得到返回值，6 + 5。

#### 2、装饰器

接下来就讲装饰器，其实装饰器就是一个闭包，装饰器是闭包的一种应用。什么是装饰器呢，简言之，**python装饰器就是用于拓展原来函数功能的一种函数，这个函数的特殊之处在于它的返回值也是一个函数，使用python装饰器的好处就是在不用更改原函数的代码前提下给函数增加新的功能。**使用时，再需要的函数前加上@demo即可。

```python
def debug(func):
    def wrapper():
        print("[DEBUG]: enter {}()".format(func.__name__))
        return func()
    return wrapper

@debug
def hello():
    print("hello")

hello()
-----------------------------
>>>[DEBUG]: enter hello()
>>>hello
```

例子中的装饰器给函数加上一个进入函数的debug模式，不用修改原函数代码就完成了这个功能，可以说是很方便了。

#### 3、带参数的装饰器

上面例子中的装饰器是不是功能太简单了，那么装饰器可以加一些参数吗，当然是可以的，另外装饰的函数当然也是可以传参数的。

```python
def logging(level):
    def outwrapper(func):
        def wrapper(*args, **kwargs):
            print("[{0}]: enter {1}()".format(level, func.__name__))
            return func(*args, **kwargs)
        return wrapper
    return outwrapper

@logging(level="INFO")
def hello(a, b, c):
    print(a, b, c)

hello("hello,","good","morning")
-----------------------------
>>>[INFO]: enter hello()
>>>hello, good morning
```

如上，装饰器中可以传入参数，先形成一个完整的装饰器，然后再来装饰函数，当然函数如果需要传入参数也是可以的，用不定长参数符号就可以接收，例子中传入了三个参数。

> @logging(level="INFO") 可以看做是 hello = logging(level="INFO")(hello)。这里的hello是函数对象，python中一切皆是对象，函数也可以像变量一样传递，加括号后hello()才是执行函数。于是这里就变成了hello = outwrapper(hello)，而outwrapper() 的返回是 wrapper，hello 就等于 wrapper，执行 hello() 就等价于执行 wrapper()，而等号右边的 hello 已经作为参数传递给 outrapper() 了

#### 4、类装饰器

装饰器也不一定只能用函数来写，也可以使用类装饰器，用法与函数装饰器并没有太大区别，实质是使用了类方法中的**call**魔法方法来实现类的直接调用。

```python
class logging(object):
    def __init__(self, func):
        self.func = func

    def __call__(self, *args, **kwargs):
        print("[DEBUG]: enter {}()".format(self.func.__name__))
        return self.func(*args, **kwargs)

@logging
def hello(a, b, c):
    print(a, b, c)

hello("hello,","good","morning")
-----------------------------
>>>[DEBUG]: enter hello()
>>>hello, good morning
```

类装饰器也是可以带参数的，如下实现

```python
class logging(object):
    def __init__(self, level):
        self.level = level

    def __call__(self, func):
        def wrapper(*args, **kwargs):
            print("[{0}]: enter {1}()".format(self.level, func.__name__))
            return func(*args, **kwargs)
        return wrapper

@logging(level="TEST")
def hello(a, b, c):
    print(a, b, c)

hello("hello,","good","morning")
-----------------------------
>>>[TEST]: enter hello()
>>>hello, good morning
```



## 10. 类

> 类将函数和数据整洁地封装起来，让你能够灵活而高效地使用它们。

### 面向对象

其实面向对象的逻辑很简单，也非常符合人类思考的直觉。正是因为接近人类思维方式，所以才成为现代编程语言的主流。

- **面向对象**相对于**[面向过程](https://www.zhihu.com/search?q=面向过程&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2365100638})**，两者编程逻辑完全不同。但面向对象也会向下兼容面向过程——Python里面也能实现面向过程。
- **过程**类似于函数，执行后不返回结果；
- 相对的，函数会返回结果。

**面向对象的编程逻辑：**

- 把功能需求的实现按步骤实现；
- 将不同的独立功能，封装成一个个独立的函数；
- 函数 - 可重复使用的代码块；
- 函数包括内置的函数，也包括用户自己编写的函数；
- 最后写成的代码，通常就是逐步地调用不同的函数。
- 在一个对象中封装多个方法和属性，以实现不同的职责；
- 根据职责的不同，定义不同的对象；
- 通过不同对象调用不同的方法，来实现项目的功能需求。

**面向对象的优点：**

- 看重对象和对象的职责；
- 不同对象有不同的属性，承担不用的角色；
- 开发套路固定，可以应付复杂的项目需求；
- 顺序调用不同对象，对象调用不用的属性和方法。

这里我们用炒菜这么一个小例子进行对比说明。

面向过程：把炒菜分解为不同步骤——把菜放入锅内->点火->加油->翻炒->出锅，菜就这么炒好了。

面向对象：

- 先抽象出不同的对象，不同对象有不同的属性和方法；
- 菜是一个对象，菜有品种、重量等属性；
- 锅是一个对象，有加菜、点火、翻炒、出锅等方法；
- 菜.种类+菜.重量+，锅.加菜 -> 锅.点火 -> 锅.翻炒 -> 锅.灭火 -> 锅.出锅；
- 如果实现得得更细一点，还可以增加锅的容量、温度等属性或者其它方法。

通过对象的方法或属性，来实现某些功能的逻辑，相对更符合人类的思维方式。



### 类 Class

> 类，是某一类具有相同特征或行为的事物的抽象。
>
> 比如人类，人类有性别、身高、体重等属性；人类有学习、吃饭、编程、写论文等行为；

- 程序开发时先定义类；
- 类的共同**特征**被称为**属性**，**attribute**；
- 类的共同**行为**被称为**方法**，**method**；
- 类是抽象的，职责很单一，就是用于创建对象，也叫实例化；
- 先有类，后有对象；同一个类只有一个，但是对象可以有很多个；
- 通过人类这个类实例化出一个”王几行“，那王几行才是一个具体的**对象**。

在Python中，几乎一切皆对象。变量、数据框、**函数，都是一个个对象**。

#### dir() 函数

> 查看类的结构，所有的属性和方法

```python
# 我们以列表型的对象为例
list1 = [1, 2, 3, 4]
dir(list1) ## list 类对象的结构

['__add__', ## 前后各带两个下划线的，是Python自带的属性或方法
 '__class__',
 '__contains__',
 '__delattr__',
 '__delitem__',
 '__dir__',
 '__doc__',
 '__eq__',
 '__format__',
 '__ge__',
 '__getattribute__',
 '__getitem__',
 '__gt__',
 '__hash__',
 '__iadd__',
 '__imul__',
 '__init__',
 '__init_subclass__',
 '__iter__',
 '__le__',
 '__len__',
 '__lt__',
 '__mul__',
 '__ne__',
 '__new__',
 '__reduce__',
 '__reduce_ex__',
 '__repr__',
 '__reversed__',
 '__rmul__',
 '__setattr__',
 '__setitem__',
 '__sizeof__',
 '__str__',
 '__subclasshook__',
 'append',
 'clear',
 'copy',
 'count',
 'extend',
 'index',
 'insert',
 'pop',
 'remove',
 'reverse',
 'sort']
```

我们试试使用这些属性或者方法。

```python
list1 = [26,1, 9,10,2]
list1.sort() ## 对list1这个对象，实现排序方法
list1

[1, 2, 9, 10, 26]
```

用 `dir()` 查看函数的结构：

```python
def add2(x, y):
    """两数之和"""
    return x + y

dir(add2)

['__annotations__',
 '__call__',
 '__class__',
 '__closure__',
 '__code__',
 '__defaults__',
 '__delattr__',
 '__dict__',
 '__dir__',
 '__doc__',
 '__eq__',
 '__format__',
 '__ge__',
 '__get__',
 '__getattribute__',
 '__globals__',
 '__gt__',
 '__hash__',
 '__init__',
 '__init_subclass__',
 '__kwdefaults__',
 '__le__',
 '__lt__',
 '__module__',
 '__name__',
 '__ne__',
 '__new__',
 '__qualname__',
 '__reduce__',
 '__reduce_ex__',
 '__repr__',
 '__setattr__',
 '__sizeof__',
 '__str__',
 '__subclasshook__']

add2.__doc__ ## 函数备注说明的属性

'两数之和'
```

#### 在类中封装方法

类中的方法的首个参数必须是`self`：self 是调用方法的那个对象的引用。

假设定义一个“人”类，定义两个方法，一个是玩耍，一个是学习。

```python
class HumanBeing: ## 类是要用“大驼峰”命名法
    
    def play(self):
        print("投篮2万次")
    
    def study(self):
        print("自学5小时")

## 通过类，创建一个对象        
linky = HumanBeing()

linky.play() ## 从林克这个对象中，调用 play 方法   

[Out: ] 投篮2万次
```

`id()`函数查看对象，在内存中的地址。

```python
id(linky) ## 查看对象在内存中的地址

[Out: ] 140324690065584

## 转换为 16 进制
("%x" % id(linky))

[Out: ] ("%x" % id(linky))
```

#### 属性的创建

- 直接给对象增加属性
- 先说一种不太推荐的、简单的操作：直接给**对象**增加一个属性。

```python
linky.height = 3.0
dir(linky)

[Out:] 
['__class__',
 '__delattr__',
 '__dict__',
 '__dir__',
 '__doc__',
 '__eq__',
 '__format__',
 '__ge__',
 '__getattribute__',
 '__gt__',
 '__hash__',
 '__init__',
 '__init_subclass__',
 '__le__',
 '__lt__',
 '__module__',
 '__ne__',
 '__new__',
 '__reduce__',
 '__reduce_ex__',
 '__repr__',
 '__setattr__',
 '__sizeof__',
 '__str__',
 '__subclasshook__',
 '__weakref__',
 'height',
 'play',
 'study']

linky.height

[Out: ] 3.0
```

不过呢，这个 height 属性，只是加在了林克这个对象上，却没有加到“HumanBeing”这个类里边。

```python
dir(HumangBeing)

[Out: ]
['__class__',
 '__delattr__',
 '__dict__',
 '__dir__',
 '__doc__',
 '__eq__',
 '__format__',
 '__ge__',
 '__getattribute__',
 '__gt__',
 '__hash__',
 '__init__',
 '__init_subclass__',
 '__le__',
 '__lt__',
 '__module__',
 '__ne__',
 '__new__',
 '__reduce__',
 '__reduce_ex__',
 '__repr__',
 '__setattr__',
 '__sizeof__',
 '__str__',
 '__subclasshook__',
 '__weakref__',
 'play',            ## 这里没有 height 这个属性
 'study']
```



### 类的多继承

- 菱形继承时，Python会按照C3算法(有向无环路图)按顺序遍历继承图
- 通过`类对象名称.__mro__` 可以查看 继承顺序
- 多重继承增加了继承的复杂度，应当减少多重继承的使用

### 混入

- 混入Mix-In是指借用多继承的语法，为现有类增加新的方法
- 混入不定义新的属性，只包含方法
- 混入便于重用，但绝不能实例化
- 混入类一般在类名称后增加Mixin

> 例如：披萨可以按层数分为单层、 双层，也可以按照形状分为圆形、方形，可以将它们定义为:单层Mixin、 双层Mixin、圆形Mixin、方形Mixin
>
> 定义一个披萨类:
> `class披萨(主要材料，单层Mixin,圆形Mixin)`



### 类的装饰器

- 类的装饰器改变了调用的方法和行为
- 类的装饰器让类的使用更加灵活，但也给新手增加了学习难度
- 非必要，不要使用类的方法的装饰器

####  classmethod装饰器

- classmethod可以实例的方法定义为类的方法，用于类直接调用

```python
class Klass:
	@classmethod
	def func(cls):
		pass
```

- cls表示当前操作的类，可以使用Klass.func()调用

#### staticmethod装饰器

- 不需要类的任何信息但又和类相关的一些方法，为了方便维护代码并保持代码工整，可以将该函数定义到类中并使用staticmethod修饰

```python
class Klass():
	@staticmethod
	def func():
		pass
```

- staticmethod修饰的方法，不需要使用self或cls 

#### property装饰器

- 把方法伪装成属性；让属性可以像方法一样编写复杂逻辑
- 调用更简单，把难度扔给编写类的人，所以很多python源码都是用这种形式

```python
class Klass:
    
	@property
	def func(self):
		return self.__varName
	@func. setter
	def func(self, varValue):
		self.__varName = varValue 
```

```python
class Klass3:
    @property
    def func(self):
        return self.__varName
    @func.setter
    def func(self, varValue):
        self.__varName = varValue

        
        
obj = Klass3()
obj.func="123"
print(obj.func)  # 123
```





### 一些常见问题

- self与cls：self指实例，cls指class

- 设计错误：
  - 哪些对象应该被抽象为类?
  - 哪些功能应该被定义为属性。哪些应该被定义为方法?
  - 如何解决类之间的依赖?

### SOLID原则

#### S 单一职责原则

- 类只负责做一件事，即只有一个职责。即越小越好

#### O 开闭原则

- 类应当对扩展开放，对修改关闭，使其有更好的可维护性

#### L 里氏替换原则

- 某个对象使用类的子类时，应当和使用父类有相同的行为。
- 即：对于任何类，客户端都能应该能无差别的使用它的子类，并且不会影响运行时的预期行为。

#### I 接口隔离原则

- Python使用“鸭子类型”实现接口，一个类对另一个类的依赖要建立在最小接口上（接口越小越好）
- 你想定义一个即像列表又像字典的功能，直接可以去改

```python
def func():
    pass
# dir(func)
# func()            
# ['__annotations__',
#  '__call__',      函数有call方法，即可以被调用,执行func()不会报错
#  '__class__',
#  '__closure__',

class Class1:
    pass
# dir(Class1)
# ['__class__',     类没有call方法，即不可以被调用，会报错 ↓ 
#  '__delattr__',
#  '__dict__',
# c1 = Class1()     # 'Class1' object is not callable
# c1()               

class Class2:
    def __call__(self):
        print("类也可以被调用")
dir(Class2)
# ['__call__',     给他加了一个__call__方法就可以了
#  '__class__',
#  '__delattr__',
#  '__dict__',
c2 = Class2()       
c2()             # "类也可以被调用"，成功调用
```



#### D 依赖倒置原则

- 高层模块不应该依赖低层模块，而是应该让二者依赖抽象









### `__init__`方法

- 有一类方法，以“`__`”开始和结束，实现了除一般方法外的特殊功能，
- 被称作**魔术方法**

#### `__init__`对象初始化方法 ：指定默认属性

在Python中，通过__init__内置方法，来对对象的属性进行初始值的设置，即初始化。 

`__init__`方法的作用：专门用来定义一个类所有的属性。

下面，我们就用这个方法，来定义类的属性。

```python
class HumanBeing:
    def __init__(self):
        self.height = 3.0 ## 默认拥有某个属性

linky = HumanBeing()
linky.height   # 3.0
```

```python
class Klass(object):
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    
    def information(self):
        
        print(self.name)
        print(self.age)
myself = Klass("Tom", 18)
myself.information()   
# Tom
# 18     
```

另外定义一个方法。

```python
class HumanBeing:
    def __init__(self):
        self.height = 3.0 ## 默认拥有某个属性

    def play(self):
        print("林克身高%s米爱打球" % self.height ) ## 这里的 self，指代的是实例化的对象
    
linky = HumanBeing()
linky.play()

[Out: ] 林克身高3.0米爱打球
```

说明：在使用类名`()`初始化对象的时候，Python会自动调用初始化方法。

#### `__init__`对象初始化方法 ：引入参数

```python
class HumanBeing:
    def __init__(self, height):
        self.height = height ## 通过参数，初始化一个属性

linky = HumanBeing(3.0)
linky.height

[Out: ] 3.0
```



## 11. 模块与标准库

### 将函数存储在模块中 — import

```python
# 导入整个模块
import module_name.function_name()
# 导入模块中的特定函数
from module_name import function_name
```

```python
# 导入整个模块
import os
# 导入模块的特定方法
from os import chdir
from os import chdir, getcwd
```

- Python读取这个文件时，代码行`import os`让Python打开文件os.py,并将其中的所有函数都复制到这个程序中。你看不到复制的代码，因为这个程序运行时，Python在 幕后复制这些代码。你只需知道，在chdir.py中， 可以使用os.py中定义的所有函数。

不同的导入方法，使用函数的格式也不同，以使用getcwd() 函数为例:

```python
import os
os.getcwd() 

from os import getcwd
getcwd()
```

#### 包

- 多个模块放在一个文件夹中，该文件夹称作**包**

- 包的导入与模块的导入相同:

  ```python
  import 包
  from 包 import 模块
  ```

#### 重命名 — as

```python
import function_name as fn
from module_name import function_name as fn

from pizza import make_pizza as mp
import make_pizza as mp
```

#### 导入所有 — *（不建议

```python
from module_name import *
#  = import module_name
```

### 标准库

https://docs.python.org/zh-cn/3.10/library/index.html

![image-20240229150242917](./Python.assets/image-20240229150242917.png)

#### 本地

![image-20240229150054187](./Python.assets/image-20240229150054187.png)

#### 远程

![image-20240229150059530](./Python.assets/image-20240229150059530.png)

### 创建自定义模块

1. 导入自定义模块时，需确保**导入路径**正确
2. 自定义模块的文件名称尽量**避免特殊字符**，文件名应**避免和标准库重名**
3. 自定义模块多次导入，模块中的代码也**只能被执行一次**
4. 自定义模块中**应为函数定义**，避免在模块中编写函数调用代码（写模块是给外面调用的，而不是在模块里就调用），或将函数调用代码放在`__name__`代码块中

![image-20240229151734937](./Python.assets/image-20240229151734937.png)

#### `if __name__ == '__main__':`

> 学过Java、C、C++的程序员应该都知道，每次开启一个程序，都必须写一个主函数作为程序的入口，也就是我们常说的main函数。如下所示， main()就是Java中的一个main函数。
>
> ```java
> public class HelloWorld {
> 	public static void main(String[] args) {
>     	System.out.println("HelloWorld");
> 	}
> }
> ```
>
> 与Java、C、C++等几种语言不同的是，Python是一种**解释型脚本语言**，在执行之前不同要将所有代码先编译成中间代码，Python程序运行时是从模块**顶行**开始，**逐行进行翻译执行**，所以，最顶层（没有被缩进）的代码都会被执行，所以Python中并不需要一个统一的main()作为程序的入口。在某种意义上讲，“`if __name__==’__main__:`”也像是一个标志，象征着Java等语言中的程序主入口，告诉其他程序员，代码入口在此——这是“`if __name__==’__main__:`”这条代码的意义之一。
>
> Python解释器在导入模块时，会将模块中没有缩进的代码全部执行一遍（模块就是一个独立的Python文件）。开发人员通常会在模块下方增加一些测试代码，为了避免这些测试代码在模块被导入后执行，可以利用`__name__`属性。
>
> 具体来说：
>
> `__name__`属性是Python的一个内置属性，记录了一个字符串。
>
> - 若是在当前文件，`__name__` 是`__main__`。
> - 在hello文件中打印本文件的`__name__`属性值，显示的是`__main__`
>
> ![image-20240229152715724](./Python.assets/image-20240229152715724.png)
>
> - 若是导入的文件，`__name__`是模块名。
> - test66文件导入hello模块，在test66文件中打印出hello模块的`__name__`属性值，显示的是hello模块的模块名。
>
> ![image-20240229153800874](./Python.assets/image-20240229153800874.png)
>
> - 因此`__name__ == '__main__'` 就表示在当前文件中，可以在`if __name__ == '__main__':`条件下写入测试代码，如此可以避免测试代码在模块被导入后执行。



## 12. 异常

- 异常是Python解释器在执行程序的过程中，出现错误时的一种管理机制，它会在错误被监测到的位置“引发
- 引发异常时，代码块会发生中断
- 异常是一种特殊**对象**
- 除SystemExit异常外，当异常没有被完全处理时，都会打印栈回溯信息

```python
>>> 10 * (1/0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: division by zero
>>> 4 + spam*3
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'spam' is not defined
>>> '2' + 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```



### 异常基类

- BaseException —— 所有内置异常的基类
- Exception —— 所有内置的非系统退出类异常都派生自此类，所有用户自定义异常也应当派生自此类
- ArithmeticError —— 此基类用于派生针对各种算术类错误而引发的内置异常
- BufferError —— 当与缓冲区相关的操作无法执行时此基类将被引发
- LookupError —— 此基类用于派生当映射或序列所使用的键或索引无效时引发的异常

### 异常捕获

出现异常时，如何利用程序进行处理？

```python
try:
	可能产生异常的代码
except异常:
	捕获指定的异常后运行的代码
finally:
	无论是否抛出异常，该部分代码均会执行
```



#### try-except子句

```python
>>> while True:
...     try:
...         x = int(input("Please enter a number: "))
...         break
...     except ValueError:
...         print("Oops!  That was no valid number.  Try again...")
```

[`try`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#try) 语句的工作原理如下：

- 首先，执行 *try 子句* （[`try`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#try) 和 [`except`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#except) 关键字之间的（多行）语句）。
- 如果没有触发异常，则跳过 *except 子句*，[`try`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#try) 语句执行完毕。
- 如果在执行 [`try`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#try) 子句时发生了异常，则跳过该子句中剩下的部分。 如果异常的类型与 [`except`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#except) 关键字后指定的异常相匹配，则会执行 *except 子句*，然后跳到 try/except 代码块之后继续执行。
- 如果发生的异常与 *except 子句* 中指定的异常不匹配，则它会被传递到外部的 [`try`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#try) 语句中；如果没有找到处理程序，则它是一个 *未处理异常* 且执行将终止并输出如上所示的消息。

[`try`](https://docs.python.org/zh-cn/3.10/reference/compound_stmts.html#try) 语句可以有多个 *except 子句* 来为不同的异常指定处理程序。 但最多只有一个处理程序会被执行。 处理程序只处理对应的 *try 子句* 中发生的异常，而不处理同一 `try` 语句内其他处理程序中的异常。 *except 子句* 可以用带圆括号的元组来指定多个异常，例如:

```python
... except (RuntimeError, TypeError, NameError):
...     pass
```

#### else子句

`try` ... `except` 语句具有可选的 *else 子句*，该子句如果存在，它必须放在所有 *except 子句* 之后。 它适用于 *try 子句* 没有引发异常但又必须要执行的代码。 例如:

```python
for arg in sys.argv[1:]:
    try:
        f = open(arg, 'r')
    except OSError:
        print('cannot open', arg)
    else:
        print(arg, 'has', len(f.readlines()), 'lines')
        f.close()
```

使用 `else` 子句比向 `try` 子句添加额外的代码要好，可以避免意外捕获非 `try` ... `except` 语句保护的代码触发的异常。



#### finally子句

`try` 语句还有一个可选子句，用于定义在所有情况下都必须要执行的清理操作。例如：

```python
>>> try:
...     raise KeyboardInterrupt
... finally:
...     print('Goodbye, world!')
...
Goodbye, world!
KeyboardInterrupt
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
```

**如果存在 `finally` 子句，则 `finally` 子句是 `try` 语句结束前执行的最后一项任务。不论 `try` 语句是否触发异常，都会执行 `finally` 子句。**以下内容介绍了几种比较复杂的触发异常情景：

- 如果执行 `try` 子句期间触发了某个异常，则某个 `except` 子句应处理该异常。如果该异常没有 `except` 子句处理，在 `finally` 子句执行后会被重新触发。
- `except` 或 `else` 子句执行期间也会触发异常。 同样，该异常会在 `finally` 子句执行之后被重新触发。
- 如果 `finally` 子句中包含 `break`、`continue` 或 `return` 等语句，异常将不会被重新引发。
- 如果执行 `try` 语句时遇到 `break`,、`continue` 或 `return` 语句，则 `finally` 子句在执行 `break`、`continue` 或 `return` 语句之前执行。
- 如果 `finally` 子句中包含 `return` 语句，则返回值来自 `finally` 子句的某个 `return` 语句的返回值，而不是来自 `try` 子句的 `return` 语句的返回值。

#### 捕获多个异常

- try语句块可以支持捕获多个异常:

```python
try:
	可能产生异常的语句
except 异常1:
	处理方式
except 异常2:
	处理方式二
except...
```

### 自定义异常

借用Python强大的异常处理功能，编写程序中断逻辑，继承现有的异常，并**为现有的异常增加额外功能**。

自定义异常需要继承异常的基类，一般通过继承Exception 类实现:

```python
class MyException(Exception)
```















## 13.高级数据类型与算法











# Python 数据结构

## 线性表

### 用列表实现堆栈

使用列表方法实现堆栈非常容易，最后插入的最先取出（“后进先出”）。把元素添加到堆栈的顶端，使用 `append()` 。从堆栈顶部取出元素，使用 `pop()` ，不用指定索引。例如：

```python
>>> stack = [3, 4, 5]
>>> stack.append(6)
>>> stack.append(7)
>>> stack
[3, 4, 5, 6, 7]
>>> stack.pop()
7
>>> stack
[3, 4, 5, 6]
>>> stack.pop()
6
>>> stack.pop()
5
>>> stack
[3, 4]
```

### 用列表实现队列

列表也可以用作队列，最先加入的元素，最先取出（“先进先出”）；然而，列表作为队列的效率很低。因为，在列表末尾添加和删除元素非常快，但在列表开头插入或移除元素却很慢（因为所有其他元素都必须移动一位）。

实现队列最好用 [`collections.deque`](https://docs.python.org/zh-cn/3.10/library/collections.html#collections.deque)，可以快速从两端添加或删除元素。例如：

```python
>>> from collections import deque
>>> queue = deque(["Eric", "John", "Michael"])
>>> queue.append("Terry")           # Terry arrives
>>> queue.append("Graham")          # Graham arrives
>>> queue.popleft()                 # The first to arrive now leaves
'Eric'
>>> queue.popleft()                 # The second to arrive now leaves
'John'
>>> queue                           # Remaining queue in order of arrival
deque(['Michael', 'Terry', 'Graham'])
```



## 数组

### Python原生方法

```python
# Array native python methods :
    # append()	Adds an element at the end of the list
    # clear()	Removes all the elements from the list
    # copy()	Returns a copy of the list
    # count()	Returns the number of elements with the specified value
    # extend()	Add the elements of a list (or any iterable), to the end of the current list
    # index()	Returns the index of the first element with the specified value
    # insert()	Adds an element at the specified position
    # pop()	    Removes the element at the specified position
    # remove()	Removes the first item with the specified value
    # reverse()	Reverses the order of the list
    # sort()	Sorts the list
```

```python
strings = ['a','b','c','d']
# 4*4 = 16 bytes of storage is used

print(strings[2])  # c

# push
strings.append('e')  # O(1)
# pop
strings.pop()
strings.pop()  # O(1)

# add first element
strings.insert(0, 'x')  # O(n)

# splice
strings.insert(2, 'alien')  # O(n)

print(strings)  # ['x', 'a', 'alien', 'b', 'c']

#List objects are implemented as arrays. 
#They are optimized for fast fixed-length operations and incur O(n) memory movement costs for pop(0) and insert(0, v) 
#operations which change both the size and position of the underlying data representation.

#For in depth information on arrays 
#https://docs.python.org/3/tutorial/datastructures.html

#to implement arrays as a stack 
#https://docs.python.org/3/library/collections.html#collections.deque

```

### 实现数组功能

```python
class Array:
    def __init__(self):
        self.length = 0
        self.data = {}

    def __str__(self):
        return str(self.__dict__)

    def get(self, index):
        return self.data[index]

    def push(self, item):
        self.data[self.length] = item
        self.length += 1

    def pop(self):
        lastitem = self.data[self.length - 1]
        del self.data[self.length - 1]
        self.length -= 1
        return lastitem

    def delete(self, index):
        deleteditem = self.data[index]
        for i in range(index, self.length - 1):
            self.data[i] = self.data[i + 1]

        del self.data[self.length - 1]
        self.length -= 1
        return deleteditem

arr = Array()
arr.push(3)
arr.push('hi')
arr.push(34)
arr.push(20)
arr.push('hey')
arr.push('welcome')
arr.delete(3)
print(arr)
# {'length': 5, 'data': {0: 3, 1: 'hi', 2: 34, 3: 'hey', 4: 'welcome'}}
```

### 归并排序

```python
# 用自带方法实现
def merge_sorted_arr(a, b):
    x = a + b
    x.sort()
    return x
a = [1, 2, 3, 4]
b = [3, 7, 9, 12]
qw = mergesortedarr(a, b)
print(qw) # [1, 2, 3, 3, 4, 7, 9, 12]

# 面试中要这样写
def merge_sorted_arr(a, b):
    if len(a) == 0 or len(b) == 0:
        return a + b
    mylist = []
    i = 0
    j = 0
    while i < len(a) and j < len(b):
        if a[i] <= b[j]:
            mylist.append(a[i])
            i += 1
        elif b[j] < a[i]:
            mylist.append(b[j])
            j += 1
    return mylist + a[i:] + b[j:]

a = [1, 3, 4, 6, 20]
b = [2, 3, 4, 5, 6, 9, 11, 76]
x = mergesortedarr(a, b)
print(x)
# [1, 2, 3, 3, 4, 4, 5, 6, 6, 9, 11, 20, 76]
```

### 字符串逆转

```python
def reverse(stra):
    mylist = []
    for i in range(len(stra) - 1, -1, -1):
        mylist.append(stra[i])
        # 注意，这里得到的mylist是类似‘a’,‘b’一个一个的字符，所以最后需要join串起来
    return ''.join(mylist)
x = reverse('I am kelin')
print(x)
#nilek ma I

# or just stra[::-1]
```





## 递归

### 阶乘

```python
# 阶乘的递归实现
def factorial_recursion(num):
    if num == 1:
        return 1
    return num * factorial_recursion(num - 1)

# 阶乘的循环实现
def factorial_for(num):
    result = 1
    for i in range(1, num + 1):
        result = result * i
    return result

print(factorial_recursion(6))  # 720
print(factorial_for(6))  # 720
```

### fibonacci

```python
def fibonacci_for(num):
    if num < 2:
        return num
    a = 0
    b = 1
    total = 0
    for i in range(num-1):
        total = a+b
        a = b
        b = total
    return total


def fibonacci_recursion(num):
    if num < 2:
        return num
    return fibonacci_for(num - 1) + fibonacci_for(num - 2)


print([fibonacci_for(i) for i in range(10)])
print([fibonacci_recursion(i) for i in range(10)])
print([0, 1, 1, 2, 3, 5, 8, 13, 21, 34])

```

### 使用递归逆序一个字符串

```python
def reverse(word):
    size = len(word)
    if size == 0:
        return
    last_char = word[size - 1]
    print(last_char, end='')
    return reverse(word[0:size - 1])
reverse('hello there')
# ereht olleh
```





## 图

### 简单生成一个图

```python
class Graph:
  def __init__(self):
    self.numberofnodes = 0
    self.adjacentlist = {}

  def __str__(self):
    return str(self.__dict__)
  
  def addVertex(self,node):
    self.adjacentlist[node] = []
    self.numberofnodes += 1

  def addEdge(self,node1,node2):
    self.adjacentlist[node1].append(node2)
    self.adjacentlist[node2].append(node1)

  def showConnection(self):
    for vertex, neighbors in self.adjacentlist.items():
      print(vertex, end = '-->')
      print(' '.join(neighbors))
      

myGraph = Graph()
myGraph.addVertex('0')
myGraph.addVertex('1')
myGraph.addVertex('2')
myGraph.addVertex('3')
myGraph.addVertex('4')
myGraph.addVertex('5')
myGraph.addVertex('6')
myGraph.addEdge('3', '1')
myGraph.addEdge('3', '4')
myGraph.addEdge('4', '2') 
myGraph.addEdge('4', '5') 
myGraph.addEdge('1', '2') 
myGraph.addEdge('1', '0') 
myGraph.addEdge('0', '2') 
myGraph.addEdge('6', '5')
print(myGraph)
# {'numberofnodes': 7, 'adjacentlist': {'0': ['1', '2'], '1': ['3', '2', '0'], '2': ['4', '1', '0'], '3': ['1', '4'], '4': ['3', '2', '5'], '5': ['4', '6'], '6': ['5']}}

myGraph.showConnection()
# 0-->1 2
# 1-->3 2 0
# 2-->4 1 0
# 3-->1 4
# 4-->3 2 5
# 5-->4 6
# 6-->5
```



## 排序

### 冒泡排序

```python
def bubblesort(arr):
    qw = 0
    while qw < len(arr):
        for i in range(0, len(arr) - 1):
            if arr[i] > arr[i + 1]:
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
        qw += 1
    return arr

arr = [5, 9, 1, 2, 7, 3, 8, 2]
print(bubblesort(arr))
# [1, 2, 2, 3, 5, 7, 8, 9]
```

### 插入排序

```python
def insertionsort(arr):
    length = len(arr)
    i = 1
    end = arr[0]
    while i < length:
        if arr[i] < end:
            x = arr.pop(i)
            for j in range(0, i):
                if x < arr[j]:
                    arr.insert(j, x)
                    break
        end = arr[i]
        i += 1
    return arr

arr = [6, 5, 3, 1, 8, 7, 2, 4]
print(insertionsort(arr))
```



## 数据结构和算法

- 算法：解决问题的方法和步骤

- 评价算法的好坏：渐近时间复杂度和渐近空间复杂度。

- 渐近时间复杂度的大O标记：

  - <img src="http://latex.codecogs.com/gif.latex?O(c)" /> - 常量时间复杂度 - 布隆过滤器 / 哈希存储
  - <img src="http://latex.codecogs.com/gif.latex?O(log_2n)" /> - 对数时间复杂度 - 折半查找（二分查找）
  - <img src="http://latex.codecogs.com/gif.latex?O(n)" /> - 线性时间复杂度 - 顺序查找 / 计数排序
  - <img src="http://latex.codecogs.com/gif.latex?O(n*log_2n)" /> - 对数线性时间复杂度 - 高级排序算法（归并排序、快速排序）
  - <img src="http://latex.codecogs.com/gif.latex?O(n^2)" /> - 平方时间复杂度 - 简单排序算法（选择排序、插入排序、冒泡排序）
  - <img src="http://latex.codecogs.com/gif.latex?O(n^3)" /> - 立方时间复杂度 - Floyd算法 / 矩阵乘法运算
  - <img src="http://latex.codecogs.com/gif.latex?O(2^n)" /> - 几何级数时间复杂度 - 汉诺塔
  - <img src="http://latex.codecogs.com/gif.latex?O(n!)" /> - 阶乘时间复杂度 - 旅行经销商问题 - NPC

  ![](./Python.assets/algorithm_complexity_1.png)

  ![](./Python.assets/algorithm_complexity_2.png)

- 排序算法（选择、冒泡和归并）和查找算法（顺序和折半）

  ```Python
  def select_sort(items, comp=lambda x, y: x < y):
      """简单选择排序"""
      items = items[:]
      for i in range(len(items) - 1):
          min_index = i
          for j in range(i + 1, len(items)):
              if comp(items[j], items[min_index]):
                  min_index = j
          items[i], items[min_index] = items[min_index], items[i]
      return items
  ```

  ```Python
  def bubble_sort(items, comp=lambda x, y: x > y):
      """冒泡排序"""
      items = items[:]
      for i in range(len(items) - 1):
          swapped = False
          for j in range(len(items) - 1 - i):
              if comp(items[j], items[j + 1]):
                  items[j], items[j + 1] = items[j + 1], items[j]
                  swapped = True
          if not swapped:
              break
      return items
  ```

  ```Python
  def bubble_sort(items, comp=lambda x, y: x > y):
      """搅拌排序(冒泡排序升级版)"""
      items = items[:]
      for i in range(len(items) - 1):
          swapped = False
          for j in range(len(items) - 1 - i):
              if comp(items[j], items[j + 1]):
                  items[j], items[j + 1] = items[j + 1], items[j]
                  swapped = True
          if swapped:
              swapped = False
              for j in range(len(items) - 2 - i, i, -1):
                  if comp(items[j - 1], items[j]):
                      items[j], items[j - 1] = items[j - 1], items[j]
                      swapped = True
          if not swapped:
              break
      return items
  ```

  ```Python
  def merge(items1, items2, comp=lambda x, y: x < y):
      """合并(将两个有序的列表合并成一个有序的列表)"""
      items = []
      index1, index2 = 0, 0
      while index1 < len(items1) and index2 < len(items2):
          if comp(items1[index1], items2[index2]):
              items.append(items1[index1])
              index1 += 1
          else:
              items.append(items2[index2])
              index2 += 1
      items += items1[index1:]
      items += items2[index2:]
      return items
  
  
  def merge_sort(items, comp=lambda x, y: x < y):
      return _merge_sort(list(items), comp)
  
  
  def _merge_sort(items, comp):
      """归并排序"""
      if len(items) < 2:
          return items
      mid = len(items) // 2
      left = _merge_sort(items[:mid], comp)
      right = _merge_sort(items[mid:], comp)
      return merge(left, right, comp)
  ```

  ```Python
  def seq_search(items, key):
      """顺序查找"""
      for index, item in enumerate(items):
          if item == key:
              return index
      return -1
  ```

  ```Python
  def bin_search(items, key):
      """折半查找"""
      start, end = 0, len(items) - 1
      while start <= end:
          mid = (start + end) // 2
          if key > items[mid]:
              start = mid + 1
          elif key < items[mid]:
              end = mid - 1
          else:
              return mid
      return -1
  ```

- 常用算法：

  - 穷举法 - 又称为暴力破解法，对所有的可能性进行验证，直到找到正确答案。
  - 贪婪法 - 在对问题求解时，总是做出在当前看来
  - 最好的选择，不追求最优解，快速找到满意解。
  - 分治法 - 把一个复杂的问题分成两个或更多的相同或相似的子问题，再把子问题分成更小的子问题，直到可以直接求解的程度，最后将子问题的解进行合并得到原问题的解。
  - 回溯法 - 回溯法又称为试探法，按选优条件向前搜索，当搜索到某一步发现原先选择并不优或达不到目标时，就退回一步重新选择。
  - 动态规划 - 基本思想也是将待求解问题分解成若干个子问题，先求解并保存这些子问题的解，避免产生大量的重复运算。

  穷举法例子：百钱百鸡和五人分鱼。

  ```Python
  # 公鸡5元一只 母鸡3元一只 小鸡1元三只
  # 用100元买100只鸡 问公鸡/母鸡/小鸡各多少只
  for x in range(20):
      for y in range(33):
          z = 100 - x - y
          if 5 * x + 3 * y + z // 3 == 100 and z % 3 == 0:
              print(x, y, z)
  
  # A、B、C、D、E五人在某天夜里合伙捕鱼 最后疲惫不堪各自睡觉
  # 第二天A第一个醒来 他将鱼分为5份 扔掉多余的1条 拿走自己的一份
  # B第二个醒来 也将鱼分为5份 扔掉多余的1条 拿走自己的一份
  # 然后C、D、E依次醒来也按同样的方式分鱼 问他们至少捕了多少条鱼
  fish = 6
  while True:
      total = fish
      enough = True
      for _ in range(5):
          if (total - 1) % 5 == 0:
              total = (total - 1) // 5 * 4
          else:
              enough = False
              break
      if enough:
          print(fish)
          break
      fish += 5
  ```

  贪婪法例子：假设小偷有一个背包，最多能装20公斤赃物，他闯入一户人家，发现如下表所示的物品。很显然，他不能把所有物品都装进背包，所以必须确定拿走哪些物品，留下哪些物品。

  |  名称  | 价格（美元） | 重量（kg） |
  | :----: | :----------: | :--------: |
  |  电脑  |     200      |     20     |
  | 收音机 |      20      |     4      |
  |   钟   |     175      |     10     |
  |  花瓶  |      50      |     2      |
  |   书   |      10      |     1      |
  |  油画  |      90      |     9      |

  ```Python
  """
  贪婪法：在对问题求解时，总是做出在当前看来是最好的选择，不追求最优解，快速找到满意解。
  输入：
  20 6
  电脑 200 20
  收音机 20 4
  钟 175 10
  花瓶 50 2
  书 10 1
  油画 90 9
  """
  class Thing(object):
      """物品"""
  
      def __init__(self, name, price, weight):
          self.name = name
          self.price = price
          self.weight = weight
  
      @property
      def value(self):
          """价格重量比"""
          return self.price / self.weight
  
  
  def input_thing():
      """输入物品信息"""
      name_str, price_str, weight_str = input().split()
      return name_str, int(price_str), int(weight_str)
  
  
  def main():
      """主函数"""
      max_weight, num_of_things = map(int, input().split())
      all_things = []
      for _ in range(num_of_things):
          all_things.append(Thing(*input_thing()))
      all_things.sort(key=lambda x: x.value, reverse=True)
      total_weight = 0
      total_price = 0
      for thing in all_things:
          if total_weight + thing.weight <= max_weight:
              print(f'小偷拿走了{thing.name}')
              total_weight += thing.weight
              total_price += thing.price
      print(f'总价值: {total_price}美元')
  
  
  if __name__ == '__main__':
      main()
  ```

  分治法例子：[快速排序](https://zh.wikipedia.org/zh/%E5%BF%AB%E9%80%9F%E6%8E%92%E5%BA%8F)。

  ```Python
  """
  快速排序 - 选择枢轴对元素进行划分，左边都比枢轴小右边都比枢轴大
  """
  def quick_sort(items, comp=lambda x, y: x <= y):
      items = list(items)[:]
      _quick_sort(items, 0, len(items) - 1, comp)
      return items
  
  
  def _quick_sort(items, start, end, comp):
      if start < end:
          pos = _partition(items, start, end, comp)
          _quick_sort(items, start, pos - 1, comp)
          _quick_sort(items, pos + 1, end, comp)
  
  
  def _partition(items, start, end, comp):
      pivot = items[end]
      i = start - 1
      for j in range(start, end):
          if comp(items[j], pivot):
              i += 1
              items[i], items[j] = items[j], items[i]
      items[i + 1], items[end] = items[end], items[i + 1]
      return i + 1
  ```

  回溯法例子：[骑士巡逻](https://zh.wikipedia.org/zh/%E9%AA%91%E5%A3%AB%E5%B7%A1%E9%80%BB)。

  ```Python
  """
  递归回溯法：叫称为试探法，按选优条件向前搜索，当搜索到某一步，发现原先选择并不优或达不到目标时，就退回一步重新选择，比较经典的问题包括骑士巡逻、八皇后和迷宫寻路等。
  """
  import sys
  import time
  
  SIZE = 5
  total = 0
  
  
  def print_board(board):
      for row in board:
          for col in row:
              print(str(col).center(4), end='')
          print()
  
  
  def patrol(board, row, col, step=1):
      if row >= 0 and row < SIZE and \
          col >= 0 and col < SIZE and \
          board[row][col] == 0:
          board[row][col] = step
          if step == SIZE * SIZE:
              global total
              total += 1
              print(f'第{total}种走法: ')
              print_board(board)
          patrol(board, row - 2, col - 1, step + 1)
          patrol(board, row - 1, col - 2, step + 1)
          patrol(board, row + 1, col - 2, step + 1)
          patrol(board, row + 2, col - 1, step + 1)
          patrol(board, row + 2, col + 1, step + 1)
          patrol(board, row + 1, col + 2, step + 1)
          patrol(board, row - 1, col + 2, step + 1)
          patrol(board, row - 2, col + 1, step + 1)
          board[row][col] = 0
  
  
  def main():
      board = [[0] * SIZE for _ in range(SIZE)]
      patrol(board, SIZE - 1, SIZE - 1)
  
  
  if __name__ == '__main__':
      main()
  ```

  动态规划例子：子列表元素之和的最大值。

  > 说明：子列表指的是列表中索引（下标）连续的元素构成的列表；列表中的元素是int类型，可能包含正整数、0、负整数；程序输入列表中的元素，输出子列表元素求和的最大值，例如：
  >
  > 输入：1 -2 3 5 -3 2
  >
  > 输出：8
  >
  > 输入：0 -2 3 5 -1 2
  >
  > 输出：9
  >
  > 输入：-9 -2 -3 -5 -3
  >
  > 输出：-2

  ```Python
  def main():
      items = list(map(int, input().split()))
      overall = partial = items[0]
      for i in range(1, len(items)):
          partial = max(items[i], partial + items[i])
          overall = max(partial, overall)
      print(overall)
  
  
  if __name__ == '__main__':
      main()
  ```

  > **说明**：这个题目最容易想到的解法是使用二重循环，但是代码的时间性能将会变得非常的糟糕。使用动态规划的思想，仅仅是多用了两个变量，就将原来$O(N^2)$复杂度的问题变成了$O(N)$。









# Python Tips

- python行末加不加分号都行
- python中没有`i++`，`i--`的操作，需要写成`i+=1`,`i-=1`的形式

## join方法

1. 元素序列是列表

```python
a = '!@'.join(['Fusion', 'Sphere', 'Cloud'])
a
'Fusion!@Sphere!@Cloud'
```

2. 元素序列是元组
```python
" ".join(('China', 'Japan', 'USA', 'UK'))
'China Japan USA UK'
```

3. 元素序列是集合
```python
''.join({'C', 'h', 'i', 'n', 'a'})
'ahCni'
# 可以看出，输出的字符顺序与集合中元素的顺序不是保持一致的。
```

4. 元素序列是字典
```python
' ~ '.join({'Asia':'China', 'Europe':'UK'})
'Asia ~ Europe'
# 可以看出，如果序列是字典，拼接的字符是字典的键。
```

5. 元素序列是字符串
当元素序列仅仅是字符串时，join函数会将字符串中的每一个单个字符抽取出来，与连接符组合。

```python
', '.join('happy')
'h, a, p, p, y'
```

注意事项

1. 要连接的字符串序列（参数）必须是字符串
join函数的参数应该是全部由字符串构成的可迭代对象。当可迭代对象不全是由字符串构成的时，Python会报错TypeError。

例如，参数是一个由字符串和整数构成的列表时：

```python
' * '.join(['1', 2])
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: sequence item 1: expected str instance, int found
```

2. 字符串连接符可省略
字符串连接符可以省略（空字符串）。当字符串连接符为空时，序列中的所有字符串都将连接成一个字符串。

```python
''.join(['1', '2', '3', '4', '5'])
'12345'
```



3. 当可迭代序列是集合时，拼接结果是无序的
如果可迭代序列参数是集合，join的返回结果不一定是元素在集合中的顺序，而是打乱的：

```python
' -- '.join({'a', 'b', 'c'})
'b -- c -- a'
```



4. 当可迭代序列是字典时，拼接结果是键的拼接
如果可迭代序列参数是字典，join的返回结果是字典中键的拼接结果，而不是键值对的拼接结果。

可以用values函数来拼接值的结果。

```python
test_dict = {'A':'a', 'B':'b', 'C':'c'}
"".join(test_dict)
'ABC'
"".join(test_dict.values())
'abc'
```



## 语法糖

### 推导式

**推导式（又称解析器）**，是 Python 独有的一种特性。

使用推导式可以**快速生成列表、元组、字典以及集合类型的数据**，因此推导式又可细分为列表推导式、元组推导式、字典推导式以及集合推导式。

#### 列表推导式

列表推导式可以利用 range 区间、元组、列表、字典和集合等数据类型，快速生成一个满足指定需求的列表。

列表推导式的语法格式如下：

```python
[表达式 for 迭代变量 in 可迭代对象 [if 条件表达式] ]
```


此格式中，[if 条件表达式] 不是必须的，可以使用，也可以省略。

通过列表推导式的语法格式，明显会感觉到它和 for 循环存在某些关联。

其实，除去 [if 条件表达式] 部分，其余各部分的含义以及执行顺序和 for 循环是完全一样的（表达式其实就是 for 循环中的循环体），即它的执行顺序如下所示：

```python
for 迭代变量 in 可迭代对象:
    表达式
```

> **可以这样认为，它只是对 for 循环语句的格式做了一下简单的变形，并用 [] 括起来而已，只不过最大的不同之处在于，列表推导式最终会将循环过程中，计算表达式得到的一系列值组成一个列表。**

```python
a_range = range(10)
# 对a_range执行for表达式
a_list = [x * x for x in a_range]
# a_list集合包含10个元素
print(a_list)

输出结果：
[0 , 1 , 4 , 9 , 16 , 25 , 36 , 49 , 64, 81]

```

上面代码的第 3 行会对 a_range 执行迭代，由于 a_range 相当于包含 10 个元素，因此程序生成的 a_list 同样包含 10 个元素，且每个元素都是 a_range 中每个元素的平方（由表达式 x * x 控制）。

不仅如此，我们还可以在列表推导式中添加 `if 条件语句`，这样列表推导式将只迭代那些符合条件的元素。例如：

```python
b_list = [x * x for x in a_range if x % 2 == 0]
# a_list集合包含5个元素
print(b_list)

输出结果：
[0 ,4 , 16, 36, 64]
```

这里给列表推导式增加了 if 条件语句，这会导致推导式只处理 range 区间的偶数，因此程序生成的 b_list 只包含 5 个元素。

另外，以上所看到的列表推导式都只有一个循环，实际上它可使用多个循环，就像嵌套循环一样。例如如下代码：

```python
d_list = [(x, y) for x in range(5) for y in range(4)]
# d_list列表包含20个元素
print(d_list)
```

上面代码中，**x 是遍历 range(5) 的迭代变量**（计数器），因此该 x 可迭代 5 次；**y 是遍历 range(4) 的计数器**，因此该 y 可迭代 4 次。因此，**该（x,y）表达式一共会迭代 20 次**。上面的 for 表达式相当于如下嵌套循环：

```python
dd_list = []
for x in range(5):
    for y in range(4):
        dd_list.append((x, y))

输出结果：
[(0, 0), (0, 1), (0, 2), (0, 3), (1, 0), (1, 1), (1, 2), (1, 3), (2, 0), (2, 1), (2, 2), (2, 3), (3, 0), (3, 1), (3, 2), (3, 3), (4, 0), (4, 1), (4, 2), (4, 3)]

```

当然，也支持类似于三层嵌套的 for 表达式，例如如下代码：

```python
e_list = [[x, y, z] for x in range(5) for y in range(4) for z in range(6)]
# e_list列表包含120个元素
print(e_list)
```

对于包含多个循环的 for 表达式，同样可指定 if 条件。

假如我们有一个需求：

- 程序要将两个列表中的数值按“能否整除”的关系配对在一起。
- 比如 src_a 列表中包含 30，src_b 列表中包含 5，其中 30 可以整除 5，那么就将 30 和 5 配对在一起。对于上面的需求使用 for 表达式来实现非常简单，例如如下代码：

```python
src_a = [30, 12, 66, 34, 39, 78, 36, 57, 121]
src_b = [3, 5, 7, 11]
# 只要x能整除y，就将它们配对在一起
result = [(x, y) for x in src_a for y in src_b if x % y == 0]
print(result)

输出结果：
[(30, 3), (30, 5), (12, 3), (66, 3), (66, 11), (39, 3), (78, 3), (36, 3), (57, 3), (121, 11)]

```

```python
print([x*x for x in range(10) if x % 7 == 0])
# 上面这行等价于下面这段
number = 0
list1 = []
while number < 10:
    if number % 7 == 0:
        list1.append(number*number)
    number += 1
print(list1)

# [0, 49]
```



#### 元组推导式

元组推导式可以利用 range 区间、元组、列表、字典和集合等数据类型，快速生成一个满足指定需求的元组。

元组推导式的语法格式如下：

```python
(表达式 for 迭代变量 in 可迭代对象 [if 条件表达式] )
```

其中，用 [] 括起来的部分，可以使用，也可以省略。

通过和列表推导式做对比，你会发现，除了**元组推导式是用 () 圆括号**将各部分括起来，而列表推导式用的是 []，其它完全相同。不仅如此，元组推导式和列表推导式的用法也完全相同。

例如，我们可以使用下面的代码生成一个包含数字 1~9 的元组：

```python
a = (x for x in range(1,10))
print(a)

输出结果：
<generator object <genexpr> at 0x000001C6E5F97748>
```

从上面的执行结果可以看出，使用元组推导式生成的结果并不是一个元组，而是一个**生成器对象**，这一点和列表推导式是不同的。

如果我们想要使用元组推导式获得新元组或新元组中的元素，有以下三种方式：

1. 使用 tuple() 函数，可以直接将生成器对象转换成元组，例如：

   ```python
   a = (x for x in range(1,10))
   print(tuple(a))
   
   运行结果为：
   (1, 2, 3, 4, 5, 6, 7, 8, 9)
   
   ```

2. 直接使用 for 循环遍历生成器对象，可以获得各个元素，例如：

   ```python
   a = (x for x in range(1,10))
   for i in a:
       print(i,end=' ')
   print(tuple(a))
   
   输出结果：
   1 2 3 4 5 6 7 8 9 ()
   ```

3. 使用 __next__() 方法遍历生成器对象，也可以获得各个元素，例如：

   ```python
   a = (x for x in range(3))
   print(a.__next__())
   print(a.__next__())
   print(a.__next__())
   a = tuple(a)
   print("转换后的元组：",a)
   
   输出结果：
   0
   1
   2
   转换后的元组： ()
   ```

注意，无论是使用 for 循环遍历生成器对象，还是使用 __next__() 方法遍历生成器对象，遍历后原生成器对象将不复存在，这就是遍历后转换原生成器对象却得到空元组的原因。

#### 字典推导式

Python 中，使用字典推导式可以借助列表、元组、字典、集合以及 range 区间，快速生成符合需求的字典。

字典推导式的语法格式如下：

```python
{表达式 for 迭代变量 in 可迭代对象 [if 条件表达式]}
```

可以看到，和其它推导式的语法格式相比，唯一不同在于，**字典推导式用的是大括号{}**。

```python
listdemo = ['Jack','Tom']
#将列表中各字符串值为键，各字符串的长度为值，组成键值对
newdict = {key:len(key) for key in listdemo}
print(newdict)

输出结果：
{'Jack': 4, 'Tom': 3}
```

交换现有字典中各键值对的键和值。

```python
olddict={'Jack': 4, 'Tom': 3}
newdict = {v: k for k, v in olddict.items()}
print(newdict)

输出结果：
{4: 'Jack', 3: 'Tom'}
```

使用 if 表达式筛选符合条件的键值对。

```python
olddict={'Jack': 4, 'Tom': 3}
newdict = {v: k for k, v in olddict.items() if v>3}
print(newdict)

输出结果：
{4: 'Jack'}
```

#### 集合推导式

集合推导式的语法格式和字典推导式完全相同，如下所示：

```
{ 表达式 for 迭代变量 in 可迭代对象 [if 条件表达式] }
```


**集合推导式和字典推导式的格式完全相同，那么给定一个类似的推导式，如何判断是哪种推导式呢？**

最简单直接的方式，就是根据表达式进行判断，如果表达式以键值对`(key：value)`的形式，则证明此推导式是字典推导式；反之，则是集合推导式。

```python
setnew = {i**2 for i in range(3)}
print(setnew)

输出结果：
{0, 1, 4}
```

既然生成的是集合，那么其保存的元素必须是唯一的。

```python
tupledemo = (1,1,2,3,4,5,6,6)
setnew = {x**2 for x in tupledemo if x%2==0}
print(setnew)

输出结果：
{16, 4, 36}
```

```python
dictdemo = {'1':1,'2':2,'3':3}
setnew = {x for x in dictdemo.keys()}
print(setnew)

输出结果：
{'2', '1', '3'}
```





### 生成全0列表

```python
>>> c = [0]
>>> a = c * 10
[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
```



## Mistakes

```python
In [1]: c = [0]
In [2]: a = [c for i in range(10)]
In [3]: a
Out[3]: [[0], [0], [0], [0], [0], [0], [0], [0], [0], [0]]
In [4]: a[0][0] = 1
In [5]: a
Out[5]: [[1], [1], [1], [1], [1], [1], [1], [1], [1], [1]]
# 这里a是把c的引用重复了10次，因此对第一个元素赋值，也相对于对其他元素赋值
# 可以改成下面这样
In [6]: a = [[0] for i in range(10)]
In [7]: a
Out[7]: [[0], [0], [0], [0], [0], [0], [0], [0], [0], [0]]
In [8]: a[0][0] = 1
In [9]: a
Out[9]: [[1], [0], [0], [0], [0], [0], [0], [0], [0], [0]]
```



### 遍历过程中修改列表

- 导致数据遗漏

```python
list1 = [ 'a', 'b', 'c', 'd' ]
	for i in range(len(list1)):
	list1.pop(i)
# 列表在执行pop()之后，长度会减少，因此不能使用固定长度的for循环遍历
```









## OJ help

- 除了题意之外，要认真查看输入输出的格式
- 对于输入来说:
  - 多行输入，每一行对应一个input()函数，根据题目描述的输入类型转换
  - 如果每行一个整数，则可以写a = int(input())这样的读入代码
  - 单行输入多个变量的话，用input().split()读入并分 解为列表
  - 如果多个整数在一行，则用list(map(int, input() .split()))来获取
- 对于输出来说:
  - 如果是单个整数，直接print即可
  - 如果是浮点数，则要看清保留小数点后几位，比如4位，用(%.4f) 这样
  - 特别注意**空格的位置和数量**，行末一般不输出空格，即使肉眼无法察觉



## 轮子

### 计算Pi

- 用反余弦函数

```python
import math

def Pi(x:int):
    pi = math.acos(-1) # 用反余弦函数来算
    print(f'{pi:.{x}f}') # x是浮点数的位数

Pi(20)
# 3.14159265358979311600
```

- 蒙特卡洛法

![image-20231205163210344](./Python.assets/image-20231205163210344.png)

```python
import random

# 蒙特卡洛方法
def cal_pi(n:int) -> float:
    count = 0

    for i in range(int(n)):
        x = random.random()
        y = random.random()
        d = (x - 0.5) ** 2 + (y - 0.5) ** 2
        if d <= 0.5 ** 2:
            count+=1
        else:
            pass

    return (4*count)/n

# 测试验证
n = 10000000 # n为点的数量
print(f"PI的近似值为：{cal_pi(int(n))}")
# PI的近似值为：3.1424044
```

- 莱布尼兹公式

### ASCII

- 数字：0(48) ~ 9(57)
- 大写字母：A(65) ~ Z(90)
- 小写字母：a(97) ~ z(122)

```python
c = input()
print(c.upper())
#a
#A
```

- 将s中的小写字母转换为大写字母

```C++
for (int i = 0; i < s.length(); i++) {
	if (s[i] >= 'a' && s[i] <= 'z') {
		s[i].upper;
	}
	compare[s[i]] = 1;
}
```



### 定义无穷大

```C++
#define INF 0x3f3f3f3f //定义成无穷大
```



### 求长度

```C++
#include <iostream>
using namespace std;
int main(){
    int i[10];
    cout << "sizeof(i)  = " << sizeof(i) << endl;	//整个数组所占的空间长度
    cout << "sizeof(*i) = " << sizeof(*i) << endl;	//第一个元素（单个元素）所占的空间长度
    cout << "sizeof(i) / sizeof(*i) = " << sizeof(i) / sizeof(*i) << endl;//整个数组长度/元素个数
    return 0;
}
//result
  sizeof(i)  = 40
  sizeof(*i) = 4
  sizeof(i) / sizeof(*i) = 10
```



### 求一行数字的和

```C++
string s; //用string接受输入  
cin >> s;
int sum = 0;
for(int i = 0; i < s.length(); i++)
    sum += (s[i] - '0'); 
cout<<sum;
```

### 四舍五入

#### ceil、floor、round

```C++
#include<iostream>
#include<cmath>
using namespace std;
int main(){
    double a=2.5;
    cout<<ceil(a)<<endl;   //向上取整
    cout<<floor(a)<<endl;   //向下取整
    cout<<round(a)<<endl;   //四舍五入
    //不使用函数实现
    cout<<(a>(int)a?(int)a+1:(int)a)<<endl;  //向上取整
    cout<<(int)a<<endl;    //向下取整_正数
    cout<<(int)(a+0.5)<<endl;   //四舍五入_正数
    cout<<(int)a-1<<endl;    //向下取整_负数
    cout<<(int)(a-0.5)<<endl;   //四舍五入_负数
    return 0;
}
```



### 判断素数

```C++
bool isprime(int a) {
    if (n <= 1) return false;
    for (int i = 2; i * i <= a; i++)
        if (a % i == 0) return false;
    return true;
}
//或者
bool isprime(int n) {
	if (n <= 1) return false;
	int sqr = int(sqrt(n * 1.0));
	for (int i = 2; i <= sqr; i++)
		if (n % i == 0) return false;
	return true;
}
```



### 数字转数组

```C++
void number_to_array(int n,int num[]){	//将数字n的每一位存到num数组中
	for(int i = 0; i < 4; i++){
		num[i] = n % 10;
		n /= 10;
	}
}
```

### 数组转数字

```C++
int array_to_number(int num[]){	//将num数组转换成数字
	int sum = 0;
	for(int i = 0; i < 4; i++){
		sum = sum * 10 + num[i];
	} 
	return sum;
} 
```



### 进制转换

```C++
//将十进制数x 转换为D进制数y 
int res[40],i = 0;	//数组y存放D进制x的每一位，num为位数
do{
	res[i++] = x % D;	//除基取余
	x = x / D;
} while(x!=0);	//当商不为0时进行循环 
//倒序输出
while(i>0)
    cout<<res[--i];
```

#### sprintf ( )

```c++
sprintf(s, "%8x", 4567); //小写16 进制，宽度占8个位置，右对齐
sprintf(s, "%-8X", 4568); //大写16 进制，宽度占8个位置，左对齐
这样，一个整数的16进制字符串就很容易得到，但我们在打印16进制内容时，通常想要一种左边补0的等宽格式，那该怎么做呢？很简单，在表示宽度的数字前面加个0 就可以了。
sprintf(s, "%08X", 4567); //产生："000011D7"
上面以"%d"进行的10进制打印同样也可以使用这种左边补0的方式。
```



### 判断闰年

```C++
bool isLeap(int year){
	return (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);//返回的是条件语句（1/0）
}
```



### 求反序数

```C++
// 1234   →  4321
int Reverse(int x){
    int rvex = 0;
    while(x != 0){
        revx *= 10;
        revx += x % 10;
        x /= 10;
    }
    return revx;
}
```



### 判断回文串

```C++
bool judge(char str[]){
	int len = strlen(str);	//字符串长度
	for(int i = 0;i < len / 2;i++){//枚举字符串的前一半 
		if(str[i]!=str[len-1-i])
			return false; 
	} 
	return true;
}
```

### 最大公约数

```C++
//辗转相除法
int gcd(int a, int b){
	return b == 0 ? a : gcd(b, a % b);
}
```

### 最小公倍数

```c++
int lcm(int a, int b){
	return a * b / gcd (a, b); 
}
```

- Example

```C++
#include<iostream> 
using namespace std;
int gcd(int a, int b){
	return b == 0 ? a : gcd(b, a % b);
}
int lcm(int a, int b){
	return a * b / gcd (a, b); 
}
int main(){
	int a, b, g, l;
	g = gcd(64, 16);
	l = lcm(8, 12);
	cout << "64和12的最大公约数为 " << g << endl;
	cout << "8和12的最小公倍数为 " << l << endl;
	return 0;
}
```

### 九九乘法表

```python
# 用列表推导式生成九九乘法表
print('\n'.join([' '.join([ f"{j}*{i}={j*i}" for j in range(1,i+1)]) for i in range(1,10)]))

# 用双循环实现
for j in range(1,10):
    for i in range(1,j+1):
        print(f'{i}*{j}={i*j}',end=' ')
    print()

# 1*1=1 
# 1*2=2 2*2=4 
# 1*3=3 2*3=6 3*3=9 
# 1*4=4 2*4=8 3*4=12 4*4=16 
# 1*5=5 2*5=10 3*5=15 4*5=20 5*5=25 
# 1*6=6 2*6=12 3*6=18 4*6=24 5*6=30 6*6=36 
# 1*7=7 2*7=14 3*7=21 4*7=28 5*7=35 6*7=42 7*7=49 
# 1*8=8 2*8=16 3*8=24 4*8=32 5*8=40 6*8=48 7*8=56 8*8=64 
# 1*9=9 2*9=18 3*9=27 4*9=36 5*9=45 6*9=54 7*9=63 8*9=72 9*9=81 

```



### 阶乘

```C++
int F1(int n){
	int temp = 1;
	for(int i = n; i > 0; i--)
		temp = temp * i;  //模拟阶乘的数学算法
	return temp; 
} 

int F2(int n){
    if(n == 0) return 1;	//当到达递归边界F(0)时，返回F(0)==1
    else return F(n-1) * n;	//当没有到达递归边界时，使用递归式递归下去
}
```



### Fibonacci数列

```C++
int Fibonacci_recursion(int n){
	if(n == 0 || n == 1) return 1;
    else return Fibonacci_recursion(n - 1) + Fibonacci_recursion(n - 2);
}

int Fibonacci_loop(int n){
	int a* = new [n]{1,1};	//a[0]=a[1]=1
    for(int i = 3; i < n; i++)
		a[i] = a[i-1]+a[i-2];
    return a[n-1];
}
```



### 批量赋值

- #include< string.h>	//C
  #include< cstring> 	//C++

- **void \*memset(void \*str, int c, size_t n)** 复制字符 **c**（一个无符号字符）到参数 **str** 所指向的字符串的前 **n** 个字符。

```C++
int n = 10;
//方法一
int* a = new int[n];
memset(a, 0, n*sizeof(int));
//方法二
int b[10];
for(int i = 0; i<n; ++i)
	b[i] = 0;	
```

```C++
#include<stdio.h>
#include<string.h>
int main(){
	int a[5][6];
	memset(a,-1,sizeof(a)); //批量赋值
	for(int i = 0;i<4;i++){	//输出
		for(int j =0;j<5;j++)
			printf("%d",a[i][j]);
		printf("\n");
	}
	printf("\n");
	return 0;
}
```

### 求因子

```C++
for (int i = 1; i < N; i++){ //不包括N自身
    if (N % i == 0){
        cout<<i<<" ";
    }
}
```



### 打印直角梯形

```C++
#include<iostream>
using namespace std;
int main(){
	int h;
	scanf("%d",&h) ;
	while(h>0){
		int row = h;	//4 
		int col = h+(h-1)*2;	//10
		for(int i = 0; i < row; ++i){
			for(int j = 0; j < col; ++j){
				if(j < col-(h+2*i))
					cout<<" ";
				else
					cout<<"*";
			}
			cout<<endl;
		}
		h = -1*h;
	}
	return 0;
} 

//10
//                  **********
//                ************
//              **************
//            ****************
//          ******************
//        ********************
//      **********************
//    ************************
//  **************************
//****************************
```



### 输出一个正整数的各位之和

```C++
int getSum(int num) {
	int sum = 0;
	while(num != 0) {
		sum += num % 10;	//不断取个位数求和 
		num /= 10;		
	}
	return sum;
}
```



### 输出一个正整数的所有因子

```C++
#include<iostream>
#include<cstring>
#include<cmath> 
using namespace std; 
int main(){
	int yinzi[1000];	//存放因子 
    int N;	//待求整数 
    cin >> N;
    int vis = sqrt(N) + 1;
    memset(yinzi, 0, sizeof(yinzi));
    //仅输出因子 
    for (int i = 2; i <= vis; i++){
        if (N % i == 0){
            cout<<i<<" ";
        }
    }
    cout<<endl;
    //输出因子的同时也保存在数组中 
    for (int i = 2, j = 0; i <= vis; i++){
        if (N % i == 0){
            yinzi[j++] = i;   
            cout<<i<<" ";
        }
    }
}
```



### 格式化输出

```c++
printf("%04d-%02d-%02d\n",year,month,day);
yyyy-mm-dd
```

### 【str[i] - 'a'】做索引

```C++
for(int i = 0; i<str.size(); ++i){
	time += keytab[str[i]-'a'];			//str[i]取到字符串中的某一个字母，-'a'得到第几个字母(从0开始) 
	if(i != 0 && str[i]-str[i-1] == keytab[str[i]-'a'] - keytab[str[i-1]-'a'])
		time += 2; 
}


for (int i = 0; i < v.size(); i++) {
    if (arr[v[i]] == 0) {
        if (flag == 1) cout << " ";
        cout << v[i];
        flag = 1;
    }
}
```

### “最后一个元素后没有空格”

```C++
//法一
for (int i = 0; i < v.size(); i++) {
    if (arr[v[i]] == 0) {
        if (flag == 1) cout << " ";	//第一次循环flag = 0，不输出"_", 最后一个元素输出后，就跳出循环了
        cout << v[i];	//因此每次循环输出: "_X"、"_X"、"_X"...最后输出
        flag = 1;	//输出一个元素之后才flag设为1
    }
}

//法二
for (int i = 0; i < n - 1; i++)
    cout << a[i] << " ";
cout << a[n - 1];
```







```c++
#include<iostream>
using namespace std;
const int n = 10;
int a[n] = { 1,2,3,4,5,6,7,8,9,10 };
long long s;
vector<int>v;
void dfs(int sum)
{
    if (sum >= 10)
    {
        if (sum == 10) 
        {
            for (int i = 0;i < v.size();i++)
            {
                cout << v[i] << " ";
            }
            s++; //求种数
            cout << endl;
        }
        return;
    }
    for (int i = 0;i < n;i++)
    {
        v.push_back(a[i]);
        sum += a[i];
        dfs(sum);
        sum -= a[i];
        v.pop_back();
    }
}
int main()
{
    dfs(0);
    cout << s << endl;
    return 0;
}
```



# Python 小demo

## 文件

### 文件编码检测

```python
# pip install chardet
from chardet.universaldetector import UniversalDetector
 
detector = UniversalDetector()
 
with open("./test.txt", "rb") as f:
    detector.feed(f.read())
    detector.close()
 
    print(detector.result)
# {'encoding': 'utf-8', 'confidence': 0.7525, 'language': ''}
```



### 文档读取

```python
import pprint
with open("./24-demo.txt") as f:
    file_data = f.readlines()
    pprint.pprint(file_data)   # 为了演示文件内容而特意使用了pprint

 # ['You can eat and eat, but nothing will ever fill the void. Welcome to the '
#  'real world! It sucks. You’re gonna love it!\n',
#  '\n',
#  'I thought that it (propose) mattered what I said or where I said it. \n',
#  '\n',
#  'Then I realized the only thing that matters is that you, you make me happier '
#  'than I ever thought I could be.\n',
#  '\n',
#  'If I had known the last time I saw you would be the last time, I ... I would '
#  'have stopped to memorize your face, the way you move, everything about '
#  'you. \n',
#  '\n',
#  'If I had known the last time I kissed you would have been the last time... I '
#  'never would have stopped.\n',
#  '\n',
#  'Monica, I thought this (getting married) was going to be the most difficult '
#  'thing I ever gonna have to do. \n',
#  '\n',
#  'But when I saw you walking down that aisle I realized how simple it was.\n',
#  '\n',
#  'I love you. Any surprises that come our way it’s okay, because I will always '
#  'love you. You are the person I was meant to spend the rest of my life '
#  'with.\n',
#  '\n',
#  'I say more sumb things before 9 am than most people say all day.\n',
# ...   


# 统计全部行数
print(len(file_data))          # 27

# 统计空行行数
print(file_data.count("\n"))     # 13

# 统计非空行的行数,方法1：相减
print(len(file_data) - file_data.count("\n"))             # 14
# 方法2：将列表数据转换为set数据，这样空行就只有一个（重复的被去掉），
# 再-1，那剩下的集合长度，就是非空行的行数
print(len(set(file_data)) - 1)                            # 14

# 统计单词 I 出现的次数
print(file_data.count("I"))  # 错误用法，结果为0
print(str(file_data).split(" ").count("I"))   # 16

# 统计单词 you 和 You 出现的次数
print(int(str(file_data).split(" ").count("you")) + int(str(file_data).split(" ").count("You"))) # 9
```

### 文件合并

- 合并文件 = 读取原始文件 + 追加写入新的文件
- 关键任务:
  1. 以可读取的模式打开原始文件
  2. 以写入的模式创建并打开要合并的文件
  3. 正确关闭文件

```python
# 打开文件demo1.txt并读取其数据
with open("demo1.txt") as f1:
    file_data_1 = f1.read()
# 打开文件demo2.txt并读取其数据
with open("demo2.txt") as f2:
    file_data_2 = f2.read()
# 将两个数据写入到demo3.txt
with open("demo3.txt", mode="w") as f3:
    f3.write(file_data_1)
    f3.write(file_data_2)
```











































