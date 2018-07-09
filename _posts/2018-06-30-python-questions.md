---
layout: post
title:  "python基础题目"
date:  2018-06-28 20:00:59 +0800
categories: Learn
tags: python
img: https://www.python.org/static/img/python-logo.png
author: LiuKK
---

# 1. 简述解释型和编译型编程语言?

解释型语言编写的程序不需要编译，在执行的时候，专门有一个解释器能够将VB语言翻译成机器语言，每个语句都是执行的时候才翻译。这样解释型语言每执行一次就要翻译一次，效率比较低。
用编译型语言写的程序执行之前，需要一个专门的编译过程，通过编译系统，把源高级程序编译成为机器语言文件，翻译只做了一次，运行时不需要翻译，所以编译型语言的程序执行效率高，但也不能一概而论，部分解释型语言的解释器通过在运行时动态优化代码，甚至能够使解释型语言的性能超过编译型语言。

# 2. Python解释器种类以及特点
Python是一门解释器语言，代码想运行，必须通过解释器执行，Python存在多种解释器，分别基于不同语言开发，每个解释器有不同的特点，但都能正常运行Python代码，以下是常用的五种Python解释器：

`CPython`

当 从Python官方网站下载并安装好Python2.7后，就直接获得了一个官方版本的解释器：Cpython，这个解释器是用C语言开发的，所以叫 CPython，在命名行下运行python，就是启动CPython解释器，CPython是使用最广的Python解释器。

`IPython`

IPython是基于CPython之上的一个交互式解释器，也就是说，IPython只是在交互方式上有所增强，但是执行Python代码的功能和CPython是完全一样的，好比很多国产浏览器虽然外观不同，但内核其实是调用了IE。

`PyPy`

PyPy是另一个Python解释器，它的目标是执行速度，PyPy采用JIT技术，对Python代码进行动态编译，所以可以显著提高Python代码的执行速度。

`Jython`

Jython是运行在Java平台上的Python解释器，可以直接把Python代码编译成Java字节码执行。

`IronPython`

IronPython和Jython类似，只不过IronPython是运行在微软.Net平台上的Python解释器，可以直接把Python代码编译成.Net的字节码。

在Python的解释器中，使用广泛的是CPython，对于Python的编译，除了可以采用以上解释器进行编译外，技术高超的开发者还可以按照自己的需求自行编写Python解释器来执行Python代码，十分的方便！

# 3. 位和字节的关系

位（bit），数据存储是以“字节”（Byte）为单位，数据传输是以大多是以“位”（bit，又名“比特”）为单位，一个位就代表一个0或1（即二进制），每8个位（bit，简写为b）组成一个字节（Byte，简写为B），是最小一级的信息单位，是计算机信息技术用于计量存储容量的一种计量单位，也表示一些计算机编程语言中的数据类型和语言字符。

# 4. b、B、KB、MB、GB 的关系
1TB=1024GB，
1GB=1024MB；
1MB=1024KB；
1KB=1024B；
1B=8bit

# 5. PEP8 Python 编码规范整理
一 代码编排
1 缩进。4个空格的缩进（编辑器都可以完成此功能），不使用Tap，更不能混合使用Tap和空格。
2 每行最大长度79，换行可以使用反斜杠，最好使用圆括号。换行点要在操作符的后边敲回车。
3 类和top-level函数定义之间空两行；类中的方法定义之间空一行；函数内逻辑无关段落之间空一行；其他地方尽量不要再空行。

二 文档编排
1 模块内容的顺序：模块说明和docstring—import—globals&constants—其他定义。其中import部分，又按标准、三方和自己编写顺序依次排放，之间空一行。
2 不要在一句import中多个库，比如import os, sys不推荐。
3 如果采用from XX import XX引用库，可以省略‘module.’，都是可能出现命名冲突，这时就要采用import XX。

三 空格的使用
总体原则，避免不必要的空格。
1 各种右括号前不要加空格。
2 逗号、冒号、分号前不要加空格。
3 函数的左括号前不要加空格。如Func(1)。
4 序列的左括号前不要加空格。如list[2]。
5 操作符左右各加一个空格，不要为了对齐增加空格。
6 函数默认参数使用的赋值符左右省略空格。
7 不要将多句语句写在同一行，尽管使用‘；’允许。
8 if/for/while语句中，即使执行语句只有一句，也必须另起一行。

