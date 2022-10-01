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

- `Queue(maxsize=0)` ：FIFO 队列。如果maxsize小于等于零，队列尺寸为无限大，下同。
- `LifoQueue(maxsize=0)`： LIFO 队列。
- `PriorityQueue(maxsize=0)`： 优先级队列。

优先级队列：二叉堆，本质上就是一个小顶堆/大顶堆。

通用API：

- qsize()：返回队列大小
- full()：队列是否满了
- put(item, block, timeout)：以同步的方式入列
- get(item, block, timeout)：以同步的方式出列
- put_nowait(item)：以非同步的方式入列
- get_nowait(item)：以非同步的方式出列
- 优先队列的item应该为以下数据格式：(priority number, data)

## collections

​		是Python内建的一个集合模块，提供了许多有用的集合类。该模块较为重要，为本文行文流畅考虑，此处仅做简介索引和用方举例。

- namedtuple：构建一个可命名的tuple，该类型可用isinstance检定
- deque：高效实现插入和删除操作双向列表，比list优异，可直接改造成FIFO队列或栈，API与list基本相同
- ChainMap：将多个dict串成一个逻辑上的dict(不修改内存)，往往用于优先级查找
- Counter： 计数器，大部分情况下速度会更快，但若只统计个别元素，推荐使用list.count()，接受一个字典或字符串
- OrderedDict： 有序字典(按key的值升序排序)，常用来做一个FIFO的有序字典
- defaultdict： 访问缺失值时会返回一个默认值的字典而不是抛出KeyError，相当好用，其它行为与dict一致，可以看成是一种更健壮的dict

