#

# Python 语法

## 1. Python概述

如果您的工作主要是用电脑完成的，总有一天您会想能不能自动执行一些任务。比如，对大量文本文件执行查找、替换操作；利用复杂的规则重命名、重排序一堆照片文件；也可能您想编写一个小型数据库、或开发专用的图形界面应用，甚至是开发一个简单的游戏。

作为一名专业软件开发人员，您可能要处理 C/C++/Java 库，但编码、编译、测试、再编译这些开发流程太慢了；也许您正在给这些库开发测试套件，但总觉得这项工作真是枯燥乏味。又或许，您开发了个使用扩展语言的软件，却不想为这个软件专门设计一种新语言。

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

现在，您已经对 Python 跃跃欲试，想深入了解一些细节了吧。要知道，学习语言的最佳方式是上手实践，建议您边阅读本教程，边在 Python 解释器中练习。

本教程的其他部分将利用各种示例，介绍 Python 语言、系统的功能，开始只是简单的表达式、语句和数据类型，然后是函数、模块，最后，介绍一些高级概念，如，异常、用户定义的类等功能。

## 2. 变量和数据类型

### 2.2 变量

#### 命名和使用

​		在Python中使用变量时，需要遵守一些规则和指南。违反这些规则将引发错误，而指南旨在让你编写的代码更容易阅读和理解。请务必牢记下述有关变量的规则。

- 变量名只能包含字母、数字和下划线。变量名可以字母或下划线打头，但不能以数字打头， 例如，可将变量命名为mesage_1,但不能将其命名为1_message。
- 变量名不能包含空格，但可使用下划线来分隔其中的单词。例如，变量名greeting_message可行，但变量名greeting message会引发错误。
- 不要将Python关键字和函数名用作变量名，即不要使用Python保留用于特殊用途的单词，如print。
- 变量名应既简短又具有描述性。例如，name比n好，student_name比s_n好，name_length比length_of_persons_name好。
- 慎用小写字母1和大写字母O，因为它们可能被人错看成数字1和0。

​	要创建良好的变量名，需要经过一定的实践，在程序复杂而有趣时尤其如此。随着你编写的程序越来越多，并开始阅读别人编写的代码，将越来越善于创建有意义的变量名。

### 2.3 字符串

- 字符串有多种表现形式，用单引号（`'……'`）或双引号（`"……"`）标注的结果相同
- 反斜杠 `\` 用于转义

```python
>>> 'spam eggs'  # single quotes
'spam eggs'
>>> 'doesn\'t'  # use \' to escape the single quote...
"doesn't"
>>> "doesn't"  # ...or use double quotes instead
"doesn't"
>>> '"Yes," they said.'
'"Yes," they said.'
>>> "\"Yes,\" they said."
'"Yes," they said.'
>>> '"Isn\'t," they said.'
'"Isn\'t," they said.'
```

- print()函数输出的内容更简洁易读，它会省略两边的引号，并输出转义后的特殊字符：

```python
>>> s = 'First line.\nSecond line.'  # \n means newline
>>> s  # without print(), \n is included in the output
'First line.\nSecond line.'
>>> print(s)  # with print(), \n produces a new line
First line.
Second line.
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

#### 拼接

- 字符串可以用 `+` 合并（粘到一起），也可以用 `*` 重复：

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

但是，切片会自动处理越界索引：

```
>>> word[4:42]
'on'
>>> word[42:]
''
```

Python 字符串不能修改，是 immutable 的。因此，为字符串中某个索引位置赋值会报错：

> imumutable — 不可变对象：具有固定值的对象。不可变对象包括数字、字符串和元组。这样的对象不能被改变。如果必须存储一个不同的值，则必须创建新的对象。它们在需要常量哈希值的地方起着重要作用，例如作为字典中的键。

```
>>> word[0] = 'J'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>> word[2:] = 'py'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```

要生成不同的字符串，应新建一个字符串：

```
>>> 'J' + word[1:]
'Jython'
>>> word[:2] + 'py'
'Pypy'
```

#### 制表符

```python
print("Languages:\n\tPython\n\tC++\n\tJava")
#Languages:
#	Python
#	C++
#	Java
```

#### 常用函数

##### len()