四 注释
总体原则，错误的注释不如没有注释。所以当一段代码发生变化时，第一件事就是要修改注释！
注释必须使用英文，最好是完整的句子，首字母大写，句后要有结束符，结束符后跟两个空格，开始下一句。如果是短语，可以省略结束符。
1 块注释，在一段代码前增加的注释。在‘#’后加一空格。段落之间以只有‘#’的行间隔。比如：
```
# Description : Module config.
# 
# Input : None
#
# Output : None
```
2 行注释，在一句代码后加注释。比如：x = x + 1 # Increment x
但是这种方式尽量少使用。
3 避免无谓的注释。

五 文档描述
1 为所有的共有模块、函数、类、方法写docstrings；非共有的没有必要，但是可以写注释（在def的下一行）。
2 如果docstring要换行，参考如下例子,详见PEP 257

"""Return a foobang

Optional plotz says to frobnicate the bizbaz first.

"""

六 命名规范
总体原则，新编代码必须按下面命名风格进行，现有库的编码尽量保持风格。
1 尽量单独使用小写字母‘l’，大写字母‘O’等容易混淆的字母。
2 模块命名尽量短小，使用全部小写的方式，可以使用下划线。
3 包命名尽量短小，使用全部小写的方式，不可以使用下划线。
4 类的命名使用CapWords的方式，模块内部使用的类采用_CapWords的方式。
5 异常命名使用CapWords+Error后缀的方式。
6 全局变量尽量只在模块内有效，类似C语言中的static。实现方法有两种，一是__all__机制;二是前缀一个下划线。
7 函数命名使用全部小写的方式，可以使用下划线。
8 常量命名使用全部大写的方式，可以使用下划线。
9 类的属性（方法和变量）命名使用全部小写的方式，可以使用下划线。
9 类的属性有3种作用域public、non-public和subclass API，可以理解成C++中的public、private、protected，non-public属性前，前缀一条下划线。
11 类的属性若与关键字名字冲突，后缀一下划线，尽量不要使用缩略等其他方式。
12 为避免与子类属性命名冲突，在类的一些属性前，前缀两条下划线。比如：类Foo中声明__a,访问时，只能通过Foo._Foo__a，避免歧义。如果子类也叫Foo，那就无能为力了。
13 类的方法第一个参数必须是self，而静态方法第一个参数必须是cls。
七 编码建议
1 编码中考虑到其他python实现的效率等问题，比如运算符‘+’在CPython（Python）中效率很高，都是Jython中却非常低，所以应该采用.join()的方式。
2 尽可能使用‘is’‘is not’取代‘==’，比如if x is not None 要优于if x。
3 使用基于类的异常，每个模块或包都有自己的异常类，此异常类继承自Exception。
4 异常中不要使用裸露的except，except后跟具体的exceptions。
5 异常中try的代码尽可能少。比如：
```
try:
value = collection[key]
except KeyError:
return key_not_found(key)
else:
return handle_value(value)
```
要优于
```
try:
# Too broad!
return handle_value(collection[key])
except KeyError:
# Will also catch KeyError raised by handle_value()
return key_not_found(key)
```
6 使用startswith() and endswith()代替切片进行序列前缀或后缀的检查。比如
Yes: if foo.startswith(‘bar’):优于
No: if foo[:3] == ‘bar’:
7 使用isinstance()比较对象的类型。比如
Yes: if isinstance(obj, int): 优于
No: if type(obj) is type(1):
8 判断序列空或不空，有如下规则
Yes: if not seq:
if seq:
优于
No: if len(seq)
if not len(seq)
9 字符串不要以空格收尾。
10 二进制数据判断使用 if boolvalue的方式。
# 6. python递归的最大层数
998
# 7. ascii、unicode、utf-8、gbk 区别
最早只有127个字母被编码到计算机里，也就是大小写英文字母、数字和一些符号，这个编码表被称为ASCII编码，比如大写字母A的编码是65，小写字母z的编码是122。
但是要处理中文显然一个字节是不够的，至少需要两个字节，而且还不能和ASCII编码冲突，所以，中国制定了GB2312编码，用来把中文编进去。

