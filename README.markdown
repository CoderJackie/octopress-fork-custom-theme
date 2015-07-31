1. 使用方法：
```ruby
 git clone git@github.com:CoderJackie/octopress-fork-custom-theme.git octopress
 
```
 
2. clone后进行步骤：
	```ruby
    * 修改_config.yml中的title,subtitle,author,email.
    * 删除Rakefile中：
	  
			system "git remote add gitcafe git@gitcafe.com:coderJackie/coderJackie.git >> /dev/null 2>&1"
			 system "git push -u gitcafe master:gitcafe-pages"
	  
    * 修改 `/Users/xujiaqi/Desktop/octpress/source/_includes/post/sharing.html`，替换有言评论id，定制百度		分享。
    
	```


3. 创建仓库：```userName.github.com```userName为github账户名,输入完仓库名直接creat。
4. 回到终端，分别输入：

 ```ruby
 sudo gem install bundler
 bundle install
 rake setup_github_pages

 ```
 
5. 提示输入仓库名,username替换成github用户名:
 
 ```ruby
 git@github.com:username/username.github.com.git
 ```
 
6. 生成静态页面，并且上传到master分支
 
 ```ruby
 rake generate
 rake deploy
 ```
 
7. 上传博客源码到source分之
 ```ruby
 git add .
 git commit -m "content"
 git push origin source
 ```
 
