--- 
layout: post
title: "Powershell script to bring your publish to the next level"
categories: ["post"]
tags: ["Powershell",".NET"]
date: 2012-08-04
author: "Tomasz Subik"
---

<p>
How many times during the development stage did your project file break after merge? Everything looks great until you deploy 
app on test or production server. You finish your work, go home and spend 
nice evening with your girlfrienf or friends. But next day, during checking new 
issues from quality team, you might see something like that:
</p>

![Powershell_01](/images/blog/powershell_01.png "View not found")
<!--more-->
<p>
Or complaints why everything looks like shit!
</p>
<p>
What the hell?! That supposed to work perfectly fine! You go to Visual Studio looking for problematic files and baam! Found it!!
</p>
![Powershell_02](/images/blog/powershell_02.png "Solution Explorer")

<p>
Your view is not added to the project. It is that simple and silly. It can be any file - view, stylesheet, script file and a bunch of others.
</p>
So, we need a simple solution to prevent it from happening again.
<p>
Problem is trivial and solution is so. All you have to do is check if all files listed in project catalog are included in project configuration file. You can write simple console app to check it and warn you about files you might miss.
</p>
<p>
But instead, I've prepared a powershell script. This is my first powershell script so any improvements are welcome (please do it directly on gist).
</p>
<div style="clear: both;"><script src="https://gist.github.com/3296391.js"> </script></div>