内置函数 [`len()`](https://docs.python.org/zh-cn/3.10/library/functions.html#len) 返回字符串的长度：

```
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

##### str()

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



### 2.4 数字

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
  - `//`也称为整数除法。 结果值是一个整数，但结果的类型不一定是 int。 运算结果总是向负无穷的方向舍入: `1//2` 为 `0`, `(-1)//2` 为 `-1`, `1//(-2)` 为 `-1` 而 `(-1)//(-2)` 为 `0`。
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



#### _

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





### 2.5 python之禅

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

## 3. 列表

> 列表让你能够在一个地方存储成组的信息，其中可以只包含几个元素，也可以包含数百万个元素。列表是新手可直接使用的最强大的Python功能之一，它融合了众多重要的编程概念。

### 访问列表

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

### 修改元素

- 与 [immutable](https://docs.python.org/zh-cn/3.10/glossary.html#term-immutable) 字符串不同, 列表是 [mutable](https://docs.python.org/zh-cn/3.10/glossary.html#term-mutable) 类型，其内容可以改变：

  > mutable -- 可变对象
  >
  > 可变对象可以在其 [`id()`](https://docs.python.org/zh-cn/3.10/library/functions.html#id) 保持固定的情况下改变其取值。另请参见 immutable。

```python
>>> cubes = [1, 8, 27, 65, 125]  # something's wrong here
>>> 4 ** 3  # the cube of 4 is 64, not 65!
64
>>> cubes[3] = 64  # replace the wrong value
>>> cubes
[1, 8, 27, 64, 125]
```

- 直接按列表位置修改即可

```python
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles)# ['honda', 'yamaha', 'suzuki']
 
motorcycles[0] = 'ducati'
print(motorcycles)# ['ducati', 'yamaha', 'suzuki']
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

### 添加元素


- 指定位置插入：.insert(k, "XXX")

```python
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles) # ['honda', 'yamaha', 'suzuki']

motorcycles.insert(2,"ducati")
print(motorcycles) # ['honda', 'yamaha', 'ducati', 'suzuki']
```

- 末尾添加：.append("XXX")

```python
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles) # ['honda', 'yamaha', 'suzuki']

motorcycles.append("ducati")
print(motorcycles) # ['honda', 'yamaha', 'suzuki', 'ducati']
```

### 删除元素

- **指定值**删除：.remove("XXX")

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

### 组织列表

#### 合并

```
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

#### 列表长度

> Python计算列表元素数时从1开始，因此确定列表长度时，你应该不会遇到差一错误。

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



#### 统计计算

```python
digits = [1,2,3,4,5,6,7,8,9,0]
print(min(digits)) # 0
print(max(digits)) # 9
print(sum(digits)) # 45
```

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

#没有指定结束索引，Python列表提取至末尾元素
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

## 4. 元组

- 相比于列表，元组是更简单的数据结构。如果需要存储的一组值在程序的整个生命周期内都不变，可使用元组。
- 值不可被修改的列表
- 列表是`list0=[1,2,3]`，元组是`tuple0=(1,2,3)`
- 对不应变化的值提供了一定程度的保护

> 列表非常适合用于存储在**程序运行期间可能变化的数据集**。列表是可以修改的，这对处理网站的用户列表或游戏中的角色列表至关重要。然而，有时候你需要创建一系列不可修改的元素，元组可以满足这种需求。Python将不能修改的值称为不可变的，而**不可变的列表**被称为元组。

### 定义元组

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

### 遍历元组

```python
dimesions = (200,50,30,10)
for dimesion in dimesions:
    print(dimesion)
# 200
# 50
# 30
# 10
```

### 修改元组

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



## 5. 字典

> 在Python中，字典是一系列**键-值对**。每个键都与一个值相关联，你可以使用键来访问与之相关联的值。与键相关联的值可以是数字、字符串、列表乃至字典。事实上，可将任何Python对象用作字典中的值。
>
> 键值对是两个相关联的值。指定键时，Python将返回与之相关联的值。键和值之间用冒号分隔，而键值对之间用逗号分隔。在字典中，你想存储多少个键值对都可以。

```python
alien_0 = {'color':'green','points':5}
```

### 使用字典

#### 访问字典

```python
alien_0 = {'color': 'green', 'points': 5}
new_points = alien_0['points']
print("You just earned "+str(new_points)+" points!")
# You just earned 5 points!
```

- 如果你在有外星人被射杀时都运行这段代码，就会获取该外星人的点数。

#### 添加键值对

```python
alien_0 = {'color': 'green', 'points': 5}
alien_0['x_position'] = 0
alien_0['y_position'] = 25
print(alien_0)
# {'color': 'green', 'points': 5, 'x_position': 0, 'y_position': 25}
```

```python
alien_0 = {}
alien_0['color'] = 'green'
alien_0['points'] = 5
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

#### 由类似对象组成的字典

```python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'c++'
}
print("Sarah's favorite language is "+
      favorite_languages['sarah'].title()+".")
