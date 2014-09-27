--- 
layout: post
title: "Port your cordova multi-platform hybrid app to Windows Phone 8.1"
tags: ["cordova","phonegap","ionic", "windows phone"]
date: 2014-09-27
author: "Tomasz Subik"
permalink: /blog/port-your-cordova-multi-platform-hybrid-app-to-windows-phone-8.1/
---

Apache Cordova team announced that in [version 3.6.3](http://cordova.apache.org/announcements/2014/09/22/cordova-361.html) developing applications for windows phone 8.1 is officially supported. Is it end of the katatonia of developers wanting to port their applications to microsoft phone platform? Let's find out.

<!-- more -->

#Adding platform

```
cordova platform add windows
```

Why windows? Because of support for some thing called 'Universal App', which means you can develop app once and with having common codebase run it on Windows 8, Windows 8.1 and Windows Phone 8.1. If you look at the created solution there are few projects targeting different platforms and common codebase.

![Universal App structure](/images/blog/universalapp_structure.png)

First thought - "Great I will have Windows desktop app also with some little efforts". Let's run app on emulator (be aware of special switches between target platforms --phone --win)

```
cordova run windows -- --phone
```

And... **It is not working :(**. App crashes after open, I did not know what happened.

#Visual Studio for rescue

Running application from visual studio will show us what actually happens

>0x800c001c - JavaScript runtime error: Unable to add dynamic content. A script attempted to inject dynamic content, or elements previously modified dynamically, that might be unsafe. For example, using the innerHTML property to add script or malformed HTML will generate this exception. Use the htoStaticHTML method to filter dynamic content, or explicitly create elements and attributes with a method such as createElement.  For more information, see http://go.microsoft.com/fwlink/?LinkID=247104.

What!? Following link from error message you find out about automatic script filtering, maniulating DOM in 'secure way' and much more. That means jquery - doesn't works, angularjs - doesn't works, ionic - doesn't works. You have to change all 'insecure' parts of libraries code due to get them works. But there are many more restrictions developing WinJS applications and right now If you want to create app this way you will have to follow microsoft rules. So I gave up!

#So what now?

Another approach which I prefer and **it is working for my Ionic application** is using old wp8 platform.

```
cordova platform add wp8
```

Then follow these few steps:

- Retarget to Windows Phone 8.1. Open solution in visual studio, project properties.![VS retarget](/images/blog/vs_retarget.png)
- If you are not using cordova 3.6.3 change all "execScript" to "eval" for the cordovalib
- Replace XHRHelper.cs with [this one](https://gist.github.com/tsubik/17598d9e142a6876a300) (I found it out somewhere on the web)

That's it! Now you can run emulator from Visual Studio and application works. It might not look like the same as on other devices you have to adapt it to IE11 :/.



