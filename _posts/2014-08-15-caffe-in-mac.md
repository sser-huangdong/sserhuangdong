---
layout: post
title: mac上安装caffe
description: ""
category: 
tags: []
comments: true
---
{% include JB/setup %}

	Caffe是一个强大的机器学习库，是用C++实现的，也有Python wrapper，可以用python代码调用。
	我们用这个工具训练深度神经网络模型进行图片特征提取，方便我们进行图片搜索。
	鉴于网络上没有太多中文资料，特别是mac上Caffe的资料，所以我写了一下。

简介
--------
[Caffe主页](http://caffe.berkeleyvision.org/)  
[官方安装教程](http://caffe.berkeleyvision.org/installation.html)  
我的系统是mac os x 10.9.x，安装工具Homebrew和pip  

依赖包
-----

[CUDA](https://developer.nvidia.com/cuda-zone): 直接到官网下载安装即可，如果你的mac有多张显卡的话，还是要自己研究一下。  

BLAS:这个mac似乎不需要，已经预装了ATLAS了

还有Boost，OpenCV等等，不过需要特殊处理一下。

具体安装其他依赖包
--------------

####仅仅针对OpenCV的修改

	brew tap homebrew/science

同时如果使用mac预装的python，即Anaconda Python，需要修改一下OpenCV的formula  

	brew edit opencv

改变一下两个变量(不会vim操作的话，请自行学习一下)

	-DPYTHON_LIBRARY=#{py_prefix}/lib/libpython2.7.dylib
	-DPYTHON_INCLUDE_DIR=#{py_prefix}/include/python2.7

####正式安装
我们需要安装的包有

	boost snappy leveldb protobuf gflags glog szip lmdb homebrew/science/opencv

由于需要将C++依赖库改成libstdc++，所以需要改一下这些包的formula

	for x in snappy leveldb protobuf gflags glog szip boost lmdb homebrew/science/opencv; do brew edit $x; done

然后修改成一下内容：

{% highlight ruby %}
def install
    # ADD THE FOLLOWING:
    ENV.append "CXXFLAGS", "-stdlib=libstdc++"
    ENV.append "CFLAGS", "-stdlib=libstdc++"
    ENV.append "LDFLAGS", "-stdlib=libstdc++ -lstdc++"
    # The following is necessary because libtool likes to strip LDFLAGS:
    ENV["CXX"] = "/usr/bin/clang++ -stdlib=libstdc++"
    
    ...  # 本来的内容

{% endhighlight %}

之后正式安装

	for x in snappy leveldb gflags glog szip lmdb homebrew/science/opencv; do brew uninstall $x; brew install --build-from-source --fresh -vd $x; done
	brew uninstall protobuf; brew install --build-from-source --with-python --fresh -vd protobuf
	brew install --build-from-source --with-python --fresh -vd boost

PS. 如果leveldb 出现问题可以参考[homebrew leveldb](https://github.com/BVLC/caffe/issues/454)

编译安装Caffe
-----------

从github上下载[Caffe](https://github.com/BVLC/caffe/archive/master.zip)
之后解压，假设解压后的目录是caffe-master

####修改makefile.config
进入caffe-master然后创建makefile.config并进行修改

	cd caffe-master
	cp Makefile.config.example Makefile.config

之后需要进行的修改，修改python的路径

	vim Makefile.config

将里面的PYTHON_INCLUDE改成：

	PYTHON_INCLUDE := /System/Library/Frameworks/Python.framework/Versions/2.7/include/python2.7 \
	/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/numpy/core/include

当然你可能会用其他默认的Python路径，请自行修改。


####编译安装并测试

	make all
	make test
	make runtest

测试可能会失败，如果涉及到下载dropbox的内容，国内网络可能会有点困难。
我后续会把一些dropbox上的内容移动到百度云上，方便国内的同胞下载。

安装python wrapper
-----------------
进入caffe-master/python，安装python依赖包

	cd caffe-master/python
	pip install -r requirements.txt

之后是将Caffe添加到pythonpath下，当然你可以将这个包移动到/Library/Python/2.7/site-packages下。  
另一种比较简单的就是设置环境变量。我用的是iterm+oh-my-zsh所以我改的是~/.zshrc，其他请自行查阅如何修改环境变量。  
在~/.zshrc里面加上

	export PYTHONPATH=/path/to/caffe/python:$PYTHONPATH 

其实这样依然会有问题，就是因为系统预安装了numpy等等。而且系统的路径优先级会比用户包的优先级高，当然你可以修改。  
先说一下怎么查询import的numpy路径和版本吧，就是import numpy 后print numpy就能知道引用所在的路径了。

方法1：同样改PYTHONPATH

	export PYTHONPATH=/Library/Python/2.7/site-packages:$PYTHONPATH

方法2：import numpy前修改路径

	import sys
	sys.path.insert(0, '/Library/Python/2.7/site-packages')
	import numpy

方法3：使用virtualenv，请自行搜索学习。

后记
---
后面我会将dropbox的内容上传云端，并分享链接。还有有时间的话将训练模型部分的笔记整理成文章发布上来。

	时间久远，难免会有疏忽，如发现错漏，烦请指出，谢谢。

