---
layout: post
title: "多电脑编写octopress"
date: 2015-07-13 14:16:20 +0800
comments: true
categories: octopress
---

1. 建立公钥私钥

	```
	ssh-keygen -t rsa
	``` 

2. 在/Users/xujiaqi/.ssh找到id_rsa.pub文件，打记事本打开将其中全部内容复制，粘贴到github或gitcafe的SSH管理里面。

3. 检查是否可以连接到github或gitcafe

	```
	ssh -T git@github.com
	或
	ssh -T git@gitcafe.com
	```
连接成功：

	```
	Hi coderJackie! You've successfully authenticated, but GitCafe does not provide shell access.
	```

4. 将博客的源文件clone到本地的octopress文件夹内。
	
	```
	xujiaqideMac-mini:octopress xujiaqi$ git clone -b source 	git@github.com:CoderJackie/coderjackie.github.com.git octopress
	```

5. 将博客文件clone到octopress的_deploy文件夹内。
	
	```
	xujiaqideMac-mini:octopress xujiaqi$ cd octopress
	xujiaqideMac-mini:octopress xujiaqi$ git clone git@github.com:CoderJackie/	coderjackie.github.com.git _deploy
	```
6. 安装bundler,rake,如安装过则不需要

	```
	cd octopress
	sudo gem install bundler
	bundle install
	rake install （不需要，会覆盖掉原来的主题）
	```
	
7. 最后就可以在这台电脑上写博客了

	```
	rake new_post["myBlog"]
	```
	
8. 编写完博客要上传到github

	```
	rake generate
	git add .
	git commit -m "Some comment here." 
	git push origin source
	rake deploy
	```

9. 如果无法push到仓库的master分支，尝试在项目目录的.git/config中添加

	```
	[branch "master"]
	 remote = origin
	 merge = refs/heads/master
	```

	**为防止多台电脑编辑，每次编写前先要pull一下**

	```
	$ cd octopress
	$ git pull origin source  # update the local source branch
	$ cd ./_deploy
	$ git pull origin master  # update the local master branch
	```