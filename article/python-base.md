### 名字和对象   name = object
    名字是以字母数字下划线组成，但名字不能以数字开头，区分大小写。
    “=” 作用就是赋值，给对象一个名字后就可以通过这个名来调用这个对象。
    一个名字名字对应一个对象，后创建的对象会覆盖掉先创建的对象。
    关键字del用来删除对象，名字被删除这个对象也就被删除了

### 单行注释  三引号多行注释

### 类型与类
```python
'''
通过内置函数type()查看对象类型
基本数据类型：
数字类型: int ,float,bool complex
字符串类型：str ,(bytes)
列表：list
元组：tuple
字典：dict
集合：set
不同类型的对象有不同的属性和方法
类型也是一个类，通过关键字class创建我们自己的类，定义这个类的属性和方法。
'''
a = 12
b = "python"
c = [1,2,3,4]
d = 4,5,6
print(d)

e = {'a':1,'b':2}
f = {2,3,4}
#print(a,b,c,d)
class Fruits:
    def __init__(self,name):
        self.name = name
    def eat(self):
        return 'lallalla'
fr1 = Fruits('apple')
```

### 关键字
```python
'''
关键字是在python中有特殊作用的单词
在idle里面关键是以橘色显示
导入keyword模块，可以查看所有的关键字
'''
import keyword
print(keyword.kwlist)
```


### 流程
```python
#在python中语句都是从上往下执行的，函数是先创建好了调用时才会执行

def fun():
    a = 'xxxx'
    print(a,b)
    return 'hahahhahah'

print(a)
print(fun())
print(33333)
```

### 作用域
    不同空间的相同名字表示的是不同的对象
    这个函数里面的a和外面的定义的a = 12是存在于不同作用域的两个对象

### 异常
    看懂并知道怎么解决报错


### 模块及包
    内置模块  自定义模块

## 基本数据类型

### 数字类型
    整型 int
    浮点型 float
    布尔型 bool:  True==1、False==0
    复数类型 complex
    算术运算符 +  -  * /  //  %  **
    赋值运算符 +=     -=    *=    /=    //=     %=     **=
    内置函数max(),min()求最大值最小值
    import decimal


### 序列类型
```python
'''
#字符串str、列表list、元组tuple
#序列的创建，类型转换
#字符串类型的创建：单引号或者是双引号、三引号，但一定是成对出现
#列表的创建：[] 中括号，元素之间用逗号隔开
#元组的创建：（）小括号，或者之间逗号隔开各项
'''
ss = 'hello world'
list1 = [1,3,5,7,9]
tp = 1,2,3,'a'
```

### 类型转换
    #内置函数len()求长度
    #序列类型的特点：序列中的每个元素都有字符编号，也称之为索引
    #每个元素都有各自的索引值，有正向索引也有反向索引，
    #正向索引就是元素的索引值从左到右默认从0开始
    #序列的通用操作：
    #通过索引来进行取值、切片

    #相加：同类型才能相加  +
    #重复：序列*重复次数
    #检查成员：in , not in判断元素是否在序列中



### 列表的方法及属性
```python
'''
  L.append(obj) 在列表末尾添加新的对象。
  L.clear() 清空整个列表。
  L.copy() 复制列表，和L[:]的复制方式一样属于浅复制。
  L.count(obj) 统计某个元素在列表中出现的次数。
  L.extend(seq) 用新列表扩展原来的列表。
  L.index(obj) 从列表中找某个值第一个匹配项的索引位置。
  L.insert(index,obj) 插入元素，可以指定位置。
  L.pop(obj=list[-1]) 出栈，可以指定位置。
  L.remove(obj) 移除指定元素从左边开始的第一个。
  L.reverse() 反向列表中元素。
  L.sort() 对原列表进行排序。
'''
ls = [3,1,6,7,5,4]
ls.append(12)
ls.reverse ()
print(ls)
```

### 可变对象和不可变对象
    # 可变对象： 列表，字典，集合
    # 不可变对象 ： 字符串，元祖， 数字类型

### 基本数据类型
    #元组 tuple
    '''
    元组的特点：元组是\n不可变对象
    元组的属性及方法：
      .count（obj）统计某个元素在元组中出现的次数
    .index（obj）从列表中找某个值第一个匹配项的索引位置
    '''

### 集合set
    '''
    集合的创建：{}，set([])
    集合的特点：无序，元素不重复
    集合的运算：
      & 交集， |并集， -差集 
      成员判断 in、not in
    集合的属性及方法：
     s.add(x)     添加单个元素
     s.update()   添加多个元素
     s.remove()   移除元素
     s.clear()    清空集合
    '''

### 字典
    '''
    字典的创建：{key:value}    (大括号创建字典的键时要加引号)
                dict(key=value) （括号里赋值方式，名字=对象，不要引号）
    字典里的键和值用‘：’隔开，一对键和值组成一个项，项和项之间用‘，’隔开

    字典的特点：
    1.字典中的元素是无序的
    2.不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住

    3.键必须不可变，所以可以用数字，字符串或元组充当，所以用列表就不行
    '''
    #创建字典：
    #dict1 = {'name':'rose','age':18,'gender':'female'}
    #访问字典中的值：
    #dict1['name']
    '''
    字典添加和修改：

    新值所要对应的键名如果存在，就是修改操作，如果不存在就相当于添加操作
    '''
    # 修改
    #dict1['name'] = 'taka'
    # 添加
    #dict1['class'] = 10
    #in 、not in  判断键在不在字典中，在则返回True 
    #字典的属性及方法：
    '''
     .update({ })  在字典中添加多个项        
     .items()      返回字典的各个项         
     .keys()       返回字典的键      
     .values()     返回字典的值	
     .get(k)       如果键k在，返回键k的值，不存在则返回None
     .get(k,x)     如果键k在，返回键k的值，不存在则返回x
     .pop(k)       返回并移除键k所对应的元素，不存在则抛出异常	
     .pop(k,x)     返回并移除键k所对应的元素，不存在则返回x
    '''
    #字典的特性总结：
    '''
    不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住。
    键必须不可变，所以可以用数字，字符串或元组充当，所以用列表就不行。
    '''

### 运算符：
    '''
    算术运算符：+ ，- ， *， /， %， **，//
    赋值运算符：= ，+=，-=， *=，/=，%=， **=

    比较运算符：==，!=， >， <， >=，<=
    成员运算符：in , not in
    身份运算符：is , is not
         判断两个名字是否指向同一个对象，当id相同时返回True(==比较运算是判断的值)
    逻辑运算符：and，or，not，优先级 not>and>or
         and(与) 两个条件都满足时才返回True
         or(或)  有一个条件满足了就返回True
         not(非) 取反
    '''
    #a = int(input())
    #运算符优先级
    
### 练习：
```python
'''
一、已知字典ainfo = {'name':'lily','age':20}
    1.加入两项使得输出的结果：
    ainfo = {'name':'lily','age':20,'gender':'female','class':10}
    2.访问字典中的所有项，访问字典的键，访问字典中的值
二、将这三项内容创建字典,按下面规则添加到同一个对象中:
(name = 'lily',age= 20,gender = 'female',class = 10)
(name ='jack',age= 25,gender ='male',class =10)
(name ='jane',age= 19,gender ='female',class =10)
1.将这三项内容创建的三个字典放到一个列表里。
[{},{}]
2.将这三项内容创建的三个字典放到一个字典里，要求字典以个人姓名为键，
其他信息组成的字典为姓名这个键所对应的值。（字典里面嵌套字典）{'lily':{},'jack':{}}
例如info = {'lily'：{'age':20,'gender':'female','Class':10}}
  
'''
'''
ainfo = {'name':'lily','age':20}
ainfo.update({'gender':'female','class':10})
print(ainfo)
print(ainfo.items())
print(ainfo.keys())
print(ainfo.values())

a1 = dict(name = 'lily',age= 20,gender = 'female',Class = 10)
a2 = dict(name ='jack',age= 25,gender ='male',Class =10)
a3 = dict(name ='jane',age= 19,gender ='female',Class =10)
b = [a1,a2,a3]
print(b)
c = {}
c[a1.pop('name')] = a1
c[a2.pop('name')] = a2
c[a3.pop('name')] = a3
print(c)
'''
'''
a1 = {'name':'lily','age':20,'gender':'female','class':10}
a2 = {'name':'jack','age':25,'gender':'male','class':10}
a3 = {'name':'jane','age':19,'gender':'female','class':10}

lily = a1['name']
jack = a2['name']
jane = a3['name']
a1.pop('name')
a2.pop('name')
a3.pop('name')

b={lily:a1,jack:a2,jane:a3}

'''
```

