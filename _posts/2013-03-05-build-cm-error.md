---
layout: post
title: "编译CM时出现的问题"
description: ""
category: 
tags: [技术交流]
---
{% include JB/setup %}
错误：  
`使用GCC4.7编译源码时，external/srec文件夹源码会出现错误，需要打补丁。`  

方法：  
`cd external/srec`  
`wget "https://github.com/CyanogenMod/android_external_srec/commit/6607a0a8ba8966db7f7fdb7f57928cd7fb43b4b3.diff"`  
`patch -p1 < 6607a0a8ba8966db7f7fdb7f57928cd7fb43b4b3.diff`  
`rm -f 6607a0a8ba8966db7f7fdb7f57928cd7fb43b4b3.diff`  
`cd ../..`  

