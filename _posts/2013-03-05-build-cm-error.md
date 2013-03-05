---
layout: post
title: "编译CM时出现的问题"
description: ""
category: 
tags: [技术交流]
---
{% include JB/setup %}
错误：
<code>
frameworks/base/include/utils/KeyedVector.h:193:31: note: declarations in dependent base ‘android::KeyedVector<android::String8, android::sp<AaptDir> >’ are not found by unqualified lookup
frameworks/base/include/utils/KeyedVector.h:193:31: note: use ‘this->indexOfKey’ instead
make: *** [out/host/linux-x86/obj/EXECUTABLES/aapt_intermediates/AaptAssets.o] Error 1
</code>

修正：
> 编辑 frameworks/base/tools/aapt/Android.mk  
> 在31行后添加"-fpermissive"  
> > LOCAL_CFLAGS += -Wno-format-y2k -fpermissive  

