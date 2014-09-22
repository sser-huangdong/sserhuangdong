---
layout: post
title: 简洁高效的Python写法
description: ""
category: 
tags: ['Python', 'code']
---
{% include JB/setup %}

    学完C/C++之后，接触Python，甚至用来刷leetcode，但是有时候感觉我的写法不是很Pythonic，比较繁琐。所以一直寻思着整理一份参考。未完待续。。。

{% highlight python %}

{% endhighlight %}

---

基础部分
======

布尔判断
------

{% highlight python %}
1. x is y  # x是y
2. x is not y  # x不是y
3. x in y  # x在y中
4. x not in y  # x不在y中
5. x <= y < z  # 使用链式比较而不是 x <= y and y < z
6. "fun" != "funny"  # 字符串直接比较即可
{% endhighlight %}

交换变量
------
{% highlight python %}
x, y = y, x
# 而不是
temp = x
x = y
y = temp
{% endhighlight %}

三元表达式
--------
{% highlight python %}
x = y if y > z else z  # 相当于C的 x = y > z? y: z
x = max(y, z)  # 这是一种更简洁的写法
{% endhighlight %}

增减1
----
    在C里面可以用++和--来增减1，但是在Python里面只能用+=1和-=1了


else和循环(while/for)
--------------------
    Python的一个语法糖是循环可以和else结合，只要跳出循环没有执行break就会调用。

{% highlight python %}
a = [12, 24, 35, 43, 65]
b = 40
for i in a:
    if i > b:
        print 'There is some item in a bigger than %d' % b
        break
else:
    print "Every item in a not bigger than %d" % b
{% endhighlight %}

with
----
{% highlight python %}
with open('test.txt', 'r') as fin:
    fin.read()
{% endhighlight %}


---

简洁写法
======

枚举
---
{% highlight python %}
a = [1, 23, 34, 56, 67]
# 获取数组内容与相应下标：
for index, item in enumerate(a):
    print index, item

# 而不是
index = 0
for item in a:
    print index, item
    index += 1

# 更不是
for item in a:
    index = a.index(item)
    print index, item
{% endhighlight %}


同时迭代两个列表
-------------
{% highlight python %}
alist = [1, 2, 3, 4, 5]
blist = [2, 3, 4, 5, 6]
for a, b in zip(alist, blist):
    print a, b

# 也可以写，只是效率差点
for index in xrange(len(alist)):
    print alist[index], blist[index]
{% endhighlight %}

map函数
-------
    如果需要对链表里面每个元素都做同样的操作，除了for还有map
{% highlight python %}
sin = "1 2 3 4"
ints = map(int, sin.split())  # split() 是字符串的分割函数
ints = [int(s) for s in sin.split()]  # 还可以这样写
{% endhighlight %}



list构成的stack和queue
--------------------
{% highlight python %}
stack = []
stack.append(1)
stack.append(2)
stack.pop()  # 2
stack.pop()  # 1

queue = []
queue.append(1)
queue.append(2)
queue.pop(0)  # 1
queue.pop(0)  # 2
{% endhighlight %}


获取字典元素
----------
{% highlight python %}
d = {}
d['a']  # 找不到，导致异常
d.get('a')  # 找不到，返回None
d.get('a', 'default')  # 找不到，
{% endhighlight %}

字符串trim()
-----------
    Python的字符串没有trim()方法，就是去除左右两边的字符。可以使用strip()方法来代替。

{% highlight python %}
s = "   sss  "
print s.strip()  # "sss"
print s  # '   sss  '
{% endhighlight %}


字符串连接
--------
{% highlight python %}
l = ['aaa', 'bbb', 'ccc']
"".join(l)  # 'aaabbbccc'

{% endhighlight %}


---

一些坑
=====

正则匹配全部字符
-------------
    正则点号.匹配的是除了\n之外的所有字符，而不是所有字符！所以用\W\w来匹配所有字符吧

可变的默认参数
-----------
{% highlight python %}
def wrongFunc(x, l=[]):          # 不要这么干
    l.append(x)

def rightFunc(x, l=None):        # 更好的一种方式
    if l is None:
       l = []
    l.append(x)
{% endhighlight %}


负数取模和负数除法
---------------
{% highlight python %}
-1 % 5   # Python:  4  C++: -1
4  % -5  # Python: -1  C++: 4
-1 % -5  # Python: -1  C++: -1
-3 / 4   # Python: -1  C++: 0
{% endhighlight %}


---

参考:
====
[Python 实用技巧（上）](http://blog.jobbole.com/50420/)  
[给Python初学者的一些技巧](http://blog.jobbole.com/32748/)  
[Python编程中需要注意的一些事](http://blog.jobbole.com/19835/)  
[让你的python代码更加pythonic](http://wuzhiwei.net/be_pythonic/)  
[pythonic examples](http://jianpx.iteye.com/blog/736669)  
[Learning the Pythonic Way](http://www.cs.cmu.edu/~srini/15-441/F11/lectures/r04-python.pdf)  
[Code Like a Pythonista: Idiomatic Python](http://python.net/~goodger/projects/pycon/2007/idiomatic/handout.html)  