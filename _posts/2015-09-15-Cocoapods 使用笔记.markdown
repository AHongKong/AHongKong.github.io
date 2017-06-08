---
layout: post
title:  "CocoaPods使用笔记"
date:   2015-09-15 13:40:34 +0800
---

<font color = blue> 引入第三方的步骤</font>

1. 新建 Podfile 文件
2. 编辑 Podfile 文件（pod file 格式）
3. pod install 
4. 去干别的事，等待完成。关闭项目，打开workSpace文件。


下面是使用情况，我的工程叫做PicTool，接下来我的操作都是通过终端实现：

	➜  ~ cd /Users/zhengjiaohong/Desktop/_pod/PicTool 
	➜  PicTool touch Podfile
	➜  PicTool open Podfile
	➜  PicTool pod install

open Podfile 是为了编辑Podfile，Podfile的格式如下（swift的Podfile语法稍微不同）
	
	platform :ios, “8.0”
	
	target 'PicTool' do
	    pod "AFNetworking"
	    pod “GPUImage”
	end
	
今后需要更新使用命令

	pod update
	
需要查询第三方组件可用如下命令，查看版本信息

	pod search GPUImage
	
指定第三方组件版本号的写法如下

	pod ‘AFNetworking’ //不显式指定依赖库版本，表示每次都获取最新版本
	pod ‘AFNetworking’, ‘2.0’ //只使用2.0版本
	pod ‘AFNetworking’, ‘>2.0′ //使用高于2.0的版本
	pod ‘AFNetworking’, ‘>=2.0′ //使用大于或等于2.0的版本
	pod ‘AFNetworking’, ‘<2.0′ //使用小于2.0的版本
	pod ‘AFNetworking’, ‘<=2.0′ //使用小于或等于2.0的版本
	pod ‘AFNetworking’, ‘~>0.1.2′ //使用大于等于0.1.2但小于0.2的版本，相当于>=0.1.2并且<0.2.0
	pod ‘AFNetworking’, ‘~>0.1′ //使用大于等于0.1但小于1.0的版本
	
	
关于安装和更新不更新repo 的命令（默认是会更新的）

	pod install --verbose --no-repo-update
	pod update --verbose --no-repo-update
	
	
`pod setup`

Setting up CocoaPods master repo
___
	
参考资料：

[简书作者Vinc的cocoapods](http://www.jianshu.com/p/3086df14ed08)