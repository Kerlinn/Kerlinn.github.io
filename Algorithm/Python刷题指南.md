# 常用函数

## Python内建函数

- `format()`：格式化输出函数(在控制输出精度和空格补齐等问题中很好用)

- `round(x)`：四舍五入

- `cmp(x, y)`：比较2个对象，如果 x < y 返回 −1, 如果 x = y 返回 0, 如果x > y返回1 

- `abs(x)/max()/min()`：绝对值/最大值/最小值

- `len()`：返回对象的长度，如列表、字典等

- `range(start=0, stop, step=1])`：返回一个可迭代对象，常用于for循环

- `sum(iterable)`： 求和函数

- `pow(x, y, [z])`：求幂函数x^y^ ，运算完毕可以顺带对z取模；大数取模问题可以直接AC

- `sorted(iterable, key, reverse)`：采用[Timsort](https://en.wikipedia.org/wiki/Timsort)的稳定排序算法，默认升序；该函数太重要了，请多写写代码研究一下它的各个参数

  > sorted 语法：
  >
  > ```
  > sorted(iterable, cmp=None, key=None, reverse=False)
  > ```
  >
  > 参数说明：
  >
  > - iterable -- 可迭代对象。
  > - cmp -- 比较的函数，这个具有两个参数，参数的值都是从可迭代对象中取出，此函数必须遵守的规则为，大于则返回1，小于则返回-1，等于则返回0。
  > - key -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
  > - reverse -- 排序规则，reverse = True 降序 ， reverse = False 升序（默认）。

- `isinstance(obj, type)`：判断类型

- `all(iterable) / any(iterable)`：迭代与操作/迭代或操作（0、1、None均等价于False)

- `int(x, base=10))/float()/str()`：转整数(可自定义进制)/转浮点数/转字符串

- `bin()/oct()/hex()`：10进制转二进制(返回0b开头的字符串)/10进制转八进制(返回0开头的字符串)/10进制转十六进制(返回0x开头的字符串)

- `ord()/chr()`：字符转ASCII或ASCII转字符

- `complex(real, imag)`：创建一个复数，不过现在可以直接通过语法糖创建，eg：`1+2j`