# Sarah's favorite language is C.
```

### 遍历字典

#### 遍历所有键值对

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

注意，即便遍历字典时，键值对的返回顺序也与存储顺序不同。Python不关心键 值对的存储顺序，而只跟踪键和值之间的关联关系。

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

- ​	遍历字典时，会默认遍历所有的键，因此，如果将上述代码中的for name in favorite_languages.keys(): 替换为 for name in favorite languages:，输出将不变。
  ​	如果显式地使用方法keys()可让代码更容易理解，你可以选择这样做，但如果你愿意，也可省略它。

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

### 嵌套

#### 字典列表

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

### 在字典中存储列表

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

#### 在字典中存储字典

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

## 6. 流程控制语句

### if语句

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

### match

match语句接受一个表达式，并将其值与作为一个或多个case块给出的连续模式进行比较。这表面上类似于C、Java或JavaScript(以及许多其他语言)中的switch语句，但它更类似于Rust或Haskell等语言中的模式匹配。只有第一个匹配的模式被执行，它还可以从值中提取组件(序列元素或对象属性)到变量中。

### for

​	Python 的 `for` 语句与 C 或 Pascal 中的不同。Python 的 `for` 语句不迭代算术递增数值（如 Pascal），或是给予用户定义迭代步骤和暂停条件的能力（如 C），而是**迭代列表或字符串等任意序列**，元素的迭代顺序与在序列中出现的顺序一致。 

```python
>>> # Measure some strings:
... words = ['cat', 'window', 'defenestrate']
>>> for w in words:
...     print(w, len(w))
...
cat 3
window 6
defenestrate 12
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





### while循环

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

#### 让用户选择何时退出

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

#### 使用break退出循环

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

#### 在循环中使用continue

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

#### 使用while循环来处理列表和字典

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

##### end取消换行

- 关键字参数 *end* 可以取消输出后面的换行, 或用另一个字符串结尾：

```
>>> a, b = 0, 1
>>> while a < 1000:
...     print(a, end=',')
...     a, b = b, a+b
...
0,1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,
```







## 7. 输入与输出

### 输入input()

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

#### 使用int()来获取数值输入

```python
height = input("How tall are you, in meters? ")
height = float(height)  # input函数直接输入得到的是字符串，做比较时得转换成数值
print(height)
if height >= 1.2:
    print("\nYou're tall enough to ride!" )
else:
    print("\nYou'll be able to ride when yor're a little older")
```

#### 求模

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

### 输出print()

- `print()` 函数输出给定参数的值。与表达式不同（比如，之前计算器的例子），它能处理多个参数，包括浮点数与字符串。它输出的字符串不带引号，且各参数项之间会插入一个空格，这样可以实现更好的格式化操作：

  ```python
  >>> i = 256*256
  >>> print('The value of i is', i)
  The value of i is 65536
  ```









## 8. 函数

```python
def greet_user(username):
    "显示简单的问候语"
    print("Hello, "+ username.title() +"!")

greet_user('jesse')
# Hello, Jesse!
```

### 传递实参

#### 位置实参

- 注意多个参数时，实参的前后位置要对应准确

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

#### 关键字实参

- 关键字实参是传递给函数的名称值对。你直接在实参中将名称和值关联起来了，因此向函数传递实参时不会混淆(不会得到名为Hamster的harry这样的结果)。关键字实参让你无需考虑函数调用中的实参顺序，还清楚地指出了函数调用中各个值的用途。
- 使用关键字实参时，务必准确地指定函数定义中的形参名。

```python
def describe_pet(animal_type, pet_name):
    "显示宠物的信息"
    print("\nI have a "+animal_type+".")
    print("My "+animal_type+"'s name is "+pet_name.title()+".")

describe_pet('hamster', 'harry')
describe_pet(pet_name='harry',animal_type='hamster')
# I have a hamster. 
# My hamster's name is Harry.
#
# I have a hamster.
# My hamster's name is Harry.
```

#### 默认值

- 使用默认值时，在形参列表中必须先列出没有默认值的形参，再列出有默认值的实参。这让Python依然能够正确地解读位置实参。

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

#### 等效的函数调用

```Python
# 函数定义
def describe_pet(pet_name, animal_type= 'dog' ):


# 函数调用    
#一条名为Willie的小狗
describe_pet('willie')
describe_pet(pet_name= 'willie')
#一只名为Harry的仓鼠
describe_pet('harry','hamster' )
describe_pet(pet_name=' harry', animal_type= 'hamster')
describe_pet(animal_type=' hamster', pet_name= ' harry')
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

### 将函数存储在模块中 — import

```python
# 导入整个模块
module_name.function_name()
# 导入模块中的特定函数
from module_name import function_name
```

```python
# 导入整个模块
import pizza
# 导入模块中的特定函数
from pizza import make_pizza
```

- Python读取这个文件时，代码行`import pizza`让Python打开文件pizza.py,并将其中的所有函数都复制到这个程序中。你看不到复制的代码，因为这个程序运行时，Python在 幕后复制这些代码。你只需知道，在making_pizzas.py中， 可以使用pizza.py中定义的所有函数。

#### 重命名 — as

```python
import function_name as fn
from module_name import function_name as fn

from pizza import make_pizza as mp
import make_pizza as mp
```

#### 导入所有 — *

```python
from module_name import *
#  = import module_name
```



## 9. 类

> 类将函数和数据整洁地封装起来，让你能够灵活而高效地使用它们。

### 创建和使用类

看书《Python编程从入门到实践》：==P157==







### 使用类和实例







### 继承





### 导入类



### Python标准库





### 类编码风格



# Python 数据结构

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













# Python Tips

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

















