### 控制流程
```python
# if 判断语句
'''
a = 12
if a>0:
    print('a大于0')
if a<5:
    print('a大于5')
else:
    print('哈哈哈')

基本形式：
if <条件判断1>:
    <执行1>
elif <条件判断2>:
    <执行2>
elif <条件判断3>:
    <执行3>
else:
    <执行4>
'''
'''
if语句
注意事项：
1.判断条件的表达式的值一般为布尔型的值，当值为True就执行里面的语句块。
  一般是使用比较运算符或者成员运算符。
2.条件表达式后面接的“:”是语法的一部分不能少。
  有了“:”号后，满足条件时要的执行语句以缩进后的形式写在下面。
3.if，elif是写分支条件，当前面的if和elif不满足时就执行else里面的语句。
  可以有零到多个elif，else是可选的。
4.语句是从上往下执行的，当前面有条件已经满足了，那么直接执行里面的语句。
  后面的条件判断不再执行。

b = 'python'
if b.isupper():
    print('hahahh')
'''
'''
import random
a = random.randint(1,10)
n = 0

for i in range(3):
    num =input('请输入一个数：')
    if num.isdigit():
        num = int(num)
        if num == a:
            print('猜对了')
            break
        elif num> a:
            print('大了')
        else:
            print('小了')
    else:
        print('输入有误!')
        continue
    #print('你还有%d次机会' % (3-n))

else:
    print('你的机会用完了')

print('这个数是' , a )
'''

### 循环
#while循环
#break跳出整个循环，并且不会执行else里面的语句
#continue 跳出本次循环
#else
#pass

#for 循环，for迭代
#range() range(0,100,2)


# 练习
# 写个完整的猜字游戏
# 分数等级测试，可以循环测试的。
'''
 写一个程序用来判定分数的等级，总分为100分，
 90以上为等级A，大于等于80小于90为等级B，
 大于等于60小于80为等级C，小于60分为等级D，
 输入的分数不在0~100中时显示输入有误。
'''
'''
import random
m = 100
n = 7
print('您拥有100枚金币，达到1000枚时可获宝物一件！')
print('您有7次机会！')
while n > 0:
    a = '飞雪连天射白鹿'
    b = a[random.randint(0,len(a)-1)]
    c = input("请输入'飞雪连天射白鹿'中的一个字：")
    if c == b:
        m += m*4
        print('您猜对了，金币数量*5！')
        print('您现在拥有%s枚金币！'%m)
        if m >= 1000:
            print('祝贺您通关，获得倚天剑！')
            break
    else:
        m -= 20
        if m > 0:
            print('这个字是%s，您猜错了，扣除20枚金币！'%b)
            print('您现在拥有%s枚金币！'%m)
        else:
            print('您没有金币了，欢迎下次光临！')
            break
    n -= 1
    if n == 0:
        print('您没有机会了，欢迎下次光临！')
    else:
        print('您还有%d次机会！'%n)
'''

'''
import random
m = 100
n = 7
print('您拥有100枚金币，达到1000枚时可获宝物一件！')
print('您有7次机会！')
while n > 0:
    a = '飞雪连天射白鹿'
    b = a[random.randint(0,len(a)-1)]
    c = input("请输入'飞雪连天射白鹿'中的一个字：")
    if c == b:
        m += m*4
        print('您猜对了，金币数量*5！')
        print('您现在拥有%s枚金币！'%m)
        if m >= 1000:
            print('祝贺您通关，获得倚天剑！')
            break
    #find,通过values获得keys，但输入超出范围的values返回-1；
    #用index，输入超出范围的values会报错；
    elif abs(a.find(b)-a.find(c)) == 1 and a.find(c) >= 0:
        print('你差点就猜中了，这个字是%s！'%b)
    else:
        m -= 20
        if m > 0:
            print(a.find(b))
            print('这个字是%s，您猜错了，扣除20枚金币！'%b)
            print('您现在拥有%s枚金币！'%m)
        else:
            print('您没有金币了，欢迎下次光临！')
            break
    n -= 1
    if n == 0:
        print('您没有机会了，欢迎下次光临！')
    else:
        print('您还有%d次机会！'%n)

'''

# 分数等级测试
while True:
    print('想停止测试请输入：T')
    a = input('请输入分数：')
    _a = a.replace('.','',1)
    if _a.isdigit():
        a = float(a)
        if a < 0 or a > 100:
            print('输入有误。')
        elif a >= 90:
            print('等级A')
        elif a >= 80 and a < 90:
            print('等级B')
        elif a >= 60 and a < 80:
            print('等级C')
        else:
            print('等级D')
    elif a == 'T':
        break
    else:
        print('请输入整数')


'''
import random
a = random.randint(1,10)
n = 3
while n > 0:
    if n == 3:
        print('猜数字，你有3次机会！')
    num = input('请输入数字：')
    if num.isdigit():
        num = int(num)
        if num > a:
            print('大了')
        elif num < a:
            print('小了')
        else:
            print('你猜对了！')
            break
    n = n - 1
    if n == 0:
        print('这个数是%d'%a)
        print('Game Over!')
    else:
        print('你还有%d次机会！'%n)
'''
```

### 控制流
```python
# while循环
'''
注意：普通应用里，while一定要给一个结束条件，否则就是传说中的死循环
1.while 后面设置退出循环的条件，
         条件不满时退出循环
2.while 后面接值一直为真的条件
        循环体里面通过break来打破这个死循环
'''
# for 循环：
'''
基本形式：
for item in iterable:
    循环语句

1.for循环又叫for迭代，可迭代的对象有：列表、元组、字符串、字典等。
2.for语句迭代出里面的每一项元素，当元素取完了循环也就结束了。
3.break和continue的用法与while 语句是一样的
'''
'''
循环控制语句总结：
break 
用来终止循环，当循环条件还为真或者序列还没被迭代完，遇到break也会停止循环
continue
用来跳过当次循环的剩余语句，继续执行下一轮的循环
pass 
用来占位，是空语句，没有任何操作，可以保持程序结构的完整。
'''

# 用循环语句写出0~100之间的偶数
x = []
n = 0
while n<101:
    x.append(n)
    n += 2
    
y = []
for i in range(101):
    if i%2 == 0:
        y.append(i)

# 计算100以内的所有整数和

s = 0
for i in range(101):
    s += i
    
# 打印出九九乘法表
'''
# i x j = k = i*j
for i in range(1,10):
    for j in range(1,i+1):
        print('%s x %s = %2s '%(j,i,i*j),end='')
    print('aaaa')
'''
#  i = 1
#  i = 2  j  (1,3)
#  i = 3  j   (1,2,3)

# 生成一个100以内能被7整除的列表

def list_7():
    ll = []
    for i in range(101):
        if i % 7 ==0:
            ll.append(i)
    return ll
```

### 函数
    # 函数的定义，函数的调用

### 练习
```python
'''
按下面的要求写出两个求和函数。
sum
1.参数为一个列表或元组类型，求里面所有元素的和。
2.参数的个数不限，求所有参数的和。

3.一个整数，它加上100和加上268后都是一个完全平方数，请问该数是多少？
注：一个数如果是另一个整数的完全平方，我们称这个数是完全平方数
  例如：1，4，9，16，25，36，49·····
  x +100 =y*y  x+268=z*z

'''

'''
#0~100之间的偶数:
a = []
for i in range(101):
    if i % 2 == 0:
        a.append(i)
print(a)

a = []
n = 0
while n < 101:
    a.append(n)
    n += 2
print(a)

print(list(range(0,101,2)))


#计算100以内的所有整数和
n = 0
for i in range(101):
    n += i
print(n)

print(sum(range(101)))


#生成一个100以内能被7整除的列表
def list_7():
    a = []
    for i in range(101):
        if i % 7 == 0:
            a.append(i)
    return a
print(list_7())
'''

'''
def fun1(x,y,z):
    print(x)
    print(y)
    print(z)

tp = 5,6,7
fun1(*tp)
d = {'z':9,'y':3,'x':4}
fun1(**d)
'''
'''
def fun(a,b=2,*c,**d):
    print(a,b,c,d)

fun(1)
fun('a','b','c','d')
fun('a',x='b',y='c',z='d')
'''

'''
#打印出九九乘法表
for i in range(10):
    for j in range(1,i+1):
        print('%d x %d = %2d'%(j,i,j*i),end='  ')
    print()
'''



### 练习1
a = [1,4,3,8,5]
b = 2,6,4,9,3
def sum_1(arg):
    n = 0
    for i in arg:
        n += i
    return n
print(sum_1(a))
print(sum_1(b))

### 练习2
def sum_2(*arg):
    n = 0
    for i in arg:
        n += i
    return n
print(sum_2(5,7,7,3,9))
'''
'''
### 练习3
for x in range(301):
    for y in range(301):
        for z in range(301):
            if x+100 == y*y:
                if x+268 == z*z:
                    print(x,y,z)
```

### 内置函数
    '''
    len 求长度
    min 求最小值
    max 求最大值
    sorted  排序
    reversed 反向
    sum  求和

    进制转换函数
    bin()  转换为二进制
    oct()  转换为八进制
    hex() 转换为十六进制
    ord() 将字符转换成对应的ASCII码值
    chr() 将ASCII码值转换成对应的字符
    '''

### lambda  匿名函数
    '''
    关键字lambda用来创建简单的匿名函数。
    它既不能包含控制结构也没有return语句，
    返回的值就仅仅是表达式计算后得到的值。

    使用lambda可以省下函数定义的过程，
    可以使得代码更加精简。
    对于有些只需要使用一两次的函数，
    使用lambda也就不需要考虑函数命名的问题。
    '''

### 作用域
```python
'''
变量的在哪里被赋值的就决定了这个变量作用的区域。
定义在函数外的拥有全局作用域的变量称为全局变量，可以在整个程序
范围内访问，全局变量可以在函数内被访问但不可以在函数内被修改。
定义在函数内部的拥有一个局部作用域的变量称为局部变量，
只能在其被声明的函数内部访问。
'''
x = 12
def fun():
    a = 12
    global x
    x +=1
    return a+x

def fun1():
    m = 1
    def fun2():
        global x
        x += 1
        nonlocal m
        m +=1
        return m+x
    return fun2()
# global   用来声明全局变量。
# nonlocal  用来声明使用外层(非全局)变量。
```

