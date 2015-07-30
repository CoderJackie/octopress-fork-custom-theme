---
layout: post
title: "设置UIAlert按钮颜色"
date: 2015-07-27 11:31:07 +0800
comments: true
categories: iOS
---


需求：将UIAlertView的button文字改成指定颜色：

{% img top /images/2015-07-27-1/image1.png %}

代码如下：

```
    UIAlertView *alertView = [[UIAlertView alloc] initWithTitle:@"" message:@"设置按钮为红色" delegate:nil cancelButtonTitle:@"我是红色" otherButtonTitles:nil];
	    
    [[UIView appearance] setTintColor:[UIColor redColor]];
	   
    [alertView show];  	
    
```


然后要在点击按钮的时候将tintColor置空，因为默认UIView的appearance是为nil的：


```
	+ (void)alertView:(UIAlertView *)alertView didDismissWithButtonIndex:(NSInteger)buttonIndex
	{
		if (buttonIndex == [alertView cancelButtonIndex]) {
			[[UIView appearance] setTintColor:nil];
		}
	}

```
	
	