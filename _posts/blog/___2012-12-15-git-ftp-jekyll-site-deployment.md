--- 
layout: post
title: "Using git-ftp to speed up jekyll generated site deployment"
categories: ["post"]
tags: ["git","git-ftp"]
date: 2012-12-15
author: "Tomasz Subik"
permalink: /blog/git-ftp-jekyll-site-deployment/
---

To create my personal website I am using great static site generator tool called jekyll. I mentioned it in my [inital post][Post about Jekyll]. This tool is very simple and have everything you need to create simple websites or blogs. Everytime you need to update your website, the best way was just connect via ftp client and copy all files from _site directory where all generated files are. It takes not very long time, it's quick, but there is a better solution out there and it's called git-ftp. 

git-ftp
-------

You can check out this tool on [github][Git-FTP Github]. It is a bash script, a kind of git plugin to upload new commits to chosen remote location using ftp. What is great about it that only changes are transfered to the server and that is why git is using for.

Installation
-------

For install just read the install guide on the project site. You can use it on Windows, linux, macos. I tried to run it on Windows, but with no luck (I end up with msysgit, cygwin etc., still something missing), so I decided to switch to Ubuntu for some development processes.

Usage with jekyll
-------

Generally how to use this tool you can read manual, it is very good and understandable. I want to show how I use it along with jekyll.

Configure first
-------
Ok. Before starting let's configure.

You have two options here.

First option 

If you have whole page with generated output (_site dir) under source control. You can init git ftp on whole repository and choose _site directory as a sync directory

<code>$ git config git-ftp.syncroot _site</code>
Only files from this directory will be uploaded on ftp server.


<!-- BEZSENSU
Second 

If you do not have output directory under source control. You can create git repository for output _site directory and whole repository will be synced with ftp.

I've chosen second option, I just don't want to have generated files on remote git repository.

Ok. So. Configuration.

Wait there is a litte catch here. I cannot create git repository inside _site folder because everytime I changed something in my website jekyll recreates this folder and my git repo will be gone! So I need create repo somewhere else. 

Let's do this.

I've created catalog for such a repos ~/dev/git.

$ cd ~/dev/git
$ mkdir tsubik.com.git && cd tsubik.com.git
$ git init --bare
$ git config core.bare false
$ git config core.worktree ~/dev/tsubik/_site

Ok. I've created bare git repository and changed worktree to point jekyll output directory _site.

Let's make initial commit

<code>$ git add . && git commit -m"initial commit"</code>

Unfortunatelly in time when I wrote this post git-ftp doesn't work with repositories which have worktree outside.

So another workaround :/.

Let's clone our created repository

<code>$ git clone tsubik.com.git tsubik.com.git_cloned</code>

Ok. Now it's time to config git-ftp in cloned repository. For the first init

$ git ftp init -u jaymz85_master -p - ftp://ftp.tsubik.com/tsubik.com/wwwroot

Then to automate process of pushing changes to ftp I've created simple bash script which I added to my site main directory

cd ~/dev/git/tsubik.com.git
git add . && git add -u && git commit -m"
cd ~/dev/git/tsubik.com.git_cloned
git pull origin master
git 

-->

[Post about Jekyll]: /blog/new-personal-website-released/
[Git-FTP Github]: https://github.com/resmo/git-ftp 