### 内嵌函数和闭包
```python
def fun1(x):
    def fun2(y):
        return x+y
    return fun2
````


### 递归函数  
```python
# 函数里面自己调用自己
# 阶乘
'''
1! = 1
2! = 1*2
3! = 1*2*3 =2!*3
4!=1*2*3*4 = 3!*4

n! =1*2*....*n = (n-1)!*n
'''
def factorial(n):
    if n==1:
        return 1
    else:
        return factorial(n-1)*n
```

### 回调函数
```python
from tkinter import *

root = Tk()
root.geometry('400x400+300+100')
def click():
    print('我被调用了。。。。')
Button(root,text='点我',command=click,bg='red').pack(fill=X,expand=1)
root.mainloop()
```

### 练习
```python
'''
1.利用递归写斐波那契数列的函数f(n)。
注：(斐波那契数列：1,1,2,3,5,8,13,21,34,55,·······)
解析：      
f(1) = 1    
f(2) = 1      
f(3) = f(1) + f(2)
  .....
f(n) = f(n-2) + f(n-1)
'''
def f(n):
    if n==1 or n==2:
        return 1
    else:
        return f(n-2) + f(n-1)

'''

2.输出100以内的所有素数，素数之间以一个空格区分。

'''
def fun22():
    ls = []
    for i in range(2,101):
        for j in range(2,i):
            if i%j == 0:
                break
        else:
            ls.append(i)
    return ls


def fun33():
    ls = list(range(2,101))
    for i in range(2,101):
        for j in range(2,i):
            if i%j == 0:
                ls.remove(i)
                break
    return ls
```

### 正则表达式
```python
'''
 用于处理字符串的强大工具
 Python的re模块拥有全部的正则表达式的功能
 python中的正则表达式是一个特殊的字符序列，
 检查一个字符串是否与某种模式匹配
'''

# 元字符 ：
#  .   ^   $   *   +   ?   {}  []   \   |   ()

'''
大多数字母和字符会匹配它们自身，
有少数特殊字符我们称为元字符，
它们不能匹配自身，它们定义了字符类、
子组匹配和模式重复次数等
。
'''
# 元字符的使用
'''
    .    匹配除换行符之外的所有的字符(比\w多了特殊符号等) 
  \d  匹配0~9的数字   
  \s   匹配任意的空白符，包括空格，制表符(Tab)，换行符等
  \w 匹配字母或数字或下划线或汉字等  
  \b  表示单词的边界
  ^    脱字符，匹配输入字符串的开始的位置
    $   匹配输入字符串的结束位置
  解除元字符的特殊功能例
    \.   表示匹配点号本身
   \D、\S、\W、\B是与小写的相反的作用
'''
# 匹配次数
'''
 {M,N}   M和N 为非负整数，其中M<=N 表示前面的匹配M~N次
 {M，}   表示需要匹配M~无穷次（这里一个字符算一次，即'aaa'用'.'匹配是3次）
 {，N}    等价于{0~N}
 {N}          表示需要匹配N次
 *      匹配前面的子表达式零次或多次，等价于{0，}
 +      匹配前面的子表达式一次或多次，等价于{1，} 
 ？   匹配前面的子表达式零次或一次，等价于{0,1}
注：*？、+？、{n,m}?  贪婪与懒惰-----加个问号变为非贪婪模式

'''
# 子组匹配
'''
 [ ]   字符类，将要匹配的一类字符集放在[]里面-----只匹配里面的一个
 例如:
 [ . ? * ( ) {} ]     匹配里面的这些符号----注意：.在[]里是匹配.本身
 [0-9]                 匹配0到9的数字相当于\d
 [^\d]                  匹配除数字以外的字符，相当于\D---^放[]里表示取反
 [a-z]                  匹配所有的小写字母
 [^a-z]                 匹配非小写字母
    |                       相当于或（or）分支条件
例如：
 A|B                 匹配字母A或者B 与[AB]是一样的
 ab|c为匹配ab或c，a(b|c)为匹配ab或ac
 不能用[\]，因为\会把元字符]转义成]本身，即失去特殊意义
'''
# 分组
'''
 ()  分组，将要匹配的一类字符集放在()组成一个小组 
例如:
 (\d){3} 匹配一个三位数------等同于\d{3}，可以不用()的
 a(bc)*匹配一个a和0个或多个bc---ab*为匹配一个a加0个b或多个b,ab+为匹配一个a加1个b或多个b
 a(b|c) 匹配ab或者ac
'''
# re模块
'''
re.compile() 编译正则表达式为模式对象
re模块的常用方法
match()
判断一个正则表达式是否从开始处匹配字符串---即判断字符串内第一个字符开始是否满足
search()   遍历字符串，找到正则表达式匹配的第一个位置
findall()     遍历字符串，找到正则表达式匹配的所有位置并
以列表的形式返回
查看匹配对象中的信息
group() 返回匹配到的字符串
star()返回匹配的开始位置
end()返回匹配的结束位置
span()  返回一个元组表示匹配位置（开始，结束）
'''
#例：
url = 'slwofhttps:sdjifnls.gifdwfonnvohttps:sndi.gif'
p = re.compile(r'http.*?\.gif')
xx = re.findall(p,url)

#错在哪？
#一、原来是？?的原因，要英文输入法的?才行！！！
>>> re.search(r'ab.*？b','wjofiabbbbbbedacd')-----返回None
>>> re.search(r'ab.*?b','wjofiabbbbbbedacd')
<_sre.SRE_Match object; span=(5, 8), match='abb'>
>>> x = 'wjofiabbbbbbedacd'
>>> re.findall(r'ab.*?b',x)
['abb']

#二、
>>> re.search(r'\\+','sljdof\\\fdfsf')
<_sre.SRE_Match object; span=(6, 7), match='\\'>
```

## 面向对象
### 类的定义
```python
'''
基本形式：
class ClassName(object):
               Statement
	
    1.class定义类的关键字
    2.ClassName类名，类名的每个单词的首字母大写。
    3.object是父类名，object是一切类的基类。在python3中如果继承类是基类可以省略不写。
'''
```

### 类的初始化
    #   __init__
    '''
    定义类时，这种方法可以使类对象实例按某种特定的模式生产出来。

    后面的参数中第一个参数我们约定俗成的为self参数名，
    self代表的是在类实例化后这个实例对象本身。

    初始化函数除了有self这个参数表示实例对象本身之外，
    其他的参数的定义也遵循函数的必备参数和默认参数一样的原则，
    必备参数就是在实例化是一定要传入的参数，
    默认参数就是在定义时可以给这个参数一个初始值。
    '''

### 类的实例化
    '''
    基本形式：实例对象名 = 类名（参数）

    在实例化的过程中，self代表的就是这个实例对象自己。

    实例化时会把类名后面接的参数传进去赋值给实例，
    这样传进去的参数就成为了这个实例对象的属性。

    实例化的过程遵循函数调用的原则。
    在实例化时也必须个数和顺序与定义时相同（使用关键字参数可以改变传参的顺序）。
    当初始化函数定义时使用了默认参数时，在实例化时默认参数可以不传参这时
    这个实例对象就会使用默认的属性，如果传了参数进去则会改变这参数值，
    使实例化对象的属性就为你传进来的这个参数。

    isinstance(实例名，类名)
    判断一个实例是不是这个类的实例。
    '''

### 类的定义
```python
class Fruits:
    fruits = 'xxxxxx'    # 类属性
    def __init__(self,name,color,weight=90):
        self.name = name
        self.color = color
        self.weight = weight
        self.fruits = 'yyyyy'   # 实例属性
    def show(self):
        print('我的重量是%s'% self.color)

class Apple(Fruits):
    def __init__(self,color,weight,shape):
        Fruits.__init__(self,'apple',color,weight)    # 调用父类的初始化函数
        self.shape = shape
    def eat(self):
        print('被吃掉了。。。。')
  
ap1 = Apple('red',100,'圆的')
```

### 类的实例化
```python
fr1 = Fruits('apple','red')
fr2 = Fruits('banana','yellow')
fr3 = Fruits('apple','green',100)
```

### 类和实例属性
```python
'''
类属性
.类属性是可以直接通过“类名.属性名”来访问和修改。
.类属性是这个类的所有实例对象所共有的属性，
 任意一个实例对象都可以访问并修改这个属性（私有隐藏除外）。
.对类属性的修改，遵循基本数据类型的特性：列表可以直接修改，字符串不可以，
 所以当类属性是一个列表时，通过任意一个实例对象对其进行修改。
 但字符串类型的类属性不能通过实例对象对其进行修改。

实例属性
.在属性前面加了self标识的属性为实例的属性。
.在定义的时候用的self加属性名字的形式，在查看实例的属性时
 就是通过实例的名称+‘.’+属性名来访问实例属性。

方法属性
.定义属性方法的内容是函数，函数的第一个参数是self，代表实例本身。

一些说明：
.数据属性会覆盖同名的方法属性。减少冲突，可以方法使用动词，数据属性使用名词。
.数据属性可以被方法引用。
.一般，方法第一个参数被命名为self,，这仅仅是一个约定，
 self没有特殊含义，程序员遵循这个约定。
.查看类中的属性和实例属性可以调用__dict__方法返回属性组成的字典。
'''
```

### 私有变量和类本地变量
    '''
    以一个下划线开头的命名（无论是函数，方法或数据成员），
    都会被隐藏起来。但直接将命名完整的写下还是一样可以访问到。
    单下划线只是隐藏了属性，但还是可以从外部访问和修改。
    以两个下划线开头的命名，一样会被隐藏，只能在内部访问和修改，
    不能在外部访问，因为它变成了“_类名__属性”的形式。
    在外部只能通过这种形式才能访问和修改。
    双下划线开头的属性就变成了私有变量，即使能改也不要在外部外部修改了。
    私有变量的作用就是确保外部代码不能随意修改对象内部的状态。
    '''

### 数据封装：
    '''
    在类里面数据属性和行为用函数的形式封装起来，
    访问时直接调用，不需知道类里面具体的实现方法。
    '''

### 继承：
    '''
    .在定义类时，可以从已有的类继承，
     被继承的类称为基类，新定义的类称为派生类。

    .在类中找不到调用的属性时就搜索基类，
     如果基类是从别的类派生而来，这个规则会递归的应用上去。
     反过来不行。

    .如果派生类中的属性与基类属性重名，那么派生类的属性会覆盖掉基类的属性。
     包括初始化函数。

    .派生类在初始化函数中需要继承和修改初始化过程，
     使用’类名+__init__(arg)’来实现继承和私有特性,也可以使用super()函数。

    issubclass(类名1，类名2)
    判断类1是否继承了类2
    '''

### 多态：
    '''
    .多态是基于继承的一个好处。

    .当派生类重写了基类的方法时就实现了多态性。
    '''

### 练习
```python
# 一、写个人的类。
#   要求：
#       1. 属性包含姓名，性别，年龄。
#       2.方法可以自己随便写。
#二、写一个学生的类，学生的类继承了人的类。
#   要求：
#       1.在继承人的属性的基础上增加成绩这一属性。
#       2.把之前分数等级测试的函数写到这个类里，作为这个类的一种方法。
#       提示：把input和循环语句都删掉，只留下if判断。


