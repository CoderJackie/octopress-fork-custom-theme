---
layout: post
title: "禁止某个Method"
date: 2015-07-27 15:57:48 +0800
comments: true
categories: iOS
---


有时，不希望别人使用某个父类方法，比如，写了一个继承NSObject的类，不希望别人用init方法实例化。

那么可以通过这个方法禁止掉，并且报错提示给别人：

```
	#ifndef DOXYGEN_SHOULD_SKIP_THIS
	// Disallow init and don't add to documentation
    - (id)init __attribute__((unavailable("init is not a supported initializer for this class.")));
	#endif

```

{% img top images/2015-07-27-2/image1.png%}

{% img top images/2015-07-27-2/image2.png%}