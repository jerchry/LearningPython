# LearningPython
Python开发环境搭建
{
Windows下：官网下载安装；环境变量配置
Linux下：ipython的安装
$ sudo apt install ipython

Python的文件类型
字节码文件：.pyc，.pyo

Eclipse+PyDev的安装
}

Python中的数据类型：
整数/浮点数/字符串/布尔值/空值（None）

注释：#
raw字符串与多行字符串

Python中Unicode字符串

如果中文字符串在Python环境下遇到 UnicodeDecodeError，这是因为.py文件保存的格式有问题。可以在第一行添加注释
# -*- coding: utf-8 -*-

Python把0、空字符串''和None看成 False，其他数值和非空字符串都看成 True

list：[]
添加元素：append(), insert(0,"")
删除元素：pop()

tuple：()
和list类似，一旦创建完毕，就不能修改了
单元素tuple要多加一个逗号
tuple所谓的“不变”是说，tuple的每个元素，指向永远不变。

具有相同缩进的代码被视为代码块
缩进请严格按照Python的习惯写法：4个空格，不要使用Tab，更不要混合Tab和空格，否则很容易造成因为缩进引起的语法错误。
如果你在Python交互环境下敲代码，还要特别留意缩进，并且退出缩进需要多敲一行回车：

for in循环

while循环

break

continue

dict：{key:value,...}
len() 函数可以计算任意集合的大小
通过 key 访问 dict 的value，只要 key 存在，dict就返回对应的value。如果key不存在，会直接报错：KeyError。
避免 KeyError :
一是先判断一下 key 是否存在，用 in 操作符：
二是使用dict本身提供的一个 get 方法，在Key不存在的时候，返回None：

dict的第一个特点是查找速度快，无论dict有10个元素还是10万个元素，查找速度都一样。而list的查找速度随着元素增加而逐渐下降。
dict的缺点是占用内存大，还会浪费很多内容，list正好相反，占用内存小，但是查找速度慢。
dict的第二个特点就是存储的key-value序对是没有顺序的！
dict的第三个特点是作为 key 的元素必须不可变，Python的基本类型如字符串、整数、浮点数都是不可变的，都可以作为 key。但是list是可变的，就不能作为 key。

set 持有一系列元素，这一点和 list 很像，但是set的元素没有重复，而且是无序的，这点和 dict 的 key很像。
添加：add()  删除remove()

Python内置函数：
abs(x)求绝对值
cmp(x,y)比较函数
int(x)数据类型转换函数
str(123)

在Python中，定义一个函数要使用 def 语句，依次写出函数名、括号、括号中的参数和冒号:，然后，在缩进块中编写函数体，函数的返回值用 return 语句返回。
请注意，函数体内部的语句在执行时，一旦执行到return时，函数就执行完毕，并将结果返回。如果没有return语句，函数执行完毕后也会返回结果，只是结果为 None。
return None可以简写为return。

Python的函数返回多值其实就是返回一个tuple，但写起来更方便。

使用递归函数需要注意防止栈溢出。在计算机中，函数调用是通过栈（stack）这种数据结构实现的，每当进入一个函数调用，栈就会加一层栈帧，每当函数返回，栈就会减一层栈帧。由于栈的大小不是无限的，所以，递归调用的次数过多，会导致栈溢出。可以试试计算 fact(10000)。

可变参数的名字前面有个 * 号
可变参数也不是很神秘，Python解释器会把传入的一组参数组装成一个tuple传递给可变参数，因此，在函数内部，直接把变量 args 看成一个 tuple 就好了。

经常取指定索引范围的操作，用循环十分繁琐，因此，Python提供了切片（Slice）操作符，能大大简化这种操作。
取前3个元素: L[0:3]
如果第一个索引是0，还可以省略： L[:3]
只用一个 : ，表示从头到尾：因此，L[:]实际上复制出了一个新list。
切片操作还可以指定第三个参数：L[::2]第三个参数表示每N个取一个，上面的 L[::2] 会每两个元素取出一个来，也就是隔一个取一个。

 集合是指包含一组元素的数据结构，我们已经介绍的包括：
1. 有序集合：list，tuple，str和unicode；
2. 无序集合：set
3. 无序集合并且具有 key-value 对：dict

索引迭代也不是真的按索引访问，而是由 enumerate() 函数自动把每个元素变成 (index, element) 这样的tuple，再迭代，就同时获得了索引和元素本身。