#一、
class People:
    place = '中国'
    def __init__(self, name, gender, age):
        self.name = name
        self.gender = gender
        self.age = age
        self.game = '踢足球'
    def play(self):
        print('%s在%s。'% (self.name,self.game))

p1 = People('Jack','man',20)

#二、
class Student(People):
    def __init__(self, name, gender, age, score):
        People.__init__(self, name, gender, age)
        self.score = score
    def grades(self):
        if 90 <= self.score <= 100:
            print('等级A')
        elif 80 <= self.score < 90:
            print('等级B')
        elif 60 <= self.score < 80:
            print('等级C')
        elif 0 <= self.score < 60:
            print('等级D')
        else:
            print('输入有误')

s1 = Student('Jack','man',20,85)

#super()
class Student1(People):
    def __init__(self, name, gender, age, score):
        super().__init__(name, gender, age)   #不需要参数self
        self.score = score
    def grades(self):
        if 90 <= self.score <= 100:
            print('等级A')
        elif 80 <= self.score < 90:
            print('等级B')
        elif 60 <= self.score < 80:
            print('等级C')
        elif 0 <= self.score < 60:
            print('等级D')
        else:
            print('输入有误')

s11 = Student1('Jack','man',20,85)
```

### 多继承
```python
class A:
    def show(self):
        print('AAAAA')
        
class B:
    def fun(self):
        print('BBBBB')

class C(A,B):     #如果A和B的方法名相同，则前面的A优先
    pass

x = C()
```

### 实例调用
```python
'''
__init__    初始化
__repr__    c1-----对应repr(object)这个函数，返回一个可以用来表示对象的可打印字符串
直接访问对象的时候调用__repr__； print输出的时候调用__str__；
__str__     print (c1 )(如果类里面先定义了__repr__的话print x时也会返回对应的
__repr__和__str__这两个方法都是用于显示的，__str__是面向用户的，而__repr__面向程序员。
打印操作会首先尝试__str__和str内置函数(print运行的内部等价形式)，它通常应该返回一个友好的显示。
__call__    c1()   使实例可被调用-----本身直接c1()是会提示错误的。
'''
ss = 'a\nb'
class Rectangle:
    def __init__(self,width,height):
        self.width = width
        self.height = height
    def __str__(self):
        return '宽为%s,高为%s' % (self.width,self.height)
    def __repr__(self):
        return '面积为%s' % self.area()
    def __call__(self):
        return 'hahahha'
    def area(self):
        return self.width*self.height
    def __add__(self,other):
        if isinstance(other,Rectangle):
            return self.area()+other.area()

c0 = Rectangle(3,4)
```

### 运算符魔法方法
```python
'''
__add__(self,other)     x+y
__sub__(self,other)     x-y 
__mul__(self,other)     x*y  
__mod__(self,other)     x%y
__iadd__(self,other)    x+=y
__isub__(self,other)    x-=y 
__radd__(self,other)    y+x
__rsub__(self,other)    y-x 
__imul__(self,other)    x*=y 
__imod__(self,other)    x%=y
'''
'''
__radd__是自定义的类操作符，执行“右加”。当python解释器执行到a+b这样的语句时，
首先在查找a中有没有__add__操作符，如果a中没有定义，那么就在b中查找并执行__radd__。
下面是个简单例子:
class A:
  pass
class B:
  def __radd__(self, a):
    print('B.__radd__')
    return a.v + self.v
class C:
  def __add__(self, b):
    print('C.__add__')
    return self.v + b.v

a = A()
a.v = 1
b = B()
b.v = 2
c = C()
c.v = 3
print(a + b) #因为a中没有__add__，所以调用的是B.__radd__
print(c + b) #c中有__add__，所以调用的是C.__add__
至于__iadd__()，是运算符类operator的成员函数，就是累加操作符的另一种调用形式。
a = operator.__iadd__(a, b)就等价于a += b

'''
class str1(str):
    pass

aaa = str1('ab')
bbb = str1('b')

print(aaa+bbb)            #输出'abb'
print(aaa.__add__(bbb))   #输出'abb'

'''
help(int)里面的有：
 |  Methods defined here:
 |  
 |  __abs__(self, /)
 |      abs(self)
 |  
 |  __add__(self, value, /)
 |      Return self+value.
 |  
 |  __and__(self, value, /)
 |      Return self&value.
 |  
 |  __bool__(self, /)
 |      self != 0
 |  
 |  __ceil__(...)
 |      Ceiling of an Integral returns itself.
 |  
 |  __divmod__(self, value, /)
 |      Return divmod(self, value).
 |  
 |  __eq__(self, value, /)
 |      Return self==value.
 |  
 |  __float__(self, /)
 |      float(self)
 |  
 |  __floor__(...)
 |      Flooring an Integral returns itself.
 |  
 |  __floordiv__(self, value, /)
 |      Return self//value.
 |  
 |  __format__(...)
 |      default object formatter
 |  
 |  __ge__(self, value, /)
 |      Return self>=value.
 |  
 |  __getattribute__(self, name, /)
 |      Return getattr(self, name).
 |  
 |  __getnewargs__(...)
 |  
 |  __gt__(self, value, /)
 |      Return self>value.
 |  
 |  __hash__(self, /)
 |      Return hash(self).
 |  
 |  __index__(self, /)
 |      Return self converted to an integer, if self is suitable for use as an index into a list.
 |  
 |  __int__(self, /)
 |      int(self)
 |  
 |  __invert__(self, /)
 |      ~self
 |  
 |  __le__(self, value, /)
 |      Return self<=value.
 |  
 |  __lshift__(self, value, /)
 |      Return self<<value.
 |  
 |  __lt__(self, value, /)
 |      Return self<value.
 |  
 |  __mod__(self, value, /)
 |      Return self%value.
 |  
 |  __mul__(self, value, /)
 |      Return self*value.
 |  
 |  __ne__(self, value, /)
 |      Return self!=value.
 |  
 |  __neg__(self, /)
 |      -self
 |  
 |  __new__(*args, **kwargs) from builtins.type
 |      Create and return a new object.  See help(type) for accurate signature.
 |  
 |  __or__(self, value, /)
 |      Return self|value.
 |  
 |  __pos__(self, /)
 |      +self
 |  
 |  __pow__(self, value, mod=None, /)
 |      Return pow(self, value, mod).
 |  
 |  __radd__(self, value, /)
 |      Return value+self.
 |  
 |  __rand__(self, value, /)
 |      Return value&self.
 |  
 |  __rdivmod__(self, value, /)
 |      Return divmod(value, self).
 |  
 |  __repr__(self, /)
 |      Return repr(self).
 |  
 |  __rfloordiv__(self, value, /)
 |      Return value//self.
 |  
 |  __rlshift__(self, value, /)
 |      Return value<<self.
 |  
 |  __rmod__(self, value, /)
 |      Return value%self.
 |  
 |  __rmul__(self, value, /)
 |      Return value*self.
 |  
 |  __ror__(self, value, /)
 |      Return value|self.
 |  
 |  __round__(...)
 |      Rounding an Integral returns itself.
 |      Rounding with an ndigits argument also returns an integer.
 |  
 |  __rpow__(self, value, mod=None, /)
 |      Return pow(value, self, mod).
 |  
 |  __rrshift__(self, value, /)
 |      Return value>>self.
 |  
 |  __rshift__(self, value, /)
 |      Return self>>value.
 |  
 |  __rsub__(self, value, /)
 |      Return value-self.
 |  
 |  __rtruediv__(self, value, /)
 |      Return value/self.
 |  
 |  __rxor__(self, value, /)
 |      Return value^self.
 |  
 |  __sizeof__(...)
 |      Returns size in memory, in bytes
 |  
 |  __str__(self, /)
 |      Return str(self).
 |  
 |  __sub__(self, value, /)
 |      Return self-value.
 |  
 |  __truediv__(self, value, /)
 |      Return self/value.
 |  
 |  __trunc__(...)
 |      Truncating an Integral returns itself.
 |  
 |  __xor__(self, value, /)
 |      Return self^value.

'''
```

### 装饰器
```python
'''
@property 装饰过的函数返回的不再是一个函数，而是一个property对象
          装饰过后的方法不再是可调用的对象，可以看做数据属性直接访问。
@staticmethod 把没有参数的函数装饰过后变成可被实例调用的函数，
             函数定义时是没有参数的。
@classmethod 把装饰过的方法变成一个classmethod类对象，既能能被类调用又能被实例调用。
 注意参数是cls代表这个类本身。而是用实例的方法只能被实例调用。             
'''

