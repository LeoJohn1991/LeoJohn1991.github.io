---

layout: post
title:  "Python list.sort和sorted总结"
data:   2016-07-28 00:30:00
categories:  Python
tags: python sort

---

* content
{:toc}

- list.sort(cmp=None, key=None, reverse=False)
- sorted(iterable[, cmp[, key[, reverse]]])

Python Documention中搜索 sort，在结果中选择**Sorting HOW TO**，有详细的list.sort()和sorted()例子。





---


## 我习惯的sort()排序

```python
# coding:utf-8
import sys
import os

def mycmp(x, y):
    if x[1] != y[1]:
        return x[1] - y[1]
    else:
        if y[0] == x[0]:
            return 0
        elif y[0] > x[0]:
            return 1
        else:
            return -1
def main():
    #单属性排序
    L0 = [5, 2, 3, 1, 4]
    L0.sort()
    print "L0 =", L0

    #reverse=True 降序
    L0.sort(reverse=True)
    print "(reverse)L0 =",L0

    #多属性排序（多属性同升序或同降序）
    L1 = [('a',2), ('d',2),('a',4),('b',3),('c',2)]
    L1.sort(key = lambda x:(x[1], x[0]))
    print "L1 =", L1

    #多属性排序 (多属性不同升序)
    #先数字升序,再字母降序
    L2 = [('a',2), ('d',2),('a',4),('b',3),('c',2)]
    L2.sort(cmp=mycmp)
    print "L2 =", L2

if __name__ == '__main__':
    main()
```


---

> 文档提炼，供自己查询
> 本地文档链接为：[file:///Users/jerry/Developer/docs/python-2.7.12-docs-html/howto/sorting.html#sortinghowto](file:///Users/jerry/Developer/docs/python-2.7.12-docs-html/howto/sorting.html#sortinghowto)


## list.sort()和sorted()区别

### sorted

```python
>>> help(sorted)
Help on built-in function sorted in module __builtin__:

sorted(...)
    sorted(iterable, cmp=None, key=None, reverse=False) --> new sorted list
```

### list.sort()

```python
>>> help(list.sort)
Help on method_descriptor:

sort(...)
    L.sort(cmp=None, key=None, reverse=False) -- stable sort *IN PLACE*;
    cmp(x, y) -> -1, 0, 1
```


iterable：是可迭代类型;
cmp：用于比较的函数，比较什么由key决定,有默认值，迭代集合中的一项;
key：用列表元素的某个属性和函数进行作为关键字，有默认值，迭代集合中的一项;
reverse：排序规则. reverse = True 或者 reverse = False，有默认值。
返回值：是一个经过排序的可迭代类型，与iterable一样。

注；一般来说，cmp和key可以使用lambda表达式。

sort()与sorted()的不同在于，sort是在原位重新排列列表，而sorted()是产生一个新的列表。

Another difference is that the list.sort() method is only defined for lists. In contrast, the sorted() function accepts any iterable.

```python
>>> sorted({1: 'D', 2: 'B', 3: 'B', 4: 'E', 5: 'A'})
[1, 2, 3, 4, 5]
```


## Key Functions

对复杂的元素排序例子：

```python
>>> student_tuples = [
    ('john', 'A', 15),
    ('jane', 'B', 12),
    ('dave', 'B', 10),
]
>>> sorted(student_tuples, key=lambda student: student[2])   # sort by age
[('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
```

对带属性的类对象排序例子：

```python
>>> class Student:
        def __init__(self, name, grade, age):
            self.name = name
            self.grade = grade
            self.age = age
        def __repr__(self):
            return repr((self.name, self.grade, self.age))
>>>
>>> student_objects = [
    Student('john', 'A', 15),
    Student('jane', 'B', 12),
    Student('dave', 'B', 10),
]
>>> sorted(student_objects, key=lambda student: student.age)   # sort by age
[('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
```

## Operator Module Functions

利用operator模块，进行多属性排序例子

```python
>>> sorted(student_tuples, key=itemgetter(1,2))
[('john', 'A', 15), ('dave', 'B', 10), ('jane', 'B', 12)]
>>>
>>> sorted(student_objects, key=attrgetter('grade', 'age'))
[('john', 'A', 15), ('dave', 'B', 10), ('jane', 'B', 12)]
```

## Ascending and Descending - Sorting reverse


```python
>>> print sorted([5, 2, 3, 1, 4], reverse=True)
[5, 4, 3, 2, 1]
>>> print sorted([5, 2, 3, 1, 4], reverse=False)
[1, 2, 3, 4, 5]

注：效率key>cmp(key比cmp快)
```

在Sorting Keys中：我们看到，此时排序过的L是仅仅按照第二个关键字来排的，如果我们想用第二个关键字
排过序后再用第一个关键字进行排序呢?

```python
>>> L = [('d',2),('a',4),('b',3),('c',2)]
>>> print sorted(L, key=lambda x:(x[1],x[0]))
>>>[('c', 2), ('d', 2), ('b', 3), ('a', 4)]
```