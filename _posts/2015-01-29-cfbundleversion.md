---
layout: post
title: "坑爹的苹果CFBundleVersion"
description: ""
category: 
tags: []
---
{% include JB/setup %}

####坑爹的CFBundleVersion 错误
经常在发新版本的时候会受到"Invalid Binary", CFBundleVersion出错,blabla,告诉你一大堆规则，然后让你去改CFBundleVersion,改了以后又这样，如此循环反复，直至人吐血奔溃！

####啥是CFBundleVersion？
plist里面会有两个version:

1. 一个是"Bundle version string, short",也就是"General"里面的Verion,这个是给AppStore看的，上传的时候也是靠这个字符串来匹配你的App.这个与itunesconnect里面的一致就可以了，每次上传新build的时候这个字段不用改。如果是上传到新的version，这个字段要和新version的build version字段一样。
2. 另外一个是"Bundle verion", "General"里面显示为Build, itunesconnect里面检测出错的时候会识别为CFBundleVersion,也是本片要吐槽的对象。


如果每次你上传新build的时候这个字段的值没有增加，xcode validate的时候会检测出来并报错，你按规则任意把某个section增加一定的值就可以了。比如1.0.150129可以增加为1.0.150130, 这样就可以上传build了。

####解决CFBundleVersion的问题
问题来了，itunesconnect经常抽风啊，你xcode validate过了，上传了，它不一定让你过啊，这种bug，绝对是无证程序员的错啊！

针对这种傻逼的bug，如果你有时间，可以慢慢尝试，找出它抽风的规律，反正它会不停的说你错了，重新改吧。


*吐槽哥对付这个坑有个简单的办法，每次增加第一个section就可以了!*

> eg， 前面上传了1.0.150129,那么你下一个build直接上2.0.150129. 

不
要浪费时间去尝试什么"1.0.150130","1.1.150129","1.3.150130"了,相信我，不会坑你的。

哥在这里吐过血，现在写这篇文章就是想让你们能从我身上踩过去，不谢！
