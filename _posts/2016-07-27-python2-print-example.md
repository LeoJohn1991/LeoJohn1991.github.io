---

layout: post
title:  "Python2 之 print函数的使用"
data:   2016-07-27 00:30:00
categories:  Python
tags: python print

---

* content
{:toc}

 吐槽下，python2 官方文档的print资料好少啊，看的别人博客才知道咋用╮(╯_╰)╭




## print 使用例子

```py
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import sys

print(sys.version)

#输入与输出

#str()与repr()
for x in range(1, 11):
  print repr(x).rjust(2), repr(x*x).rjust(3),
  #逗号代表不换行
  print repr(x*x*x).rjust(4)

#格式化输出
for x in range(1, 11):
  print '{0:2d} {1:3d} {2:4d}'.format(x, x*x, x*x*x)

print 'We are the {} who say "{}!"'.format('knights', 'Ni')
print '{1} and {0}'.format('spam', 'eggs')
print 'This {food} is {adjective}.'.format(food='spam', adjective='absolutely horrible')
print 'The story of {0}, {1}, and {other}.'.format('Bill', 'Manfred', other='Georg')
```
```python
import math
#保留三位小数点
print 'The value of PI is approximately {0:.3f}.'.format(math.pi)

table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 7678}
for name, phone in table.items():
  print '{0:10} ==> {1:10d}'.format(name, phone)

print 'Jack: {Jack:d}; Sjoerd: {Sjoerd:d}; Dcab: {Dcab:d}'.format(**table)

#old style， 语法类似sprintf
print 'The value of PI is approximately %5.3f.' % math.pi
print 'x = %d, y = %d' % (3, 4)
```

```python
#文件的读写
f = open('/tmp/workfile', 'r+')
print f

#f.write('This is a test\n')

f.read()

f.readline()

f.readlines()

for line in f:
  print line

#write something other than string
value = ('the answer', 42)
s = str(value)
f.write(s)

f = open('/tmp/workfile', 'r+')
f.write('0123456789abcdef')
f.seek(5)     # Go to the 6th byte in the file
f.read(1)
f.seek(-3, 2) # Go to the 3rd byte before the end
f.read(1)

f.close()
f.read()

with open('/tmp/workfile', 'r') as f:
  read_data = f.read()

f.closed

if __name__ == "__main__":
    a = 1
    b = 2
```


## Reference
1. <http://docs.pythontab.com/python/python2.7/inputoutput.html#tut-formatting>