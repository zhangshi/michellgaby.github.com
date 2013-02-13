---
layout: post
title: "[浅谈]如何汉化CWM Recovery"
description: ""
category: 
tags: [技术交流]
---
{% include JB/setup %}
##简述Recovery汉化的方法
Recovery汉化据我所知有两种方法，第一种是使用chinese_gen.rb脚本来生成中文字库并修改graphics.c文件使其调用chinese.c/chinese.h来达到显示中文的目的，第二种则是使用[xiaolu](https://github.com/xiaolu/cmw_recovery_cn)的中文字库和修改graphics.c文件来实现的。

###第一种方法的缺点与优点
使用chinese_gen.rb的方法汉化Recovery的话，中文可以显示，但是显示字体会有瑕疵，并且不能使用USB大容量存储模式和ADB无法连接。当然，通过修改部分代码是可以使用USB大容量存储模式并且ADB连接的；  

###第二种方法的缺点与优点
使用xiaolu的字库来进行汉化Recovery的话，中文显示清晰，可以使用USB大容量存储模式并且ADB可以连接，只不过在输出信息时长度太大的话会在边缘处丢失一部分字符；个人来说，我是比较倾向于第二种方法。  