你可以想得到的是，全世界有上百种语言，日本把日文编到Shift_JIS里，韩国把韩文编到Euc-kr里，各国有各国的标准，就会不可避免地出现冲突，结果就是，在多语言混合的文本中，显示出来会有乱码。

因此，Unicode应运而生。Unicode把所有语言都统一到一套编码里，这样就不会再有乱码问题了。

Unicode标准也在不断发展，但最常用的是用两个字节表示一个字符（如果要用到非常偏僻的字符，就需要4个字节）。现代操作系统和大多数编程语言都直接支持Unicode。

新的问题又出现了：如果统一成Unicode编码，乱码问题从此消失了。但是，如果你写的文本基本上全部是英文的话，用Unicode编码比ASCII编码需要多一倍的存储空间，在存储和传输上就十分不划算。

所以，本着节约的精神，又出现了把Unicode编码转化为“可变长编码”的UTF-8编码。UTF-8编码把一个Unicode字符根据不同的数字大小编码成1-6个字节，常用的英文字母被编码成1个字节，汉字通常是3个字节，只有很生僻的字符才会被编码成4-6个字节。如果你要传输的文本包含大量英文字符，用UTF-8编码就能节省空间。

UTF-8编码有一个额外的好处，就是ASCII编码实际上可以被看成是UTF-8编码的一部分，所以，大量只支持ASCII编码的历史遗留软件可以在UTF-8编码下继续工作。
GBK是只用来编码汉字的，GBK全称《汉字内码扩展规范》，使用双字节编码。

# 8. 字节码和机器码的区别
什么是机器码
机器码

机器码(machine code)，学名机器语言指令，有时也被称为原生码（Native Code），是电脑的CPU可直接解读的数据。

通常意义上来理解的话，机器码就是计算机可以直接执行，并且执行速度最快的代码。

用机器语言编写程序，编程人员要首先熟记所用计算机的全部指令代码和代码的涵义。手编程序时，程序员得自己处理每条指令和每一数据的存储分配和输入输出，还得记住编程过程中每步所使用的工作单元处在何种状态。这是一件十分繁琐的工作，编写程序花费的时间往往是实际运行时间的几十倍或几百倍。而且，编出的程序全是些0和1的指令代码，直观性差，还容易出错。现在，除了计算机生产厂家的专业人员外，绝大多数的程序员已经不再去学习机器语言了。

    机器语言是微处理器理解和使用的，用于控制它的操作二进制代码。
    8086到Pentium的机器语言指令长度可以从1字节到13字节。
    尽管机器语言好像是很复杂的，然而它是有规律的。
    存在着多至100000种机器语言的指令。这意味着不能把这些种类全部列出来。

总结：机器码是电脑CPU直接读取运行的机器指令，运行速度最快，但是非常晦涩难懂，也比较难编写，一般从业人员接触不到。
什么是字节码
字节码

字节码（Bytecode）是一种包含执行程序、由一序列 op 代码/数据对 组成的二进制文件。字节码是一种中间码，它比机器码更抽象，需要直译器转译后才能成为机器码的中间代码。

通常情况下它是已经经过编译，但与特定机器码无关。字节码通常不像源码一样可以让人阅读，而是编码后的数值常量、引用、指令等构成的序列。

字节码主要为了实现特定软件运行和软件环境、与硬件环境无关。字节码的实现方式是通过编译器和虚拟机器。编译器将源码编译成字节码，特定平台上的虚拟机器将字节码转译为可以直接执行的指令。字节码的典型应用为Java bytecode。

字节码在运行时通过JVM（JAVA虚拟机）做一次转换生成机器指令，因此能够更好的跨平台运行。

总结：字节码是一种中间状态（中间码）的二进制代码（文件）。需要直译器转译后才能成为机器码。

# 9. Python中的*arg和**kwarg

一个简单的函数

首先我们可以定一个简单的函数, 函数内部只考虑required_arg这一个形参(位置参数)
```
def exmaple(required_arg):
    print required_arg

exmaple("Hello, World!")

>> Hello, World!
```
那么，如果我们调用函数式传入了不止一个位置参数会出现什么情况？当然是会报错！
```
exmaple("Hello, World!", "another string")

>> TypeError: exmaple() takes exactly 1 argument (2 given)
```
定义函数时，使用*arg和**kwarg

