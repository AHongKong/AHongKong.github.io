---
layout: post
title:  "Instruments 使用指南阅读笔记"
date:   2017-04-11 13:40:34 +0800
---

其他开发者使用Instrument分析得到的关于性能优化的建议：

`NSDateFormatter／NSCalendar`

使用懒加载的形式，用到的时候再创建，避免重复创建。

针对NSDateFormatter时间开销出了重用对象外，尽量避免采用其处理多个日期格式.当然针对日期格式处理如果需要提高更多速度，可以直接采用C,可以采用第三方库来规避这个问题..


`UIImage缓存取舍`

A：imagedNamed初始化－自动缓存到内存

B：imageWithContentsOfFile初始化－不会缓存

`主线程处理I/O`

在System Trace里面突然发现了CPU Time很低，但Wait Time很高的调用，说明在主线程处理I/O已经严重损害了app的性能,这个时候考虑把这个操作优化了.

`viewWillAppear`

针对单个view 尽量不要在viewWillAppear费时的操作，viewWillAppear在 view 显示之前被调用，出于效率考虑，在这个方法中不要处理复杂费时的事情

`Instruments 的开启方式`

	1. 在应用程序文件夹选择Xcode，我电脑的路径如下： /Applications/Xcode.app/Contents/Applications ，找到Instruments开启。
	2.运行Xcode，点击菜单栏：product／build for／profile。
	3.open /Applications/Xcode.app/Contents/Applications/Instruments.app
	
	
`根据界面提供的模版，创建一个跟踪文档`


终端使用Instruments

	➜  ~ instruments
	instruments, version 8.0 (61187)
	usage: instruments [-t template] [-D document] [-l timeLimit] [-i #] [-w device] [[-p pid] | [application [-e variable value] [argument ...]]]
	
例子

	instruments -t "Allocations" -D ~/Desktop/
	.trace 
	
使用iprofiler to measure an app’s performance without launching Instrument

	➜  ~ iprofiler
	iprofiler error: No instrument chosen
	iprofiler, version 8.0 (61187)
	Usage: iprofiler [-l] [-L] [-legacy] [-T duration] [-I interval] [-window period] [-d path] [-o basename] [-timestamp] [-activitymonitor] [-allocations] [-counters] [-leaks] [-systemtrace] [-timeprofiler] [-kernelstacks | -userandkernelstacks] [-allthreadstates] [-pmc PMC_MNEMONIC] [-listpmcs] [-a process/pid | executable [args...]]
		Refer to the man page for detailed information about each option.
	➜  ~ 

例子

	iprofiler -activitymonitor -T 5s -d ~/Desktop/ 
	
	iprofiler -timeprofiler -activitymonitor
	
	iprofiler -T 8s -d /temp -o YourApp_perf -	timeprofiler -a YourApp
	
	iprofiler -T 2500ms -o YourApp_perf -leaks -activitymonitor -a 823
	
	iprofiler -d /tmp -timeprofiler -allocations -a YourApp.app
	
	iprofiler -T 15 -I 1000ms -window 2s -o YourApp_perf -timeprofiler -systemtrace /path/to/Your.app arg1

Timeline Pane

关联dsym

Measure CPU Use