迭代dict的value:dict 对象有一个 values() 方法，这个方法把dict转换成一个包含所有value的list，这样，我们迭代的就是 dict的每一个 value
dict除了values()方法外，还有一个 itervalues() 方法，用 itervalues() 方法替代 values() 方法，迭代效果完全一样
那这两个方法有何不同之处呢？

1. values() 方法实际上把一个 dict 转换成了包含 value 的list。

2. 但是 itervalues() 方法不会转换，它会在迭代过程中依次从 dict 中取出 value，所以 itervalues() 方法比 values() 方法节省了生成 list 所需的内存。

3. 打印 itervalues() 发现它返回一个 <dictionary-valueiterator> 对象，这说明在Python中，for 循环可作用的迭代对象远不止 list，tuple，str，unicode，dict等，任何可迭代对象都可以作用于for循环，而内部如何迭代我们通常并不用关心。

迭代dict的key和value:
items() 方法把dict对象转换成了包含tuple的list，我们对这个list进行迭代，可以同时获得key和value.和 values() 有一个 itervalues() 类似， items() 也有一个对应的 iteritems()，iteritems() 不把dict转换成list，而是在迭代过程中不断给出 tuple，所以， iteritems() 不占用额外的内存。

列表生成式？生成列表，复杂表达式，条件过滤，多层表达式
要生成list [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]，我们可以用range(1, 11);
但如果要生成[1x1, 2x2, 3x3, ..., 10x10],[x * x for x in range(1, 11)]
这种写法就是Python特有的列表生成式。利用列表生成式，可以以非常简洁的代码生成 list。

字符串可以通过 % 进行格式化，用指定的参数替代 %s。字符串的join()方法可以把一个 list 拼接成一个字符串。

函数式编程
map()
reduce()
filter()
sorted()函数可对list进行排序

python中返回函数

关键字lambda 表示匿名函数
匿名函数有个限制，就是只能有一个表达式，不写return，返回值就是该表达式的结果。

装饰器：
$ Python内置的@语法就是为了简化装饰器的调用
作用：
1.极大的简化代码，避免每个函数编写重复性代码
打印日志：@log
检测性能：@performance
数据库事务：@transaction
URL路由：@post('/register')

functools.partial可以把一个参数多的函数变成一个参数少的新函数，少的参数需要在创建时指定默认值，这样，新函数调用的难度就降低了。

包下面有个：_init_.py

如果我们只希望导入用到的math模块的某几个函数，而不是所有函数，可以用下面的语句：from math import pow, sin, log

动态导入：
try:
    from cStringIO import StringIO
except ImportError:
    from StringIO import StringIO
    
try 的作用是捕获错误，并在捕获到指定错误时执行 except 语句。
利用import ... as ...，还可以动态导入不同名称的模块。

Python 2.6/2.7提供了json 模块，但Python 2.5以及更早版本没有json模块，不过可以安装一个simplejson模块，这两个模块提供的函数签名和功能都一模一样。
导入json 模块的代码，能在Python 2.5/2.6/2.7都正常运行。
try:
    import json
except ImportError:
    import simplejson as json
print json.dumps({'python':2.7})

要在Python 2.7中引入3.x的除法规则，导入__future__的division

安装第三方模块
Python提供的模块管理工具
1.easy_install
2.pip（推荐，已内置到Python2.7.9）

类名以大写字母开头，紧接着是(object)，表示该类是从哪个类继承下来的。
python中初始化实例属性，可以为Person类添加一个特殊的__init__()方法，当创建实例时，__init__()方法被自动调用
Python对属性权限的控制是通过属性名来实现的，如果一个属性由双下划线开头(__)，该属性就无法被外部访问。
但是，如果一个属性以"__xxx__"的形式定义，那它又可以被外部访问了，以"__xxx__"定义的属性在Python的类中被称为特殊属性，有很多预定义的特殊属性可以使用，通常我们不要把普通属性用"__xxx__"定义。
以单下划线开头的属性"_xxx"虽然也可以被外部访问，但是，按照习惯，他们不应该被外部访问。

python中创建类属性
python中类属性和实例属性名字冲突怎么办，当实例属性和类属性重名时，实例属性优先级高，它将屏蔽掉对类属性的访问。
可见，千万不要在实例上修改类属性，它实际上并没有修改类属性，而是给实例绑定了一个实例属性。

python中定义实例方法
实例的方法就是在类中定义的函数，它的第一个参数永远是 self，指向调用该方法的实例本身，其他参数和一个普通函数是完全一样的

Python中方法也是属性
Python中定义类方法

函数isinstance()可以判断一个变量的类型，既可以用在Python内置的数据类型如str、list、dict，也可以用在我们自定义的类，它们本质上都是数据类型。

