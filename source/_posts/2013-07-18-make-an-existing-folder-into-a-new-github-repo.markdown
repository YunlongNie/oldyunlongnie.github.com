---
layout: post
title: "Make an existing folder into a new github repo"
date: 2013-07-18 22:43
comments: true
categories: [Github]
tag: github 
---

I am quite new to Github and it took me 2 days to get into it. Just keep a record for future reference. ### Say if you have a foler on your machine and you'd like to creat a new repo on github server. 

###* suppose your local folder is `~/myfold/`. The first thing we do is to creat a repo on github server we call it `myfold`.

###* next we add this folder to the server. 

        $ git init
        # initialise a git
        $ git add .
        $ git commit -m "your comment"
        # commit the files
        $ git remote add origin https://github.com/YunlongNie/myfolder.git
        # point origin to the myfolder.git repo
        $ git push -u origin master

*### note that some time you may like to **remove** or **rename** the origin 

        $git remote rename <old> <new>
        $git remote remove <name>

Check out this website about [git-remote](http://git-scm.com/docs/git-remote).  


