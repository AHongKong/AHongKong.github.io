---
layout: post
title:  "gdb/adb/lldb"
date:   2016-08-03 13:40:34 +0800
---


[GDB](http://linuxtools-rst.readthedocs.io/zh_CN/latest/tool/gdb.html)
是一个由GNU开源组织发布的、UNIX/LINUX操作系统下的、基于命令行的、功能强大的程序调试工具。 对于一名Linux下工作的c++程序员，gdb是必不可少的工具；

[Android 调试桥 (adb)](https://developer.android.com/studio/command-line/adb.html?hl=zh-cn) 
是一个通用命令行工具，其允许您与模拟器实例或连接的 Android 设备进行通信。


[LLDB](http://lldb.llvm.org/tutorial.html)
是个开源的内置于XCode的具有REPL(read-eval-print-loop)特征的Debugger，其可以安装C++或者Python插件。

开发iOS程序的时候常常会用到调试跟踪。xcode里有内置的Debugger，老版使用的是GDB，xcode自4.3之后默认使用的就是LLDB了。