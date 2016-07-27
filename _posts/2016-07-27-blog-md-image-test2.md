---

layout: post
title:  "博客markdown图片引用总结"
data:   2016-07-27 06:30:00
categories:  Markdown
tags: blog markdown
---

* content
{:toc}

markdown引用图片一般有两种方式，一种是绝对路径(图片网页链接地址)，另一种是相对路径(使用本地图片)。

对于github上的博客工程，若用相对路径，只能在博客Home栏下，相应博客的概括中能正常显示，如果查看完整博客，图片显示时常。而如果用图片网址，显示无误。
所以主要找到github上blog工程下图片的网址即可正常使用图片，一般这种地址为
`https://raw.githubusercontent.com/LeoJohn1991/LeoJohn1991.github.io/master/images/20160727/kaolalj.jpg`
图片在工程里的路径为`./images/20160727/kaolalj..jpg`

## 示例如下
- 相对路径 

`![koala](../images/20160727/kaolalj.jpg)`

![koala](../images/20160727/kaolalj.jpg)

*-------此处为博客概括分割线---------*

---



- 绝对路径

`![kaola1](https://raw.githubusercontent.com/LeoJohn1991/LeoJohn1991.github.io/master/images/20160727/kaolalj.jpg)`

![kaola1](https://raw.githubusercontent.com/LeoJohn1991/LeoJohn1991.github.io/master/images/20160727/kaolalj.jpg)