class Rectangle:
    def __init__(self,width,height):
        self.width = width
        self.height = height
    @property
    def area(self):
        return self.width*self.height
    @staticmethod
    def fun():
        return 'xxxxxx'
    @classmethod
    def show(cls):     #装饰后，c1.show()同Rectangle.show()
        return 'yyyyyy'

c1 = Rectangle(3,4)    #调用距离最近的Rectangle
c2 = Rectangle(4,5)


def fun1(x):
    def fun2(y):
        return x(y) + 100 
    return fun2

@fun1    #fun1(ff)
def ff(z):          #装饰后，即ff传给x，z传给y
    return z*z

def filterarg(x):
    def fit(*arg):
        if len(arg) == 0:
            return 0
        for i in arg:
            if not isinstance(i,int):
                return 0
        return x(*arg)
    return fit

@filterarg
def sums(*arg):
    return sum(arg)

def average(*arg):
    return sum(arg)/len(arg)

average = filterarg(average)
```




### 练习
```python
# 写个名为Character的类，这个类继承了str类。
# 把上次练习的前四题的函数封装到Character类中，作为这个类的方法。

#法一：
class Character(str):
    def __init__(self,x):
        self.x = x
    def reversed_sequence(self):
        if type(self.x) == str:
            return ''.join(reversed(list(self.x)))
        else:
            return type(self.x)(reversed(self.x))

    def converted_case(self):
        s = ''
        for i in self.x:
            if i.isupper():
                s += i.lower()
            elif i.islower():
                s += i.upper()
            else:
                s += i
        return type(self.x)(s)

    def which_order(self):
        if list(self.x) == sorted(self.x):
            print('UP')
        elif list(self.x) == sorted(self.x, reverse=True):
            print('DOWN')

    def charcount(self):
        a = {'whitespase': 0, 'other': 0, 'a': 0, 'b': 0, 'c': 0, 'd': 0, 'e': 0, 'f': 0, 'g': 0,
             'h': 0, 'i': 0, 'j': 0, 'k': 0, 'l': 0, 'm': 0, 'n': 0, 'o': 0, 'p': 0, 'q': 0,
             'r': 0, 's': 0, 't': 0, 'u': 0, 'v': 0, 'w': 0, 'x': 0, 'y': 0, 'z': 0}
        for i in self.x.lower():
            if i in a:
                a[i] += 1
            elif i == ' ':
                a['whitespase'] += 1
            else:
                a['other'] += 1
        return a

a1 = Character('abc')
a2 = Character('123AA')
a3 = Character([1,2,3])

#法二：此解法不准确吧。
class Character2(str):
    def reversed_sequence(x):
        if isinstance(x,str):
            return ''.join(reversed(list(x)))
        else:
            return type(x)(reversed(x))

a4 = Character2('abc')
a5 = Character2([1,2,3])    #注意isinstance(a5,str)为True,所以此解法应该不准确。

#法三：
class Character3(str):
    def __init__(self,x):
        self.x = x
    def reversed_sequence(self):
        x = self.x
        if type(x) == str:
            return ''.join(reversed(list(x)))
        else:
            return type(x)(reversed(x))

a6 = Character3('abc')
a7 = Character3([1,2,3])
```


### 文件输入输出
```python
'''
open函数可以对文本文件进行读写的操作
基本形式：
    open(filename,mode)
 filename是文件名，可以写为绝对路径也可以是相对路径
 mode是打开模式。
 open函数里面有个enconding参数，
 如果打开的文件编码不是gbk,可以通过这个参数来设置编码。
'''
```

### 跳转路径
```python
'''
os.chdir()
'''
```

### 文件的打开模式
```python
'''
r 只读模式，文件不存在时会报错。
w 写入模式，文件存在会清空之前的内容，文件不存在则会新建文件。
x 写入模式，文件存在会报错，文件不存在则会新建文件。
a 追加写入模式，不清空之前的文件，直接将写入的内容添加到后面。
b 以二进制模式读写文件，wb,rb,ab。
+ 可读写模式，r+,w+,x+,a+,这几种模式还遵循了r,w,x,a的基本原则。
'''
```

### 文件对象方法
```python
# 读取文件内容：read()，readline()，readlines()：
'''
f.read(size) 读取文件的内容，将文件的内容以字符串形式返回。
size是可选的数值，指定字符串长度，如果没有指定size或者指定为负数，
就会读取并返回整个文件。当文件大小为当前机器内存两倍时就会产生问题，
反之就尽可能大的size读取和返回数据，如果到了文件末尾，会返回空字符串。

f.readline() 从文件中读取单独一行，字符串结尾会自动加上一个换行符\n，
只有当文件最后一行没有以换行符结尾时，这一操作才会被忽略，
这样返回值就不会有混淆。如果返回空字符串，表示到达率文件末尾，
如果是空行，就会描述为\n,一个只有换行符的字符串。

f.readlines() 返回一个列表，列表的元素为文件行的内容。
可以通过列表索引的方式将文件的每一行的内容输出。
可以通过for循环迭代输出每一行的信息。
'''
# 文件的写入：write() , writelines()：
'''
f.write() 将要写入的内容以字符串的形式通过write方法写入文件中。
f.writelines() 括号里必须是由字符串元素组成的序列。
'''
# 内容的保存和关闭：flush() , close()：
'''
f.flush()在读写模式下，当写完的数据想要读取出来时，
要先缓存区的内容保存到文件当中。
f.close() 关闭文件。对一个已经关闭的文件进行操作会报错。
'''
#光标位置：tell() , seek()：
'''
f.tell() 返回光标在文件中的位置。
f.seek(offset,from)在文件中移动文件指针，
从from(0代表起始位置，1代表当前位置，2代表文件末尾)偏移offset个字节。
'''
#查看文件信息：closed , mode , name ：
'''
closed 查看文件是否已经关闭，返回布尔值。
mode 返回文件打开模式。
name 返回文件名。
'''
# with 形式打开文件，里面的语句执行完后会自动关闭文件。
'''
with open('文件名') as f:
    f.read() 
'''
```


### 异常
```python
# 异常处理程序常规语法
# The Python Standard Library---5.Built-in Exceptions---5.4.Exception hierarchy

'''
try:
    suite1        #测试语句块
except exception1:
    suite2        #如果测试语句suite1中发生exception1异常时执行
except (exception2,exception3):
    suite3       #如果测试语句suite1中发生元组中任意异常时执行
except exception4 as reason:    #as把异常的原因赋值给reason
    suite4       #如果测试语句suite1发生exception4的异常时执行
except:
    suite5      #如果测试语句suite1发生异常在所列出的异常之外时执行
else:
    suite5      #如果测试语句块suite1中没有发生异常时执行
finally:
    suit6       #不管测试语句suite1中有没有发生异常都会执行

注意：中间的except，else，finally都是可选的
              但至少有一个，不然try就没有意义了，根据实际中的需求来选择。
              经测试，不能单独写try+else
'''
'''
try:
    print(1111)
    a = 'python'
    ff = open('xxx.py')
    print(x)
    print(a[10])
except (IndexError,NameError) as reason:
    print(reason)
else:
    print('没发生异常')
finally:
    print('都执行')

print(222)
'''

'''
try:
    print(111)
    print(a)
    print(222)
except NameError:
    print('没有定义这个对象')

'''

# raise 触发异常    例：raise KeyError
# 使用raise语句自己触发异常

# assert断言：用来声明某个条件是真的
# 如果条件是假的则会抛出AssertionError异常   例：assert 1>2
```



### 练习
```python
'''
1.打开文件，修改内容，写入另一个文件。
  把文件reform.txt中的名人名言改成“某某说：......”的形式保存到另一个文件中。
2.分数等级测试程序中加入异常处理来解决用户输入不合理的情况。
'''
'''
#1.第一版
# _*_ coding: utf-8 _*_
import re

a1 = open(r'C:\Users\Administrator\Desktop\reform.txt')
b1 = open(r'C:\Users\Administrator\Desktop\reform1.txt','w+')
a2 = a1.readlines()
x = re.compile(r'.*?。')
y = re.compile(r'\w*?\s')
m = ''
for i in a2:
    if len(i)>1:
        mo1 = x.search(i)
        mo2 = y.search(i)
        m += ''.join([mo2.group()[:-1],'说：',mo1.group(),'\n'])
    else:
        m += i
b1.write(m)
b1.flush()
b1.seek(0)
print(b1.read())
a1.close()
b1.close()    #21行
'''
'''
#1.第二版
# _*_ coding: utf-8 _*_
import re

a1 = open(r'C:\Users\Administrator\Desktop\reform.txt')
b1 = open(r'C:\Users\Administrator\Desktop\reform1.txt','w+')
x = re.compile(r'(.*?。)——(\w+)\s')
m = ''
for i in x.findall(a1.read()):
    m += ''.join((i[1],'说：',i[0],'\n\n'))
b1.write(m)
b1.flush()
b1.seek(0)
print(b1.read())
a1.close()
b1.close()    #14行

#正则表达式可用下面这种方法，可用于复杂表达式。
y = re.compile(r'''
    (.*?。)    #大胆是取得进步所付出的代价。
    ——       #——
    (\w+)      #雨果
    \s         #\n\n
    ''',re.VERBOSE)

'''
'''
#1.第三版，改正一个错误（罗教·柯迪未匹配到），继续优化。
# _*_ coding: utf-8 _*_
import re

a1 = open(r'C:\Users\Administrator\Desktop\reform.txt',)
b1 = open(r'C:\Users\Administrator\Desktop\reform1.txt','w+')
x = re.compile(r'(.*?。)——(\w.+)\s')
b1.write(x.sub(r'\2说：\1\n',a1.read()))   #sub函数实现替换
b1.flush()
b1.seek(0)
print(b1.read())
a1.close()
b1.close()    #11行   

'''


