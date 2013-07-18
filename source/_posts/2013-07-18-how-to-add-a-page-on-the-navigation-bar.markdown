---
layout: post
title: "How to add a page on the navigation bar"
date: 2013-07-18 00:21
comments: true
categories: website 
---

## Big picture 

The aim is to add links to the main navigation bar, the source page needs to be edited '/source/_includes/custom/navigation.html' which looks like:

        <ul class="main-navigation">
        <li><a href="{{ root_url }}/">Blog</a></li>
        <li><a href="{{ root_url }}/archives">Archives</a></li>
        </ul>

for example you want to add a 'About me' pages just add another line there like:
        
        <li><a href="{{ root_url }}/about">Archives</a></li>
        
but you do need to add a 'about' page in your root directory, that is, under the folder 'source/', the details can be found in this [page](http://octopress.org/docs/blogging). 

        rake new_page[about]
        # it will creat source/about/index.markdown
        rake new_page[about.markdowm]
        # it will creat source/about.markdown
        
Notice the difference between these two. 


## Step by Step
here we will show how to add a page say TA in the navigation bar step by step.

1. first creat a page called 'TA' under source 
        
        rake new_page[TA]
        # this will creat source/TA/index.markdown
        
2. edit the index.markdown as you want

3. creat a item in the '/source/_includes/custom/navigation.html' and make it like this:

        <ul class="main-navigation">
        <li><a href="{{ root_url }}/">Blog</a></li>
        <li><a href="{{ root_url }}/archives">Archives</a></li>
        <li><a href="{{ root_url }}/TA">TA</a></li>
        </ul>
4. then generate all the site and push to your github account.

        rake generate
        rake preview
        rake deploy
        
## Done!       

