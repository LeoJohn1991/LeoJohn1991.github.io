---

layout: post
title:  "Python & Matlab 批处理文件脚本示例"
data:   2016-07-28 01:30:00
categories:  Script Python
tags: python script matlab

---

* content
{:toc}

如果需要重复处理文件的操作,手动选择往往低效,繁琐,这种情况往往可以写一个脚本来处理.所以学会写批处理脚本能大大提高效率,为此特地花了点时间总结下批处理脚本的编写,并写了几个例子,以供查阅.



## python os and os.path module

```python

os.mkdir(dirPath)
os.system("terminal command")
os.rename(filename, Newfilename)
os.path.listdir(path)
os.path.join(os.getcwd(), 'folder')
os.path.exists(path)
os.path.abspath(path) #绝对路径
os.path.basename(path) #文件名
os.path.split(path) #return (head,tail), path = join(head, tail)，父目录与文件名分离
os.path.splitext(path) # return (root, ext), root + ext = path， 扩展名分离

```

## Matlab批处理脚本

```matlab

str_prefix = pwd;

str_prefix = fullfile(str_prefix, 'images');
fileList = dir([str_prefix, '/TP*']);

% for i = 1:length(file)
%     fprintf('%s\n',tmp(i).name)
% end

for i = 1:length(fileList)
   filepath = fullfile(str_prefix, fileList(i).name);
   LJ_demo1(filepath);
end

```


## Python批处理脚本

```python

# coding:utf-8

import sys
import os

def main():
    '''
    批处理文件,如序列化重命名文件
    :return:
    '''
    # os.system("mkdir images")
    # os.system("touch images/a.jpg images/b.jpg images/c.jpg")
    print sys.version
    path = os.getcwd()
    if not os.path.exists('./images'):
        print "not exist " + os.path.join(path, "images")
        return
    prefix = os.path.join(path, "images")
    i = 1
    for file in os.listdir(prefix):
        [root, ext] = os.path.splitext(file)
        if ext == '.jpg':
            newname = str(i) + ext
            os.rename(os.path.join(prefix, file), os.path.join(prefix, newname))
            print "rename:", file, "->", newname
            i += 1

if __name__ == '__main__':
    main()

```

## Python编译Java项目脚本例子

```python

import os
import sys

def main():
    '''
    #designpatterns project run script
    javac -d classes src/*.java src/inner/*.java
    jar -cvf Test.jar -C classes/ .
    java -cp Test.jar Main
    '''
    ClassesDir = os.path.join(os.getcwd(), 'classes')
    if not os.path.exists(ClassesDir):
        os.mkdir(ClassesDir)
    ProjectJar = "pizzas.jar"
    ProjectMainClass = "PizzaTestDrive"
    packageName = "headfirst/designpatterns/factory/pizzafm/"
    if sys.argv[1] == "c":
            print("Compile program.")

            src = "./*.java"
            os.system("javac -d classes " + src)
            os.system("jar -cvf " + ProjectJar + " -C classes/ .")

    if sys.argv[1] == "r":
            print("Run program.")
            os.system("java -cp " + ProjectJar + " " + packageName + ProjectMainClass)

    print("Over!")

if __name__ == "__main__":
    main()

```

