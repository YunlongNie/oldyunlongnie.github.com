---
layout: post
title: "github with jeklly boostrap"
date: 2013-07-17 01:51
comments: true
categories: [Blog] 
---


This is a record about how I set up this blog and because this is quite new to me, it's probably a good idea to write the whole process down for reference in the future.   

##  Preparation 
* first set up an account in [github](https://github.com/). You can follow the tutorial [here](https://help.github.com/articles/set-up-git).
* highly recommend you [set up the ssh key](https://help.github.com/articles/generating-ssh-keys) too. 

## Creat your website repo
next creat a repo called USERNAMR.github.com. In my case, since my username is YunlongNie. It will be yunlongnie@github.com. You have two choices here. 
    
* a simple one is to make use of [github pages](http://pages.github.com/). 
* a less simple one is to use [jeklly boostrap](http://jekyllbootstrap.com/).  Next I will focus on this option. 

### install jekyll-boostrap


        $ git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.com  
        $ cd USERNAME.github.com 
        $ git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git  
        $ git push origin master


### check out your wesite in the local browser. 

Go to the folder USENAME.github.com first. 


        $ cd USERNAME.git.hub.com
        $ jeklly  server
You can check it out on this website [http://localhost:4000/](http://localhost:4000/). 
If you have no Ruby and RubyGems intalled. Go to [jekyll](http://jekyllrb.com/) webiste and there is a page for [isntallation](http://jekyllrb.com/docs/installation/).  

### how to post?
Notice there is a rakefile in your USERNAME.github.com folder. You **must** have this file to creat a new post. 

        $ cd USENAME.github.com
        $ rake post title="your title"

the codes above will creat a markdown file in the folder `\_post/` with a filename yyyy\-mm\-dd\-title\.md, say 2013\-7\-16\-first\-blog\.md. The contents will be like blow. 
        
        
        layout: post
        title: "your title "
        description: ""
        category: 
        tags: [ ]
        

then you can edit this md file to make a post. For example, set up your categories and tags. 

### update the post into remote repo in github
remember all the things we have done so far updates only on your local machine and you can only see it from [local server](http://localhost:4000/). Next we will try to make them online so anyone can see your website on http://USERNAME.github.io/. 

* first make sure you set up a repo in github called exactly USERNAME.github.com. 
* commit your local changes with a comment.


        $git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git
        $git add .
        $git commit -m "your comment"



* push the master


       $git push origin master


check out if your files in the github repo get updated.

### merge the files in the remote server with local files. 
some times files are edited directly on github repo, making the files on server latest version. You need to **merge** the data from remote server into your local machine. 

       $git pull origin master 