#2.
while True:
    score = input('请输入你的分数（q退出）：')
    if score == 'q':
        break
    try:
        score = float(score)
        if 90<=score<=100:
            print('A')
        elif 80<=score<90:
            print('B')
        elif 60<=score<80:
            print('C')
        elif 0<=score<60:
            print('D')
        else:
            print('输入有误！')
    except ValueError:
        print('输入有误！')
```

### 早期练习
```python
a = 12           #整数
b = 'python'     #字符串
c = [1,2,3,4]    #列表
d = 4,5,6        #元组可不用括号
e = {'a':1,'b':2}#字典
f = {2,3,4}      #集合
print(a,b,c,d,e,f)
print(list(b))
print(type(d))
print(type(e))
print(type(f))

class Fruits:
    def __init__(self,name):
        self.name = name
    def eat(self):
        return 'lalala'
fr1 = Fruits('apple')
print(fr1.name)   #属性，Tab调出
print(fr1.eat())  #方法

import keyword
print(keyword.kwlist)
print(keyword.iskeyword('and'))

def fun():
    a = 'xxx'
    print(a,b)
    return 'hahaha'
print(a)
print(fun())
print(333)




#整型int; 浮点型float; 布尔型bool:True==1、False==0; 复数类型complex;
#算术运算符 +，-，*，/除、结果为浮点数，//除、取整数部分，%取余数，**次方;
#浮点数//后仍然是浮点数
#赋值运算符（先赋值才能运算） +=     -=    *=    /=    //=     %=     **=


