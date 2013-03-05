---
layout: post
title: "编译CM时出现的问题"
description: ""
category: 
tags: [技术交流]
---
{% include JB/setup %}
错误：  
`使用GCC4.7编译源码时，external/srec文件夹源码会出现以下错误，需要打补丁。`  

解决方法：  
`下载`[serc_patch.diff](files/patchsrec_patch.diff)`并把他放在external/srec目录`  
`终端输入: cd external/srec`  
`patch -p1 < serc_patch.diff`  
`rm -f serc_patch.diff`  
`cd ../..`  