*arg和**kwarg 可以帮助我们处理上面这种情况，允许我们在调用函数的时候传入多个实参
```
def exmaple2(required_arg, *arg, **kwarg):
    if arg:
        print "arg: ", arg

    if kwarg:
        print "kwarg: ", kwarg

exmaple2("Hi", 1, 2, 3, keyword1 = "bar", keyword2 = "foo")

>> arg:  (1, 2, 3)
>> kwarg:  {'keyword2': 'foo', 'keyword1': 'bar'}
```
从上面的例子可以看到，当我传入了更多实参的时候

    *arg会把多出来的位置参数转化为tuple
    **kwarg会把关键字参数转化为dict

再举个例子，一个不设定参数个数的加法函数
```
def sum(*arg):
    res = 0
    for e in arg:
        res += e
    return res

print sum(1, 2, 3, 4)
print sum(1, 1)
>> 10
>> 2
```
当然，如果想控制关键字参数，可以单独使用一个*，作为特殊分隔符号。限于Python 3，下面例子中限定了只能有两个关键字参数，而且参数名为keyword1和keyword2
```
def person(required_arg, *, keyword1, keyword2):
    print(required_arg, keyword1, keyword2)

person("Hi", keyword1="bar", keyword2="foo")
>> Hi bar foo
```
如果不传入参数名keyword1和keyword2会报错，因为都会看做位置参数！
```
person("Hi", "bar", "foo")

>> TypeError: person() takes 1 positional argument but 3 were given
```
调用函数时使用*arg和**kwarg

直接上例子，跟上面的情况十分类似。反向思维。
```
def sum(a, b, c):
    return a + b + c

a = [1, 2, 3]

# the * unpack list a 
print sum(*a)
>> 6
```
```
def sum(a, b, c):
    return a + b + c

a = {'a': 1, 'b': 2, 'c': 3}

# the ** unpack dict a
print sum(**a)
>> 6
```

# 10. 在python 中is和= = 的区别

Python中的对象包含三要素：id、type、value
其中id用来唯一标识一个对象，type标识对象的类型，value是对象的值
is判断的是a对象是否就是b对象，是通过id来判断的
==判断的是a对象的值是否和b对象的值相等，是通过value来判断的

# 11.一行代码实现9*9乘法表
```
print "\n".join("\t".join(["%s*%s=%s" %(x,y,x*y) for y in range(1, x+1)]) for x in range(1, 10))  
```

# 12. re的match和search区别
re.match()从开头开始匹配string。
re.search()从anywhere 来匹配string。

# 13. 什么是正则的贪婪匹配
　　贪婪匹配：正则表达式一般趋向于最大长度匹配，也就是所谓的贪婪匹配。如上面使用模式p匹配字符串str，结果就是匹配到：abcaxc(ab*c)。

　　非贪婪匹配：就是匹配到结果就好，就少的匹配字符。如上面使用模式p匹配字符串str，结果就是匹配到：abc(ab*c)。
　　默认是贪婪模式；在量词后面直接加上一个问号？就是非贪婪模式。
　　
# 14. 静态方法和类方法区别  
实例方法，类方法，静态方法都可以通过实例或者类调用，只不过实例方法通过类调用时需要传递实例的引用（python 3可以传递任意对象，其他版本会报错）。

三种方法从不同层次上来对方法进行了描述：实例方法针对的是实例，类方法针对的是类，他们都可以继承和重新定义，而静态方法则不能继承，可以认为是全局函数。

# 15. json序列化时，可以处理的数据类型有哪些？如何定制支持datetime类型？
```
import json
from json import JSONEncoder
from datetime import datetime
class ComplexEncoder(JSONEncoder):
    def default(self, obj):
        if isinstance(obj, datetime):
            return obj.strftime('%Y-%m-%d %H:%M:%S')
        else:
            return super(ComplexEncoder,self).default(obj)
d = { 'name':'alex','data':datetime.now()}
print(json.dumps(d,cls=ComplexEncoder))
```

json序列化时遇到中文会默认转换成unicode  ，如何让他保留中文形式
```
import json
a=json.dumps({"ddf":"你好"},ensure_ascii=False)
print(a) #{"ddf": "你好"}
```

# 16. 简述 yield和yield from关键字。

说明：yield from iterable本质上等于for item in iterable: yield item的缩写版   
 






