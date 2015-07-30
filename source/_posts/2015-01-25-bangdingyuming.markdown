---
layout: post
title: "octopress绑定个人域名"
date: 2015-01-25 00:28:46 +0800
comments: true
categories: octopress
---


  
一直想拥有一个个人域名，前几天无聊去Godaddy上搜了一下，发现<http://www.xujiaqi.info>域名才20元一年，直接入手，接下来就是域名解析了。

域名解析使用的国内[DNSPOD](http://www.dnspod.cn),首先在Godaddy上修改DNS地址。

<!--more-->

1. 登录[www.godaddy.com](http://www.godaddy.com)  ！


2. 点击 Manage My Domains 

{% img top /images/2015-01-25/image1@2x.png %}

3. 点击【Set NameServers】  

{% img top /images/2015-01-25/image2@2x.png %}

4. 然后添加两个NAMESERVERS 

{% img top /images/2015-01-25/image3@2x.png %}
  
首先在[根据gitcafe](http://gitcafe.com/GitCafe/Help/wiki/Pages-相关帮助#wiki)上教程，在项目管理里添加域名，比如我添加了:

{% img top /images/2015-01-25/image5@2x.png %}


然后在[DNSPOD](http://www.dnspod.cn)上注册一个账户，然后添加域名，并添加A记录或者设置CNAME

{% img top /images/2015-01-25/image4@2x.png %}

现在你就可以在浏览器中直接打开你的域名了, 可以通过
<http://xujiaqi.info>，
<http://www.xujiaqi.info>，
<http://blog.xujiaqi.info>，
<http://m.xujiaqi.info>来打开你的博客了。
