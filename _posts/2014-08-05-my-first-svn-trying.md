---
layout: post
title: 我的第一次SVN尝试
description: ""
category: 
tags: ['svn']
comments: true
---
{% include JB/setup %}
{% assign PicPath = '/temp_assets' %}

	大三下学期学院有一个软件设计课程，需要组队做一个项目，然后将内容提交到学校SVN服务器中。  
	不过我一般都是用git，虽然用的也不是很好的。就当随便学习一下，到公司还是很有可能要用到的。
	下面是一些记录，由于没有办法用学校的SVN服务器了，所以提供一个免费的SVN仓库。

[riouxsvn](http://riouxsvn.com) 注册就有四个免费仓库，每个上限50M

一个简单的使用
-----------
由于学院SVN服务器迟迟没开放，我们组早就将代码写好并整理好了。每个人的部分也分得清楚。
所以我们一开始用SVN就是checkout然后将我们的项目扔到目录下，然后就直接提交了！  
PS. 我的用的是Mac(原安装好SVN)和Ubuntu(apt-get install subversion)，没用过Win下的。

	svn checkout "http://riouxsvn.com/svn/testrespository"  

第一次checkout的时候需要填写一些用户信息等等，每个库多多少少都有些出入吧。  
PS. 如果不嫌弃速度，可以用http取代http，这样也更安全!  
当然还可以:

	svn checkout urlPath dir  # 定义文件夹名字
	svn co urlPath  # 简写

然后把我们项目内容，简单点src，拷贝到testrespository目录下，然后再

	svn add src
	svn commit -m "our code"

然后我们的任务完成了，每个人都把代码commit上去，当然一般提交前svn update一下比较好。

常用的目录结构
-----------
但我们度过愉快的几天后，实验提交的要求放出来了，里面提到需要给最后结果打上final的tag。  
然后我们不得不按出牌，也学习了一下svn开发的工作流。

根目录下一般都是三个文件夹 branches tags trunk  
像 [riouxsvn](http://riouxsvn.com) 创建的仓库的时候，是可以选择自己创建的。没有创建的话也没关系，自己创建然后add就好了。

关于三个目录的详细介绍请自行查阅资料。  
简单说一下我的理解：  
branches：分支目录  
trunk：   主干，不承担开发任务。
tags：    一些里程碑版本  

如何打tag
--------
先来说一下怎么开发吧。创建好三个目录后，根据trunk基础上创建分支。

	svn cp -m "create branch" http://svn_server/xxx_repository/trunk http://svn_server/xxx_repository/branches/dev_1_0

比如我的测试创库就是

	svn cp -m "create branch" http://riouxsvn.com/svn/testrespository/trunk http://riouxsvn.com/svn/testrespository/branches/dev_1_0

之后就是获取分支，将之前的src拷贝到dev_1_0之中
	
	cd branches
	svn co http://riouxsvn.com/svn/testrespository/branches/dev_1_0
	cd ../..  # 返回testrespository根目录
	svn mv src branches/dev_1_0
	svn commit -m "move src to dev1.0"

合并分支到主干上

	cd trunk
	svn merge --reintegrate http://riouxsvn.com/svn/testrespository/branches/dev_1_0
	svn commit -m "merge dev1.0 to trunk"

PS. 如果想合并主干上最新的代码到分支上(不一定需要执行)

	cd dev_1_0
	svn merge http://riouxsvn.com/svn/testrespository/trunk
	svn commit -m "merge trunk to dev1.0"

打tag

	svn copy http://riouxsvn.com/svn/testrespository/trunk http://riouxsvn.com/svn/testrespository/tags/final -m "final"

PS. 删除分支或tag(不一定需要执行)

	svn rm http://riouxsvn.com/svn/testrespository/branches/dev_1_0 
	svn rm http://riouxsvn.com/svn/testrespository/tags/final

PPS. 一般比较少tag叫final，只有学校课程里面那些不需要后续维护开发的项目会有吧。一般都是released1.0这样的。

版本回滚
------
如果想看最新的版本号
	
	svn up

再看看最近的一些提交版本log
	
	svn log

比如log看到的内容是：
	
	>svn log
	-------------------------------------------------------------------------
	r10 | sserhd | 2014-09-22 00:10:37 +0800 (一, 22  9 2014) | 1 line

	add rm.md
	------------------------------------------------------------------------
	r9 | sserhd | 2014-09-22 00:07:28 +0800 (一, 22  9 2014) | 1 line

	change trunk
	------------------------------------------------------------------------
	......(忽略)

回滚(r10到r9, 取消一个提交)

	svn merge -r r10:r9 http://riouxsvn.com/svn/testrespository/
	svn commit -m "back to r9"

其他的一些功能
-----------
	
	svn add * --force  # 前行add所有内容

后记
---
简单地回忆了第一次使用svn的过程，写这篇文章发现了好友很多东西还没接触过，比如版本回滚不一定是整个库，可以只会退一个文件等等。还有解决冲突等等。  

	如果文章中有什么错漏，烦请指出，谢谢。

参考
---
[关于SVN 目录结构](http://www.cnblogs.com/newstar/archive/2011/01/04/svn.html)  
[svn命令行创建和删除 分支和tags](http://blog.csdn.net/yangzhongxuan/article/details/7519948)  
[基本的工作循环](https://i18n-zh.googlecode.com/svn/www/svnbook-1.4/svn.tour.cycle.html)  
[svn代码回滚命令](http://www.cnblogs.com/jndream/archive/2012/03/20/2407955.html)  
[命令模式坚决svn树冲突](http://www.111cn.net/sys/linux/50322.htm)  
