---
layout: post
title: "Hello Octopress"
date: 2015-08-25 12:48:28 +0800
comments: true
categories: 
---

其实很早之前我就想写一个自己的博客来记录我看到或学到的点点滴滴，可患有晚期懒癌的我迟迟都没有行动起来。是时候迈出第一步了，相信任何事情开头总是最难的，之后也便是顺水推舟的事情了。  
   
之前使用过[Blogspot](https://www.blogger.com)，但是被GFW墙了，还是决定自己搭建一个比较方便，恰好在网上看到[Octopress](http://octopress.org/)，感觉一下子就被它多简洁吸引住了，Octopress是基于Jellyll的静态页面博客，使用Markdown来生成页面也省了很多排版的琐事。  
  
接下来讲一下基本步骤
### 创建
首先你必须要安装了[Git](http://git-scm.com/)  
其次，如果没有rbenv的话也需要安装，这是在osx下安装的命令
```
brew update
brew install rbenv
brew install ruby-build
```  
然后照以下步骤初始创建博客
```
git clone git://github.com/imathis/octopress.git octopress
cd octopress
gem install bundler
rbenv rehash
bundle install
rake install # 安装Octopress默认主题
```  
值得注意的是由于访问https://rubygems.org 不稳定，如果在运行bundle install出现资源获取问题时，建议把Gemfile的source指向 http://ruby.taobao.org 的镜像就可以解决问题了
###发布
这一步就是把刚刚建立的博客发布到Github Pages上  
首先你要在Github上创建一个repo，命名规则是`username.github.io`  
接着就可以运行`rake setup_github_pages`，它会帮你设置好一切配置    
`rake generate`会把生成的静态博客拷贝到`_deploy/`里  
`rake preview`可在本地4000端口下预览  
`rake deploy`会把`_deploy/`里的内容push到master分支里，发布成功！  
**但是**最后别忘了commit你的source code
```
git add .
git commit -m 'your message'
git push origin source
```
###基本操作
这里大致写一下博客的一些基本操作命令
#####新建文章
`rake new_post["title"]`可以新建一篇文章存于`source/_posts`文件夹下，文章的命名格式为`YYYY-MM-DD-post-title.markdown`，其中日期能帮助博客文章的排序
#####新建板块
`rake new_page[super-awesome]`会为你在导航栏创建一个新的板块  
  
那基本就介绍到这里了 希望能有所帮助