- `divmod()`：函数把除数和余数运算结果结合起来，返回一个包含商和余数的元组(a // b, a % b)

- `eval(expression, [globals, locals])`：**执行一个字符串表达式**，并返回表达式的值，在某些字符串解析题中非常好用。

  > 以下是 eval() 方法的语法:
  >
  > ```
  > eval(expression[, globals[, locals]])
  > ```
  >
  > ### 参数
  >
  > - expression -- 表达式。
  > - globals -- 变量作用域，全局命名空间，如果被提供，则必须是一个字典对象。
  > - locals -- 变量作用域，局部命名空间，如果被提供，可以是任何映射对象。
  >
  > ### 返回值
  >
  > 返回表达式计算结果。
  >
  > ------
  >
  > ## 实例
  >
  > 以下展示了使用 eval() 方法的实例：
  >
  > ```
  > >>>x = 7
  > >>> eval( '3 * x' )
  > 21
  > >>> eval('pow(2,2)')
  > 4
  > >>> eval('2 + 2')
  > 4
  > >>> n=81
  > >>> eval("n + 4")
  > 85
  > ```
  >
  > 

- `map(function, iterable...)`：映射函数，需要注意的是在Python3中返回一个迭代对象而不再是一个列表

- `filter(function, iterable)`：过滤函数

- `reduce(function, iterable, [initializer])`：累积函数，现在被归类到functools模块

- `zip(iterable, ...)`：将对象中对应的元素打包成一个个元组，常用于并联取值，详见下文的【注意事项】

- `hash(obj)`：返回哈希码，常用于对象比较或将其转化为唯一的索引(不过更推荐使用id()完成该需求)

- `id()`：返回对象的唯一标识符，和`hash()`类似，但更鲁棒更快且可以对list、def等对象求id

- `enumerate()`：将一个可遍历的数据对象组合为一个索引序列，eg:`for i, v in enumerate(list_a):`

### 注意事项

1. 标准输出函数`print(*objects, sep=' ', end='\n')`可以通过设置`seq`标志位来设定间隔字符、设置`end`来设定结尾字符，常用于进行灵活的输出。对列表输出时，也常用`' '.join(result_list)`来快速输出一个串，而不用挨个遍历。

2. 需要注意的是，若从`range()`中取遍历指示器，在Python 3中，在for循环内重复定义迭代变量不影响迭代遍历的值，如：

   ```python
   # (Python 3)该段代码最终输出0 1 2三行，而不是只有一行0
   for i in range(3): # 并不等价于C语言的 for(int i=0;i<3;i++)
   	print(i)
   	i += 10 # 内部遍历不影响作为循环i的值，这跟C语言差异很大，请留心
   ```

3. `map`、`filter`、`reduce`等函数式编程函数很重要，能够让你少敲很多代码，特别是`filter`在筛选题中有高的实用性。

4. 特别的，`float()`可用来构造无限值，如`float('inf')`

5. `yield`关键字也很重要，可用来创建生成器，在数列生成、斐波那契查找等用处很大，可以极大的节省开销。[>举例一则<](https://blog.csdn.net/Shenpibaipao/article/details/105521189)，[>教程指南<](https://www.runoob.com/w3cnote/python-yield-used-analysis.html)。需要注意的是，当迭代器函数执行结束时，将自动抛出`StopIteration`异常，仅在 for 循环里，无需处理`StopIteration`异常，循环会正常结束，否则需要使用`except`关键字捕获。

6. 有些时候`try`、`except Exception as e`、`finally`等语句可以直接避免在函数体里进行空值检定，大大减少敲键盘的时间开销：[>举例一则<](https://blog.nowcoder.net/n/3f94b0d63e384045b6056a03680ac6ff)。

7. 善用`set()`来进行列表去重。

8. `format()`函数能方便你的格式化输出，如小数精度控制问题，请考虑[>进行学习<](https://www.runoob.com/python/att-string-format.html)。

9. `input()`和`raw_input()`的区别在于对于python的两个版本(2/3)表现不一致，python 3请使用前者，接收到的数据默认为`str`。

10. 对于非对象类(如`list`)变量，需要用`global`关键词在函数内使用全局变量。

11. `del`关键词会比`list.pop(index)`拥有更高的效率，属于TLE敏感的操作。

12. `list[::-1]`[语法糖](https://blog.csdn.net/Shenpibaipao/article/details/88651528)可以快速对列表进行倒序，在字符串倒序等问题中有奇效；但`list.reverse()`更高效，属于TLE敏感的操作。(另外需要注意：后者是原地倒序)

13. 在python 3中,`zip()`返回一个可迭代对象，需要手动`list()`以进行其它列表操作。

14. 求均值、中位数、众数的API在`statistics`模块中；求众数可以调用`collections.Counter`来实现。

15. python默认的递归栈很有限，有时候会出现C语言能过而python不能过的情况，请[>参考此处<](https://blog.csdn.net/Shenpibaipao/article/details/105758432)解决这个问题——`maximum recursion depth exceeded in comparison`。

## math

### 常量

- `pi`：圆周率 (`3.141592653589793`)
- `inf`：无限大
- `nan`：非数字(Not A Number)
- `e`：自然数
- `tau`：圆周率的两倍，用于计算弧度和角度的换算。（2π×弧度=360°）

### 函数

- `sqrt(x)`：开平方，eg：`math.sqrt(16) = 4.0`
- `floor(x)`：向下取整，eg：`floor(35.7)=35`
- `ceil(x)`：向上取整，eg：`floor(35.1)= 36`
- `trunc(x)`：直接去除数字的小数部分，作用等同floor
- `gcd(a, b)`：求最大公约数，返回值默认与b同号(b非0时)；任一数为0 00时返回0；
- `pow(x, y)`：求幂(x^y^)，返回浮点数，eg：`math.pow(2,3)=8.0 `
- `log(x, y)`：求对数log~y~x，返回浮点数，eg：`math.log(8,2)= 3.0`
- `radians`：将角度转换为弧度
- `modf(x)`：返回浮点数x xx的小数和整数部分，eg：`modf(32.5)=(0.5,32)`
- `exp(x)`：指数函数e^x^，需要注意的是`math.pow(math.e, x)`精度会更高
- `isnan/isinf/isfinite`：常量检测函数，isfinite当检测数为inf和nan时返回False

#### 注意事项

- `math.fabs()`和内建函数中的`abs()`相比，后者支持复数运算。复数的绝对值计算：
  $$
  |a±bj| = \sqrt{a^2+b^2}
  $$

- `divmod(a, b)`与`math.modf(x)`相比，前者返回元组`(a // b, a % b)`，后者拆分小数和整数部分；前者支持复数运算。

- `math.pow()`和内建函数中的`pow()`相比，前者运算为浮点型，后者会保留整形(还可以顺带取模)

- `fractions.gcd()`在Python 3后已被`math.gcd()`取代。

- 最小公倍数：`(a*b) // gcd(a, b)`

## cmath

> 复数运算模块，大部分API与math相同。Python中构建复数的语法示例为：c = 1 + 1j，如：

```python
a, b = 1+1j, 1-1j
print(a, b, a+b) # (1+1j) (1-1j) (2+0j)
```

## statistics

> 数据统计模块，补全了中位数、众数、方差的快速实现。同时支持下文的分数模块。

- `mean()`： 数据的算术平均数（“平均数”）
- `harmonic_mean()` ：数据的调和均值
- `median()`：数据的中位数（中间值）
- `median_low()`：数据的低中位数
- `median_high()`：数据的高中位数
- `mode()`：数据的众数
- `pstdev()`：数据的总体标准差
- `pvariance()`：数据的总体方差
- `stdev()`：数据的样本标准差
- `variance()`：数据的样本方差

## fractions

> 分数运算模块，[>参考此处<](https://docs.python.org/zh-cn/3.7/library/fractions.html)

# 数据结构

## heapq

> 堆模块，构建小顶堆。构建时直接传入一个列表作为堆结构，调用heapify等函数时会直接改变这个堆列表的内部顺序。

> 小顶堆：根节点的值小于等于其左右节点的值，即`a[k] <= a[2*k+1] and a[k] <= a[2*k+2]`
>

- `heapify(heap)`：构建/调整一个堆
- `heappop(heap)`：返回最小数
- `heappush(heap, item)`：向堆内压入一个元素
- `heappushpop(heap, item)`：向堆内压入一个元素后返回最小数
- `heapreplace(heap, item)`：删除堆中最小元素并加入一个元素
- `merge(*iterables)`：合并多个有序列表，并返回有序列表的迭代器(即需要手动list())
- `nlargest(n, iterable, key)`：返回最大的n个数的列表
- `nsmallest(n, iterable, key)`：返回最小的n个数的列表

---

技巧：如果要构建大顶堆，对入堆元素取负即可，如：

```python
heap = [1, 2, 3, 4, 5]
heap = [-i for i in heap]
heapify(heap)
m = -heappop(heap) # 注意取负回来
```

另外需要注意，**堆排序是不稳定的**。

## queue

> 队列模块，Queue其实不是很必要，完全可以用List的内建函数替代；比较有用的是其中的PriorityQueue，常用于解图结构相关的问题，如有向图最短距离等。特殊的，还有内建对象deque作为双向队列，本质是封装了collections.deque，此处不做讲解。

> 需要注意是的，queue模块中提供的是同步的类，因此其入列/出列运算速度是比较慢的，远不及list.insert()和list.pop()。
>

类：

- `Queue(maxsize=0)` ：FIFO 队列。如果maxsize小于等于零，队列尺寸为无限大，下同。
- `LifoQueue(maxsize=0)`： LIFO 队列。
- `PriorityQueue(maxsize=0)`： 优先级队列。

优先级队列：二叉堆，本质上就是一个小顶堆/大顶堆。

通用API：

qsize()：返回队列大小
full()：队列是否满了
put(item, block, timeout)：以同步的方式入列
get(item, block, timeout)：以同步的方式出列
put_nowait(item)：以非同步的方式入列
get_nowait(item)：以非同步的方式出列
优先队列的item应该为以下数据格式：(priority number, data)

8. collections
是Python内建的一个集合模块，提供了许多有用的集合类。该模块较为重要，为本文行文流畅考虑，此处仅做简介索引和用方举例。详细了解API可到：>扩展学习资料<

常用类：

namedtuple：构建一个可命名的tuple，该类型可用isinstance检定
deque：高效实现插入和删除操作双向列表，比list优异，可直接改造成FIFO队列或栈，API与list基本相同
ChainMap：将多个dict串成一个逻辑上的dict(不修改内存)，往往用于优先级查找
Counter： 计数器，大部分情况下速度会更快，但若只统计个别元素，推荐使用list.count()，接受一个字典或字符串
OrderedDict： 有序字典(按key的值升序排序)，常用来做一个FIFO的有序字典
defaultdict： 访问缺失值时会返回一个默认值的字典而不是抛出KeyError，相当好用，其它行为与dict一致，可以看成是一种更健壮的dict
8.1 Counter
该类由于重载了加、减、del等运算，因此可以直接进行减操作，在对字符串进行统计时想当有用。

构造：

Counter()：空构建
Counter(st)：传入一个字符串
Counter(dict)：传入一个字典
Counter(key=v, ...)：传入一些键值对
常用方法：

update(Counter)：
most_common(n)：返回 最多的n个元素的列表
8.2 deque
当只对首位数据进行操作时，双向队列类比list有着更高的效率。其与list相比，用有几乎完全相同的API，只不过pop()不允许按index弹出数据，只能弹出队尾数据，并且多了以下API：

popleft()：与pop()相对，从尾部弹出数据(没有发现存在比pop(0, data)明显的性能优势)
appendleft()：与append()相对，向首部添加数据(没有发现存在比insert(0, data)明显的性能优势)
注意事项：collections.deque比queue.deque更加强大；后者是对前者的封装，作为模块内建对象存在，而前者这是一个类。后者拥有dequeue、enqueue等标准队列操作，但个人更推荐使用前者而不是后者。

函数式编程/编程风格优化
9. functools
高阶函数模块，对于数学题或函数式编程风格优化起到重要作用。

主要方法：

@lru_cache(maxsize=None, typed=False)：LRU缓存，在递归和DP中取maxsize=None用作记忆法进行剪枝。
reduce(function, iterable, [initializer])：累积函数，常用于列表连续求积
其它方法跟装饰器有关，不一一罗列。

10. itertools
本模块实现了一系列 iterator，比起手动for循环，会快很多。

无穷迭代器：

count(start, [step])：步进迭代器，生成序列start, start+step, start+2*step...
cycle(iterable)：循环迭代器，输入迭代器p，生成序列p0, p1, ... plast, p0, p1, ...
repeat(obj [,n])： 重复迭代器，重复无限次或n次，生成序列obj, obj, obj, ...
有限迭代器：

accumulate(iterable, [func])：创建一个迭代器，根据func返回累加和或其他二元函数的累加结果。eg：accumulate([1,2,3,4,5]) --> 1 3 6 10 15
chain：创建一个迭代器，它首先返回第一个可迭代对象中所有元素，接着返回下一个可迭代对象中所有元素，直到耗尽所有可迭代对象中的元素，eg：chain('ABC', 'DEF') --> A B C D E F
compress(data, selectors)：返回 data 中经 selectors 真值测试为 True 的元素，eg：compress('ABCDEF', [1,0,1,0,1,1]) --> A C E F
dropwhile：从首次真值测试失败开始，eg：dropwhile(lambda x: x<5, [1,4,6,4,1]) --> 6 4 1
takewhile：直到首次真值测试失败结束，eg：takewhile(lambda x: x<5, [1,4,6,4,1]) --> 1 4
filterfalse(predicate, iterable)：返回iterable中predicate为False的元素，eg：`filterfalse(lambda x: x%2, range(10)) --> 0 2 4 6 8
groupby(iterable, [key])：迭代器中相邻的重复元素挑出来放在一起，eg：for i, v in itertools.groupby('AABBC'): print(i, list(v)) --> A ['A', 'A'] B ['B', 'B'] C ['C']
islice(iterable, start, stop[, step])：返回从 iterable 里选中的元素，eg：islice('ABCDEFG', 2, None) --> C D E F G
starmap(function, iterable)：星映射迭代器，eg：starmap(pow, [(2,5), (3,2), (10,3)]) --> 32 9 1000
tee(iterable, n)：拆分一个迭代器为n nn个
zip_longest：创建一个迭代器，从每个可迭代对象中收集元素。如果可迭代对象的长度未对齐，将根据fillvalue填充缺失值，eg：zip_longest('ABCD', 'xy', fillvalue='-') --> Ax By C- D-
排列组合迭代器：

product：笛卡尔积，eg：product('ABCD, 2') --> AA AB AC AD BA BB BC BD CA CB CC CD DA DB DC DD
permutations：连续返回由 iterable 元素生成长度为 r 的排列，和combinations有点类似，即返回组合排列解，eg：permutations('ABCD, 2') --> AB AC AD BA BC BD CA CB CD DA DB DC
combinations：返回由输入iterable中元素组成长度为r rr的子序列，eg：combinations('ABCD', 2) --> AB AC AD BC BD CD
注意事项：

accumulate可通过给定一个func来自定义累加过程，例如给定max作为累加器，则统计的是至今为止最大的数，在一些题目中相当好用。
combinations本质上就是就是计算组合数，在一些数学题中相当好用，例如print(len(list(itertools.combinations('ABCD', 2))))可以直接得到C 4 2 = 6 C_4^2=6C 
4
2

 =6；permutations则是返回A 2 2 C 4 2 A_2^2C_4^2A 
2
2

 C 
4
2

 。
专业导向
专业导向的模块除了re以外，一般不怎么用到，只对于某些专业题目，如二进制、文件、时间、加密等。

11. datetime
时间模块，可以直接对日期进行加减等操作，在某些日期问题中非常有用。如二月份的日期加减：

print(datetime.date(2019, 2, 28) + datetime.timedelta(days=1))
# 2019-03-01
1
2
常用类：

date(year, month, day)：日期模型
time(hour, minute, second, microsecond, tzinfo)：时间模型
datetime(...)：日期和时间的结合模型；常用timestamp()可将其转为时间戳
timedelta(days, seconds, microseconds, milliseconds, minutes, hours, weeks)：时间增量，常用total_seconds()可以将其转化为秒。
timezone：时区类
12. calendar
主要用于构建日历，在诸如打印出某年第某月日历的题目时非常有用，如打印2020年第二个月的日历(注意并不是2月1号到2月29号，而是印刷日历的编号，即为1月27日到3月1日【打开你右下角的windows日历自行查查对】)

c = calendar.Calendar(firstweekday=0) # 0:日历印刷的第一天为星期一
for i in c.itermonthdates(2020, 2):
    print(i)
1
2
3
13. struct
struct模块来解决bytes和其他二进制数据类型的转换。常用于处理二进制或字符串题。

>简易入门<
>format-characters

14. re
在这些专业导向的模块中，正则模块则是最重要的模块，能处理大量字符串相关的题目，需要额外学习正则表达式，此处不再赘述，属于必须掌握的模块。请参考>本文档<进行学习。

15. copy
主要用于处理浅层和深层拷贝，在某些需要自定义数据结构的题目中能方便你进行对象拷贝，属于必须掌握的模块。主要只有两个函数：

copy：返回浅层拷贝。
deepcopy：耗时大，返回深层拷贝对象。
16. os.path
在一些路径字符串分析题中非常有用，大部分情况下可以用re模块和str替代。

17. string/str
主要掌握str模块类的以下方法：

strip([chars])：返回原字符串的副本，移除其中的前导和末尾字符；常用于IO
split(sep=None, maxsplit=-1)：返回一个由字符串内单词组成的列表，常用于IO
find(sub, [start], [end])：返回子字符串 sub 在s[start:end]切片内被找到的最小索引
count(sub, [start], [end])：反回子字符串 sub 在 [start, end] 范围内非重叠出现的次数。
center(width, [fillchar])：返回长度为 width 的字符串，原字符串在其正中， 使用指定的 fillchar 填充两边的空位(优先填右)
capitalize()：返回将首字母大写、其余小写的原字符串副本
index(sub, [start], [end])：类似find()，不推荐使用，因为找不到时会触发一个异常
replace(old, new, [count])：替换子串，不过基本都由re.sub()替代该操作
join(iterable)：返回一个由 iterable 中的字符串拼接而成的字符串；常用于IO
lower()/upper()：返回一个副本，将所有字符转为小/大写
lower()/isupper()：判断是否全由小写字母/大写字母组成
isdigit()/isdecimal()/isnumeric()：判断是否全由数字字母组成【区别见下文】
isalnum()/isalpha()：判断是否全由字母和数字组成/判断是否全由字母组成
translate(table)：映射字符串，需要搭配str.maketrans(dict)一起用；eg: print("abc".translate(str.maketrans({"a": "1"})))将会输出1bc
title()：转化为标题形式，仅用于一些针对性的题目
注意事项：

字符串类似一个list，可以进行切片或使用s[::-1]的语法糖进行倒序，但不能s[i]="x"进行修改性赋值(请使用str.replace(...)或将其转为一个list)
isdigit()/isdecimal()/isnumeric()的区别使用场景为：
True	False	Error
isdigit	Unicode数字，byte数字（单字节），全角数字（双字节），罗马数字	汉字数字	/
isdecimal	Unicode数字，，全角数字（双字节）	罗马数字，汉字数字	/
isnumeric	Unicode数字，全角数字（双字节），罗马数字，汉字数字	/	byte数字（单字节）
18. base64
此模块提供了将二进制数据编码为可打印的 ASCII 字符以及将这些编码解码回二进制数据的函数，在某些数据分析题中很有用，但比较冷门，偶尔会遇到，如果掌握了可以节省大量的时间。

19. difflib
此模块提供用于比较序列的类和函数，在算法题中属于冷门模块，在一些用于比较字符串差异的题目中可以进行使用，例如比较 两个字符串序列的前后差异：

c = difflib.ndiff("abcd", "abde")
for i in c:
    print(i)
1
2
3
TLE敏感操作
上文中提到了部分敏感操作，接下来继续总结一些：

x in obj要比obj.find(x)效率高，如str或list查找时。
对list进行扩增，以下三种方式的效率依次增高：for _ in range(j): li.append(x)<li[i:i+j] = [x]*j<li += [x]*j。
del x要比list.pop(index_x)效率高。
list.reverse()要比list[::-1]效率高。
[[0 for i in range(1000)] for j in range(1000)]要比[[0] * 1000 for j in range(1000)]效率高，但不推荐直接开一个特别大的数组，该操作本身非常耗时间。
li += [1, 2, 3]要比li.extend([1, 2, 3])效率高，但在扩增的数据量较少时，候没有绝对优势。
s.remove(x)要比s.pop(s.index(x))或del s[s.index(1)]有性能优势，如果非必要，请直接移除。相对的，还有以下性能比较：if x in s: s.remove(x)>del s[s.index(x)]>s.pop(s.index(x))；总而言之，若对索引不感兴趣，尽量用in关键字做包含性查询、用del关键字移除对象。
————————————————
版权声明：本文为CSDN博主「身披白袍」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/Shenpibaipao/article/details/105873407