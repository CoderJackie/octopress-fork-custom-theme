---
layout: post
title: "网页唤醒iOS应用"
date: 2015-02-09 03:39:49 +0800
comments: true
categories: iOS
---

##应用间通讯（Inter-App Communication）

---

前段时间在逛一号店时候发现有个活动，4999抢iPhone6，只支持手机端，扫描二维码后发现是打开个网页，所以就想到在电脑上打开网页会不会更容易抢到iPhone呢。

<!--more-->

首先，用二维码扫描软件扫描发现其地址为 <http://m.yhd.com/sale/134743>,点击4999抢iPhone会跳到iTunes下载页，然后试了下在手机的safari中打开这个[网址](http://m.yhd.com/sale/134743)是跳到一号店app中，之前用百度地图和账上生活时遇到过这种情况，但是并没有去研究怎么实现。

回到正题，在点击4999抢iPhone的链接后查看了一下他网页的源码:

 ```javascript
 
 	<!DOCTYPE HTML>
	<html>
	<head>
	    <meta charset="UTF-8">
	    <meta name="Description" content="手机购物，手机团购，进口，食品，饮料，母婴，超市，1号店 "/>
		<meta name="Keywords" content="手机购物，手机团购，进口，食品，饮料，母婴，超市，1号店 "/>
	    <title>促销活动,掌上一号店,掌上1号店,比超市更便宜，-1号店</title>
	    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
	    <meta name="apple-mobile-web-app-capable" content="yes">
	    <meta name="apple-mobile-web-app-status-bar-style" content="black">
	    <meta name="format-detection" content="telephone=no">
	    <script type="text/javascript" src="http://image.yihaodianimg.com/mobile-website/js/tracker_top.js"></script>
	<script>var _hmt = _hmt || [];_hmt.push(['_setCustomVar', 4,  'yihaodian', 'yihaodian', 1]);</script></head>
	<script>
	    var tu="10305758297";
	    var sd="null";
	</script>
	<body >
	
	
	<script type="text/javascript" src="http://image.yihaodianimg.com/mobile-website/js/jq.1.7.min.js?v=20140408"></script>
	<script type="text/javascript" src="http://image.yihaodianimg.com/mobile-website/js/jquery.lazyload.min.js"></script>
	<script type="text/javascript" src="http://image.yihaodianimg.com/mobile-website/js/jquery.cookie.js"></script>
	<script type="text/javascript" src="http://image.yihaodianimg.com/mobile-website/js/tracker.js"></script>
	<script type="text/javascript" src="http://image.yihaodianimg.com/mobile-website/js/tracker_hijack.js"></script>
	<script type="text/javascript">
	goapp('9');
	function goapp(type) {
	//1-cms;2-商品详情；3-团购；4-摇一摇；5-商品搜索；6-赠品；7-n元n件；8-满减;9-首页
	 if(type==1){
	     cms('0','0','false');
	 }else if(type==2){
	     prodetail('0','0','null','null');
	 }else if(type==3){
	     grpetail('0','0');
	 }else if(type==4){
	     rockhomepage();
	 }else if(type==5){
	     search('0');
	 }else if(type ==6){
	     promofree();
	 }else if(type ==7){
	   promonn('0','0');
	 }else if(type ==8){
	    promocutoff('0')
	 }else if(type ==9){
	    goindex();
	 }
	
	}
	//cms活动页
	function cms(cmsid,provinceId,idexistflag) {
	    
	    urlGo("yhd://cms/"+cmsid+"_"+provinceId);
	    
	    var url;
	    if(idexistflag=='true'){
	      url ="urlGo('http://m.yhd.com/mw/cms/"+cmsid+"/20/"+provinceId+"')";
	      //url ="urlGo('http://m.yhd.com/mw/newcms/"+cmsid+"?provinceId="+provinceId+"')";
	    }else{
	     url ='urlGo("http://m.yhd.com/mw/d")';
	    }
	     setTimeout(url,3000);
	}
	//商品详情
	function prodetail(proid,provinceId,promotionid,pmid) {
	    var promotionidwebsite = promotionid;
	    if(promotionidwebsite ==null || promotionidwebsite=='null'){
	      promotionidwebsite ="";
	    }
	    
	    if(promotionid ==null || promotionid=='null'){
	      promotionid ="";
	    }else{
	      promotionid="_"+promotionid
	    }
	    if(pmid ==null || pmid=='null'){
	    	pmid="_0";
	    }else{
	    	pmid="_"+pmid;
	    }
	    var url="";
	    if(tu && sd){
	    	url="http://m.yhd.com/mw/productsquid/"+proid+"/"+provinceId+"/20/"+promotionidwebsite+"?tracker_u="+tu+"&source_id="+sd;
	    }else{
	    	url="http://m.yhd.com/mw/productsquid/"+proid+"/"+provinceId+"/20/"+promotionidwebsite;
	    }
	    // var url ="urlGo()";
	      
	        urlGo("yhd://product/"+proid+"_"+provinceId+promotionid+pmid);
	       
	    setTimeout(function(){
	    	urlGo(url);
	    },3000);
	}
	//团购
	function grpetail(grpid,provinceId) {
	     
	       urlGo("yhd://groupon/"+grpid+"_"+provinceId);
	     
	    var url ="urlGo('http://m.yhd.com/mw/groupdetail/"+grpid+"/"+provinceId+"')";
	    setTimeout(url,3000);
	}
	//摇一摇
	function rockhomepage() {
	 
	    urlGo("yhd://rockhomepage/");
	  
	    setTimeout('urlGo("http://m.yhd.com/mw/d")',3000);
	}
	//商品搜索
	function search(keyword) {
	     
	    urlGo("yhd://search/"+keyword+"_1_1");
	    
	    var url ="urlGo('http://m.yhd.com/mw/search?keyword="+keyword+"&searchid=1&serchtype=')";
	    setTimeout(url,3000);
	}
	//赠品促销
	function promofree() {
	    
	    urlGo("yhd://promofree/1_1");
	    
	    setTimeout('urlGo("http://m.yhd.com/mw/d")',3000);
	}
	//n元n件促销
	function promonn(promotionid,levelid) {
	     
	    urlGo("yhd://promonn/"+promotionid+"_"+levelid);
	     
	    setTimeout('urlGo("http://m.yhd.com/mw/d")',3000);
	}
	//满减列表促销
	function promocutoff(promotionid) {
	    
	    urlGo("yhd://promocutoff/"+promotionid);
	    
	    setTimeout('urlGo("http://m.yhd.com/mw/d")',3000);
	}
	//首页
	function goindex() {
	 
	      urlGo("yhd://home/");
	 
	    setTimeout('urlGo("http://m.yhd.com/mw/d")',3000);
	}
	
	function urlGo(url){
	    setTimeout(function(){
	        window.location = url;
	    },10);
	} 
	</script>
	</body>
	</html>
 
 ```
 
 一号店的工程师还挺负责的，都写上了注释。原来他是用 [yhd://](yhd://)这个协议唤醒了app，通过搜索引擎一番搜索才知道，原来这个就是通过URL scheme来打开的，相信做过app分享的都不陌生，通过设置程序的URL scheme来打开微信、微博等社交软件，但是之前不知道这个scheme还可以通过网页来唤醒app。看到苹果官方文档，原来这个就是应用间通讯(Inter-App Communication)。通过在appdelegate中可以对链接进行判断跳转，官方示例：
 
```C
	- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url
	        sourceApplication:(NSString *)sourceApplication annotation:(id)annotation {
	        
	    if ([[url scheme] isEqualToString:@"todolist"]) {
	        ToDoItem *item = [[ToDoItem alloc] init];
	        NSString *taskName = [url query];
	        if (!taskName || ![self isValidTaskString:taskName]) { // must have a task name
	            return NO;
	        }
	        taskName = [taskName stringByReplacingPercentEscapesUsingEncoding:NSUTF8StringEncoding];
	 
	        item.toDoTask = taskName;
	        NSString *dateString = [url fragment];
	        if (!dateString || [dateString isEqualToString:@"today"]) {
	            item.dateDue = [NSDate date];
	        } else {
	            if (![self isValidDateString:dateString]) {
	                return NO;
	            }
	            // format: yyyymmddhhmm (24-hour clock)
	            NSString *curStr = [dateString substringWithRange:NSMakeRange(0, 4)];
	            NSInteger yeardigit = [curStr integerValue];
	            curStr = [dateString substringWithRange:NSMakeRange(4, 2)];
	            NSInteger monthdigit = [curStr integerValue];
	            curStr = [dateString substringWithRange:NSMakeRange(6, 2)];
	            NSInteger daydigit = [curStr integerValue];
	            curStr = [dateString substringWithRange:NSMakeRange(8, 2)];
	            NSInteger hourdigit = [curStr integerValue];
	            curStr = [dateString substringWithRange:NSMakeRange(10, 2)];
	            NSInteger minutedigit = [curStr integerValue];
	 
	            NSDateComponents *dateComps = [[NSDateComponents alloc] init];
	            [dateComps setYear:yeardigit];
	            [dateComps setMonth:monthdigit];
	            [dateComps setDay:daydigit];
	            [dateComps setHour:hourdigit];
	            [dateComps setMinute:minutedigit];
	            NSCalendar *calendar = [s[NSCalendar alloc] initWithCalendarIdentifier:NSGregorianCalendar];
	            NSDate *itemDate = [calendar dateFromComponents:dateComps];
	            if (!itemDate) {
	                return NO;
	            }
	            item.dateDue = itemDate;
	        }
	 
	        [(NSMutableArray *)self.list addObject:item];
	        return YES;
	    }
	    return NO;
	}

```

可以用这个地址打开app，并且在appdelegate中对地址进行分析，得到产品id，活动类型，来负责跳到不同界面。

最后吐槽一号店，活动前一天并没有限制必须跳转到app，所以我保存了iPhone抢购的详情页，第二天抢购的时候用电脑浏览器刷新时间，iPhone一秒钟全部抢光，但是已售出才10几件，明显是在坑人啊。第二轮抢购发现他限制必须进入app抢购，这明显阻挡不了程序员啊，通过charles分析抓包找到了真是地址，发现第二轮已经去掉了已售出记录，大公司还来这一套，可惜了我定了5个闹钟，唯一收获就是学到了通过设置URL scheme在其他应用来唤醒app。


官方文档 [Inter-App Communication](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html)