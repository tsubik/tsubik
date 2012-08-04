--- 
layout: post
title: "Powershell script to bring your publish on the next level"
categories: ["post"]
tags: ["powershell",".NET"]
date: 2012-08-04
author: "Tomasz Subik"
---

<p>
How many times during development stage your project file broke after merge? Everything looks great since you deploy 
app on test or production server. You finish your work go home and spend 
nice evening with your girl or friends. But next day during checking new 
issues from quality team you might see something like that:
</p>
<!--more-->
![Powershell_01](/images/blog/powershell_01.png "View not found")
<p>
Or complaints why everything looks so fucked up!
</p>
<p>
What the fuck?! That suppose to work perfectly fine! You go to Visual Studio looking for problematic files and baam! Founded!!
</p>
![Powershell_02](/images/blog/powershell_02.png "View not found")

<p>
Your view is not added to project. It is that simple and stupid. It can be any file - view, stylesheet, script file and bunch of others.
</p>
So we need simple solution to do something that it could never happen again.
<p>
Problem is trivial and solution is so. All you have to do is check if all files listed in project catalog are included in project configuration file. You can write simple console app to check it and warn you about files you might miss.
</p>
<p>
But instead of, I prepare some powershell script. This is my first powershell script so any improvements are welcome (please do it directly on gist).
</p>
<div style="clear: both;"><script src="https://gist.github.com/3156783.js"> </script></div>