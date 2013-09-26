---
layout: post
title: "Redirect personal website to here"
date: 2013-07-19 02:30
comments: true
categories: [website]
tags: html 
---

### my old personal website is `stat.ubc.ca/~yunlong.nie` and when visitors come to this web page, I'd like to guide them to this new blog automatically. 

Here we need to make use `.haccess` file. 

          $ cd public_html/
          $ vi .haccess
          # put the following code into this file
          Redirect 301 /~yunlong.nie/ http://yunlongnie.github.io/
 
Bingo! This [website](http://www.uvm.edu/webguide/?Page=redirects.html&SM=urlsubmenu.html) has more details.  

         