print('-'*15,'1','-'*15)
print('***运算符***')
print(type(5),type(1.1))
print(type(True),type(1+2j))
print((5+2),(5-2), 5/2, 5//2, 5%2, 5**2)
print(-5**2,(-5)**2)
a, b ,c= 5, 2, 3           #先赋值
a += b                     #list情况下与a = a+b不同
print(a,type(a))           #a = 7,int
a /= b         
print(a,type(a))           #a = 3.5,float
a *= b 
print(a,type(a))           #a = 7.0,float
a //= b
print(a,type(a))           #a = 3.0,float
a %= b
print(a,type(a))           #a = 1.0,float
b **= c
print(b)
print(max(1,2,4,5,6.0),min(1,2,-5,7))
print(1.2-0.1)             #浮点数不精确
import decimal
d = decimal.Decimal('1.2')
e = decimal.Decimal('0.1')
print(type(d))             #<class 'decimal.Decimal'>
print(d-e)                 #结果精确
print('***序列***')
aa = 'we are'
bb = [1,3,5]
cc = (1,2,3,'a')
print(type(aa),aa[1:3],len(aa))
a, b, c= bb, bb, bb[:]     #[:]为浅拷贝
print(a, b, c)
print(id(a),id(b),id(c))
d, e=list(aa), str(list(aa))
print(d, type(d))          #字符串可转列表
print(e, type(e))          #list转str无法直接变回‘原样’
print(e[0],e[1],e[4],len(e))#[ ' ,都变成字符串的一部分
e1 = ''.join(d)            #list转str转回原样
print(aa, e1, type(e1))
f = list(cc)               #列表元组可互相转换
g = tuple(f)
print(f, g)
print(aa + e1)             #同类型可相+
print('w' in aa)
print('w' not in aa)
print('***列表方法及属性***')
aaa = [3,1,6,7,5,4]
aaa.append(9)       #注意，不要赋值，直接print则返回None！
print(aaa)                 #列表末尾添加新的对象。
aaa.clear()                #清空整个列表。
print(aaa)
aaa = [3,1,6,7,5,4]
bbb = aaa.copy()           #同[:]法，浅拷贝
print(aaa, bbb)
print(id(aaa), id(bbb))
aaa.extend([3,3,3])
print(id(aaa), aaa)        #扩展原来的列表。
print(aaa.count(3))        #统计某个元素在列表中出现的次数。
aaa.insert(0,34)           #指定位置插入元素。
print(aaa)
print(aaa.index(3))  #列表中找某个值第一个匹配项的索引位置。
print(aaa.index(3,5,8))  #在索引序列5-7中找第一个3的索引位。
print(aaa.pop(2))    #移除指定位置的元素，没指定为最后一个。
print(aaa)
aaa.remove(3)              #移除指定元素从左边开始的第一个。
print(aaa)
aaa.reverse()              #反向列表中元素。
print(aaa)
aaa.sort()                 #从小到大排序,只能同种类元素。
print(aaa)                 #排序且改变本身。
aaa.sort(reverse=True)     #从大到小排序，可改为reverse=1。
print(aaa)
print(sorted(aaa))         #内置方法，排序但不改变本身。

print(reversed(aaa))       #生成迭代器对象，<>表示对象。
print(list(reversed(aaa))) #list法查看迭代器对象。

print('-'*15,'2','-'*15)
print("12+'12'会报错，同类型才能相加。")
print(12 + int('12'))

print('-'*15,'3','-'*15)
print('str转list可转回，但需用join法。')
print('元组列表可互相转换。')
print('数字型字符串只能转对应数字类型。')
aaaa = 'we are'
bbbb = list(aaaa)
print(bbbb)
print(''.join(bbbb))
print(int(float('12.5')))
cccc = [1,2,3,4]
print(type(cccc)(aaaa))    #此处等同于list(aaa)
print('-'*14,'End','-'*14)
```

### 字符串
```python
#字符串的创建：单引号，双引号，三引号
#字符串的运算：长度len，	取值，切片，重复*，成员操作in
'''
字符串的方法及属性：
s.count(x)：返回字符串x在s中出现的次数，带可选参数
s.endswith(x)：如果字符串s以x结尾，返回True
s.startswith(x)：如果字符串s以x开头，返回True
s.find(x) ：返回字符串中出现x的最左端字符的索引值，如果不在则返回-1
s.index(x)：返回字符串中出现x的最左端的索引值，如果不在则抛出valueError异常
s.isalpha ()  ：测试是否全是字母,中文，都是字母则返回 True,否则返回 False.
s.isdigit () ：测试是否全是数字，都是数字则返回 True 否则返回 False.
s.islower () ：测试是否全是小写
s.isupper () ：测试是否全是大写
s.lower () ：将字符串转为小写
s.upper () ：将字符串转为大写 
s.replace (x,y) ：子串替换,在字符串s中出现字符串x的任意位置都用y进行替换
s.split()：返回一系列用空格分割的字符串列表
s.split(a,b)：a,b为可选参数，a是将要分割的字符串，b是说明最多要分割几个
'''
a = 'hello'
b = '中文aaa'

c = '222'
d = 'world'
e = '!'
print(a.count('l',0,3))
print(a.endswith('o'))
print(a.startswith('o'))
print(a.find('l'))
print(a.index('l'))
print(a.find('x'))
#print(a.index('x'))
print(b.isalpha())
print((b + '111').isalpha())
print(c.isdigit())
print(b.islower())
print(b.isupper())
print(b.upper())
print(b.upper().lower())
print(a.replace('l','2'))
print(a.split('l'))
print(a.split('l',1))

print(a+' '+d+e)
print('%s %s%s'%(a,d,e))
print(' '.join([a,d+e]))
print('{} {}{}'.format(a,d,e))
print('{1} {2}{0}'.format(a,d,e))
print('{x} {y}{z}'.format(x=a,y=d,z=e))

print('%d'%(12))
print('%f'%(1.11))
print('%10f'%(1.11))
print('%+10f'%(1.11))
print('%-10f'%(1.11))  #-表示左靠边
print('%10.2f'%(1.11))
print('%c'%(97))
print('%o'%(8))
print('%x'%(16))
print('%e'%(10**5))    #把一个数字记为a×10n的形式(1≤|a|<10，n为整数),这种计数法叫做科学计数法。

print('I\'m')
print('I love\npython')

#print('\a')            #要在cmd中进入环境才能看到效果
#print('aaa\b')         #注意，\b放末尾不起退格作用
#print('aaa\bd')
#print('we are \rfamily')
#print('sfw\tfd')

#二、
a = 'abcd'
print(a[3])
print(a[-1])
a = 'jay'

b = 'python'
print('my name is %sne,i love %s.'%(a[0:2],b))
#二、3.结果是报错，因为字符串是不可变的
info = 'abc'
print(info.replace('c','d'))
ls = ['a','b','c']
ls[2] = 'd'
print(ls)
lls = ['I','love','python']
print(' '.join(lls))


'''
字符串的拼接：
例： a = 'hello'  ,    b = 'python'   ,   c = '!'     将a,b ,c 中的字符串连成一句话。  
第一种方法：用  +   号      
   a + b +c    
第二种方法：格式化字符串  %s   
  '%s %s %s' % (a , b ,c)  （注：s前面可以加对象名，后面以字典的方式填入
第三种方法：''.join()方式，注意括号里是要连接的可以是列表，元祖   
      ' '.join([a,b,c])  （注：''里面是连接后面各个字符串的字符）
第四种方法：.format方式
   '{}{}{}'.format(a,b,c)    (注：{}里面可以填入与后面相对应的符号)
'''
'''
a = 'hello'
b,c = 'python','!'
x1 = a + ' ' + b +c
x2 = '%s %s %s ' % (a,b,c)
x3 = ' '.join([a,b,c])
x4 = '{} {} {}'.format (a,b,c)
'''
'''
format方法详解：
'{}{}{}'.format(a,b,c)
当{}里面是空的时候，里面默认索引为0，1，2按format括号里的顺序依次填入
'{1}{2}{0}'.format(a,b,c)
当{}里面有索引值时，按前面的索引值将后面的每项依次填入
'{x}{y}{z}'.format(x=a,y=b,z=c)
{}里面可以指定对象名称，后面通过赋值的方式给前面的相应的值，后面是无序的
'''
'''
%s 格式化字符串
%d 格式化整数
%f 格式化小数
%c 格式化ASCII字符
%o 格式化八进制
%x 格式化十六进制
%e 用科学计数法格式化
-  用作左对齐
+ 用在正数前面显示加号
m.n  m是显示的最小长度，当m大于格式化位数时才起作用显示m位，
            n是代表小数的位数。
'''
#字符串转义
'''
\\ 反斜杠  \'  单引号    \"双引号

\n 换行   \a提示音  \b退格键  \r回车键  \t横向制表符 \f换页

'''
'''
print(111,end='')
print(2222)
'''

#原始字符r

```

### 练习
```python
'''
1. 字符串:a = 'abcd' 用2个方法取出字母d
2. a = 'jay'   b = 'python'
用字符串拼接的方法输出：my name is jane,i love python.
3.info = 'abc'   info[2] = 'd'结果是什么，为什么会报错呢?
4.如果要把上面的字符串info里面的c替换成d，要怎么操作呢？
5.如果是列表对象ls = ['a','b','c'],在不重新创建的前提下要变成ls = ['a','b','d']怎么做。
6.将lls = ['I','love','python']，列表中的单个字符串对象连成一句话。
'''

# 题目1：
"""
给定一个任意的序列，对这个序列进行逆序输出

要求：
    1.不能直接使用序列切片方式。
    2.能够同时适用于字符串和元组

例如：
>>> reversed_sequence(('a','b','c'))
('c', 'b', 'a')
>>> reversed_sequence((1, 2, 3))
(3, 2, 1)
>>> reversed_sequence('abc')
'cba'
"""
#序列切片法：
def reversed_sequence(x):
    return x[::-1]

'''
# 题目1：
def reversed_sequence(x):
    if type(x) == str:
        return ''.join(reversed(list(x)))
    else:
        return type(x)(reversed(x))
'''

# 题目2：
"""
给定一个任意的字符序列，将字符序列中的大写字母转换成小写，将小写字母转换成大写

要求：
1. 序列的每一项都是单个的字符
2. 对于非字母字符，不做处理

例如：
>>> converted_case('AaBbCc')
aAbBcC
>>> converted_case(('a', 'b', 'c', '-'))
('A', 'B', 'C', '-')
"""
'''
# 题目2：
def converted_case(x):
    t = type(x)
    if type(x) == str:
        return x.swapcase()       
    else:
        m = ''.join(list(x)).swapcase()
        return t(m)
'''
def converted_case(x):
    s = ''
    for i in x:
        if i.isupper():
            s += i.lower()
        elif i.islower():
            s += i.upper()
        else:
            s += i
    return type(x)(s)
        

'''
def converted_case(x):
    y = []
    for i in x:
        if i.islower() == True:
            y.append(i.upper())
        elif i.isupper() == True:
            y.append(i.lower())
        else:
            y.append(i)
    if type(x) == str:
        return ''.join(y)
    else:
        return type(x)(y)
'''

# 题目3：
"""
输入一个序列，判断这个序列是升序，降序还是无序。

说明：排序规则，是Python默认的排序规则

要求：
  1. 如果是升序，输出'UP'
  2. 如果是降序，输出'DOWN'
  3. 如果无序，输出None

建议：整数序列或字符序列

例如：
>>> which_order('abc')
UP
>>> which_order([3,2,1])
DOWN
>>> which_order('132')
>>>
"""

# 题目3：
def which_order(x):
    if list(x) == sorted(x):
        print('UP')
    elif list(x) == sorted(x, reverse=True):
        print('DOWN')
    #else:
        #return None   


def which_order11(x):
    n = len(x)
    temp = []
    for i in range(n - 1):
        if x[i] <= x[i + 1]:
            temp.append(1)
        if x[i] >= x[i + 1]:
            temp.append(2)
    if temp.count(1) == n - 1:
        return 'UP'
    elif temp.count(2) == n - 1:
        return 'DOWN'

#题目4：
"""
输入一个字符串，统计出字符串中的元素的个数。

要求：
    1.字符不区分大小写，也就是'A'也算在'a'这个的个数上。
    2.返回一个固定28个键的字典，字典的28键'为：a-z26个小写字母，加上'whitespace'和'other'。
    3.字典的值为对应元素的个数，字符是空格则属于'whitespace',其他的字符为'other'。

提示：先创建一个28个键的字典，字典键对应的初始值都为0。

例如：
>>> charcount('123AA')
{'whitespase': 0, 'other': 3, 'a': 2, 'b': 0, 'c': 0, 'd': 0, 'e': 0, 'f': 0, 'g': 0, 'h': 0, 'i': 0, 'j': 0, 'k': 0, 'l': 0, 'm': 0, 'n': 0, 'o': 0, 'p': 0, 'q': 0, 'r': 0, 's': 0, 't': 0, 'u': 0, 'v': 0, 'w': 0, 'x': 0, 'y': 0, 'z': 0}
>>> charcount('a b c d')
{'whitespase': 3, 'other': 0, 'a': 1, 'b': 1, 'c': 1, 'd': 1, 'e': 0, 'f': 0, 'g': 0, 'h': 0, 'i': 0, 'j': 0, 'k': 0, 'l': 0, 'm': 0, 'n': 0, 'o': 0, 'p': 0, 'q': 0, 'r': 0, 's': 0, 't': 0, 'u': 0, 'v': 0, 'w': 0, 'x': 0, 'y': 0, 'z': 0}
>>>

"""
'''
#打印出26个字母的简便写法：
a = {}
for i in range(97,123):
    a[chr(i)] = 0
print(a)
'''
#答案
def charcount(x):
    a = {'whitespase': 0, 'other': 0, 'a': 0, 'b': 0, 'c': 0, 'd': 0, 'e': 0, 'f': 0, 'g': 0,
         'h': 0, 'i': 0, 'j': 0, 'k': 0, 'l': 0, 'm': 0, 'n': 0, 'o': 0, 'p': 0, 'q': 0,
         'r': 0, 's': 0, 't': 0, 'u': 0, 'v': 0, 'w': 0, 'x': 0, 'y': 0, 'z': 0}
    for i in x.lower():
        if i in a:
            a[i] += 1
        elif i == ' ':
            a['whitespase'] += 1
        else:
            a['other'] += 1
    return a


#题目5：
"""
写一个属于你自己的 frange函数，frange与range类似，一样的参数规则，但是每一项必须要是float类型

要求：
1. 不能利用range等已有的功能来方便实现，要自己写逻辑
2. 输出只需要是个列表就好

例如：
>>> frange(10)
[0.0, 1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0]
>>> frange(1, 5)
[1.0, 2.0, 3.0, 4.0]
>>> frange(1, 10, 2)
[1.0, 3.0, 5.0, 7.0, 9.0]
>>>
"""
'''
def frange(start,stop=None,step=1):
    if stop is None:
        stop = start
        start = 0
    result = []
    while start < stop:
        result.append(float(start))
        start += step
    return result
'''
#答案
def frange(start,stop=None,step=1):
    if stop is None:
        stop = start
        start = 0
    result = []
    while start < stop:
        result.append(float(start))
        start += step
    while start > stop and step < 0:
        result.append(float(start))
        start += step
    return result
        


'''
#题目5：
def frange(x,y=False,z=1):
    if y==False and z==1:
        if x == 1:
            return [0.0]
        elif x > 0 and type(x) == int:
            return frange(x-1) + [x-1.0]
        else:
            pass
    elif x >= 0 and y > x and z == 1:
        if y == (x+1):
            return [x-0.0]
        else:
            return frange(x,(y-1)) + [y-1.0]
    elif x >= 0 and y > x and int(z) > 1:
        if (y-x) <= z:
            return [x-0.0]
        else:
            return frange(x,y-z,z) + [y-(y-x)%z-0.0]
    else:
        pass
'''
```


### 模块及包
```
1.什么是模块？就是一个.py文件

2.导入模块？

import module
import module as new_name
from module import objectname
from module import *  
from module import objectname as newname

当前的文件目录中自动生成__pycache__文件夹，
文件夹里面会看到有新文件出现以.pyc扩展名的文件是
当前文件的__name__属性为‘__main__’,
所以测试文件放在if条件下，所以只导入创建的对象，

3.什么是包管理？把处理同一个事件的多个模块放到同一个目录下。
比如放到同个文件夹111里面,假设里面有Fruit.py模块。
然后import 111----------python2需要现在文件夹内新建个__init__.py文件。python3则不需要
from 111 import Fruit


#os模块-------对操作系统进行操作
os.name  如果是windows操作系统返回’nt’，如果是其他系统则返回 ‘posix’
os.environ 返回系统的环境变量，以dict形式显示
Os.getcwd() 返回当前工作目录
Os.chdir(path) 改变工作目录
Os.listdir(path=’.’) 列举指定目录中的文件名(‘.’表示当前目录，’..’代表上一级目录)
Os.mkdir(path) 创建单层目录，如该目录已存在抛出异常
Os.makedirs(path) 递归创建多层目录，如果该目录已经存在则抛出异常。
Os.remove(path) 删除文件
Os.rmdir(path) 删除单层目录，如改目录非空则抛出异常
Os.removedirs(path) 递归删除目录，从子目录到父目录逐层尝试删除，遇到目录非空则抛出异常。
Os.rename(old,new) 将文件old 重命名为new，文件和目录都使用这条命令

Os.path 模块中关于路径常用的函数使用方法：
Os.path.basename(path) 去掉目录路径，单独返回文件名
Os.path.dirname(path)  去掉文件名，单独返回目录路径
Os.path.join(path1,path2) 将path1,path2各部分组合成一个路径名
Os.path.split(path) 分割文件名和路径，返回（f_path,f_name）元组。如果完全使用目录，它也会将最后一个目录作为文件名分离，且不会判断文件或者目录是否存在。
Os.path.splitext(path)分离文件名与扩展名，返回（f_name,f_extension）元组
Os.path.getsize(file)返回指定文件的尺寸，单位是字节
Os.path.getatime(file) 返回指定文件最近的访问时间（浮点型秒数，可用time模块的gmtime()或localtime()函数换算）
Os.path.getctime(file) 返回指定文件创建时间（浮点型秒数，可用time模块的gmtime()或localtime()函数换算）
Os.path.getmtime(file) 返回指定文件最新的修改时间（浮点型秒数，可用time模块的gmtime()或localtime()函数换算）
返回True或False的函数
Os.path.exists(path) 判断指定路径（目录或文件）是否存在
Os.path.isabs(path) 判断指定路径是否为绝对路径
Os.path.isdir(path) 判断指定路径是否存在且是一个目录
Os.path.isfile(path) 判断指定路径是否存在且是一个文件

#shutil模块
复制文件
Shutil.copyfile(‘oldfile’,’newfile’) oldfile和newfile都只能是文件
Shutil.copy(‘oldfile’,’newfile’) oldfile只能是文件，newfile可以是文件也可以是目标目录
复制文件夹
Shutil.copytree(‘olddir’,’newdir’),olddir和newdir都只能是目录，且newdir必须不存在
移动文件（目录）
Shutil.move(‘oldname’,’newname’)
删除目录
Os.rmdir(‘dir’)只能删除空目录
Shutil.rmtree(‘dir’)空目录，有内容的目录都可以删


#sys模块-------对python进行操作
Sys.argv
用来向python解释器传递参数，名曰“命令行参数”
Sys.exit()
退出当前程序
Sys.stdout
与Python中的函数功能对照，sys.stdin获得输入，等价于python2中的raw_inpurt()，python3中的input(),sys.stdout负责输出
Sys.path
返回python目录下所有.pth路径文件下的内容集系统默认设置。
可以通过列表的操作对其进行修改，不过这种更改只对当前的程序起作用。


time模块

time.localtime()
    返回的元组的内容：
    属性(attribute)            值(value)
    tm_year(年)                例如：2016
    tm_mon(月)                 1~12
    tm_mday(日)                1~31
    tm_hour(时)                0~23
    tm_min(分)                 0~59
    tm_sec(秒)                 0~61
    tm_wday(星期几)            0~6(0代表星期一)
    tm_yday(一年中的第几天)    1~366
    tm_isdst(是否为夏令时)     0，1，-1(-1代表夏令时)
time.time()返回当前时间的时间戳，可以用来计算程序的耗时
时间戳(timestamp)表示的是从1970年1月1日00：00：00开始按秒计算的偏移量（time.gmtime(0)）
time.clock()用以浮点数计算的秒数返回当前的cpu时间,用来衡量不同程序的耗时
time.sleep(secs)推迟调用线程的运行，secs的单位是秒
time.asctime([t])接收时间元组并返回一个可读的形式。

```

### 迭代器生成器
```python
可以用for迭代的对象统称为可迭代对象（Iterable）。
可以被next()函数调用并不断返回下一个值的对象称为迭代器（Iterator）。
所有的可迭代对象可以通过iter()函数变成迭代器。
迭代器的特点是可以通过next()内置函数或者调用自身的__next__()方法来获取元素，当元素获取完则会抛出StopIteration异常。
所以迭代器的元素只能使用一次，在迭代之后元素会被销毁，这也正是迭代器的一大魅力。
例：
>>> x = [1,2,3]
>>> y = iter(x)
>>> y
<list_iterator object at 0x01021210>
>>> next(y)
1
>>> y.__next__ ()
2
>>> next(y)
3
>>> y.__next__ ()
Traceback (most recent call last):
  File "<pyshell#85>", line 1, in <module>
    y.__next__ ()
StopIteration
>>>
生成器（generator）也是一种迭代器。可以通过列表生成式的方式把列表解析的[]换成()，创建生成器对象。
例：
>>> l = [x*x for x in range(5)]
>>> l
[0, 1, 4, 9, 16]
>>> g = (y*y for y in range(3))
>>> g
<generator object <genexpr> at 0x036D7930>
>>> next(g)
0
>>> g.__next__ ()
1
>>> next(g)
4
>>> next(g)
Traceback (most recent call last):
  File "<pyshell#13>", line 1, in <module>
    next(g)
StopIteration
>>> 
例子中的l是列表解析生成的列表对象，使用的for迭代range函数，元素以x*x的形式组成一个新的列表对象。
将中括号换成小括号生成的g就是生成器对象，使用next()函数或者__next__方法获取里面的值，当值被取完之后返回StopIteration异常。
在函数中使用yield关键字可以创建生成器函数，带有yield的函数就不再是普通函数。
生成器函数可以生产一个无限的序列，调用生成器函数时会返回yeild后面的值。
例：
>>> def ge():
    n=1
    while True:
        yield n
        n+=1
        
>>> ge
<function ge at 0x035711E0>
>>> ge()
<generator object ge at 0x03567900>
>>> y = ge()
>>> next(y)
1
>>> next(y)
2
>>> next(y)
3
>>> 
上面例子中的ge函数就是一个生成器，先创建个n值为1，然后是while True的死循环，循环里面使用关键字yield，
yield n会让next()函数来取值时每次返回n的值，之后对n进行加1的操作。把ge()这个生成器对象赋值给y，
用next()函数会每次返回一个n的值，因为里面是个死循环，所以这里面的值是无限的，也就不会出现StopIteration的异常。
生成器函数里面在没有return时会执行到没有值时返回的StopIteration的异常。
但如果有return这个关键字，函数在执行的过程中遇到return 后就会出现StopIteration的异常，
return后面的值也不再是程序的返回值而是StopIteration异常的说明。
例：
>>> def ge():
    n=1
    while True:
        yield n
        n+=1
        return 'sfdsdffredsf'

>>> n = ge()
>>> next(n)
1
>>> next(n)
Traceback (most recent call last):
  File "<pyshell#23>", line 1, in <module>
    next(n)
StopIteration: sfdsdffredsf
>>> 
在之前的例子中加了一个return后，在使用next()时，会将程序挂起在yield的位置，
当下一次执行next()的时候会在yield的后一句开始执行，所以这里当执行到return时就返回了StopIteration的异常，
而异常的说明则是return后面的表达式。
生成器的方法：
close() 手动关闭生成器函数，再次调用时就会返回StopIteration的异常。
Send()可以接受外部传入的一个变量，并根据变量内容计算结果后返回。
首先要通过g.send(None)或者next启动生成器函数，并执行到第一个yield语句结束的位置。
throw() 用来向生成器函数送入一个异常。
例：
程序：
def ge():
    n = 1
    while True:
        try:
            m = yield n
            n += m
        except TypeError:
            print('send int type')
运行后shell中：
>>> a = ge()
>>> next(a)
1
>>> a.send(12)
13
>>> a.send(12)
25
>>> a.send('123')
send int type
25
>>> a.throw(TypeError)
send int type
25
>>> a.close()
>>> a.send(12)
Traceback (most recent call last):
  File "<pyshell#65>", line 1, in <module>
    a.send(12)
StopIteration
>>> 
这个例子中m = yield n 会使得send方法传进来的值赋给m，返回值是yield后面的n，然后让n与m相加后重新赋给n。
这里首先要注意的是要使用send的方法这个生成器就必须处于开启的状态，可以是用send(None)或者next()方法来开启。
那么如果传入的m不能与n相加则会报错，所以在循环中捕抓TypeError的异常。
使用throw方法传入了异常那么就会直接返回这个一场，这里对异常做了处理，所以执行了except里面的语句。
使用close()方法关闭生成器，如果再次使用时就会返回StopIteration的异常。
```

Python内建的filter()函数用于过滤序列。
和map()类似，filter()也接收一个函数和一个序列。和map()不同的时，filter()把传入的函数依次作用于每个元素，然后根据返回值是True还是False决定保留还是丢弃该元素。
例如，在一个list中，删掉偶数，只保留奇数，可以这么写：
def is_odd(n):
    return n % 2 == 1
filter(is_odd, [1, 2, 4, 5, 6, 9, 10, 15])
# 结果: [1, 5, 9, 15]






































































































