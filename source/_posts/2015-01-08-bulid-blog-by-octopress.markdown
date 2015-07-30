---
layout: post
title: "搭建基于octopress的个人blog"
date: 2015-01-08 00:35:45 +0800
comments: true
categories: octopress
---

想要有一个自己的独立博客是很久之前的事。

以前也在其他网站上写过自己的博客，但总觉得用的不顺手，感觉少了归属感，最主要是提供的界面感觉都不怎么好。

最近想学学**Git**，知道了**Github**，开始以为就是个代码仓库，后来才发现还提供了page服务，可以用来在上面搭建自己的**独立博客**。

在Github上搭建博客可以利用[Jekyll](https://github.com/mojombo/jekyll/wiki)或者[Octopress](http://octopress.org/)，Octopress是在Jekyll上建立起来的，即使没有网站设计经验的人也能够快速搭建起自己的博客。

<!--more-->

Jekyll和Octopress都是利用**Ruby**实现的，因此在搭建自己博客的过程中难免要接触到一些Ruby的东西，嗯，这说不定也是一个让自己开始了解Ruby的契机。

整个博客的内容和设置都是通过Git进行版本管理的，其中当然需要了解一些基本的Git操作，其实也没有几个常用的命令。

Mac OS 10.10.1

下面是我用Octopress搭建博客的过程:

##安装和设置Git


##安装Ruby环境

##安装Octopress

先通过Git从Github上克隆一份Octopress

    git clone git://github.com/imathis/octopress.git octopress

然后安装一些依赖的工具

    cd octopress
    ruby --version 
    gem install bundler
    bundle install

安装Octopress默认的Theme

    rake install

##配置Octopress

##开始写博文


##预览效果

在修改设置或者写完文章后，想看看具体效果，可以通过如下命令来完成:

    rake generate
    rake preview

然后在浏览器中[打开](http://localhost:4000/)来看一看效果。

##将博客部署到Github上

在预览的效果符合自己的预期后，就可以通过如下命令将内容部署到Github上了。

第一次部署前需要先要在Github上创建一个**username.github.com**的repository，
然后通过`rake setup_github_pages`将自己的Blog与上述的repository关联起来。
在其过程中根据提示输入**username.github.com**。

然后就可以通过下面的命令来部署自己的博客内容至Github了:

    rake deploy
    git status
    git add .
    git commit -a -m 'comment'
    git push origin source

##开始浏览自己的博客

在浏览器的地址栏中输入**username.github.com**，打开的网站就是自己的博客了，此刻一个独立博客就如此问世了!

以后就可以享受这种以Geek方式来写博客的生活了!
