---
layout: post
title: "[浅谈]如何汉化CWM Recovery"
description: ""
category: 
tags: [技术交流]
---
{% include JB/setup %}
##简述Recovery汉化的方法
Recovery汉化据我所知有两种方法，第一种是使用chinese_gen.rb脚本\(出处不明，不过在github上最早放出源码的是[tewilove](https://github.com/tewilove/android_recovery_with_chinese),在于2010-09-16放出源码的\)来生成中文字库并修改graphics.c文件使其调用chinese.c/chinese.h来达到显示中文的目的，第二种则是使用[xiaolu](https://github.com/xiaolu/cmw_recovery_cn)的中文字库和修改graphics.c文件来实现的。
  
###第一种方法的缺点与优点
使用chinese_gen.rb的方法汉化Recovery的话，中文可以显示，但是显示字体会有瑕疵，并且不能使用USB大容量存储模式和ADB无法连接。当然，通过修改部分代码是可以使用USB大容量存储模式并且ADB连接的；  
  
###第二种方法的缺点与优点
使用xiaolu的字库来进行汉化Recovery的话，中文显示清晰，可以使用USB大容量存储模式并且ADB可以连接，只不过在输出信息时长度太大的话会在边缘处丢失一部分字符；个人来说，我是比较倾向于第二种方法。  
  
##如何汉化Recovery
下面将告诉大家两种汉化的使用方法。
  
###1.使用chinese_gen.rb
* 把chinese_gen.rb脚本下载下来先,[点击此处下载!](https://github.com/tewilove/android_recovery_with_chinese/archive/master.zip)
* 脚本存放在minui文件夹里，需要安装好ruby环境才可使用，不知到怎么安装的话那自己谷歌去。。
* 双击运行，他会生chinese_custom.gperf/chinese_custom.h/chinese.bmp/chinese.preview.txt/font.h，其中chinese_custom.gperf/chinese_custom.h/font.h就是我们需要的文件。
* 用minui文件夹里的graphics.c替换原本的graphics.c,并把chinese.c/chinese.h一同复制过去.
* 在Android.mk里面的LOCAL_SRC_FILES中加上chinese.c；
* 重新编译一下，中文显示出来了吧,不过字体有点瑕疵，我编译的ADB和USB大容量存储模式都不可使用，你自己测试下吧！
  
###2.使用xiaolu的中文字库
* 这种方法就简单许多了，只需替换几个文件即可，让我们下载好中文字库先,[点击此处下载!](https://github.com/xiaolu/cmw_recovery_cn/archive/master.zip)
* 把minui文件夹的graphics_cn.c/font_cn_tiny.h/font_10x18_cn.h复制到CWM recovery源码的minui文件夹里.
* 把graphics_cn.c重命名为graphics.c，此文件本身调用的字库是删减版的，不全面，如果你的中文显示不全，那就需要把里面的font_cn_tiny.h替换为font_10x18_cn.h即可；
* 重新编译一次，中文成功显示吧，并且无瑕疵，ADB和USB大容量存储模式可以使用。建议使用这种方法!!!
  
#####好了，已经完成上述两种汉化的方法，我仅测试了CWM Recovery 5.0.2.8 按理说是通用的，如果在CWM6中不能显示的话，适当的修改下graphics.c应该就可以了，有什么问题可以大家共同讨论，也希望大家分享更多经验。
