---
layout: post
title: "Website: Link to your own post"
date: 2013-07-21 00:21
comments: true
categories: website 
tags: octopress
---

Sometimes, we need to link to our own post. You can, of course, link with `http://` but I'd rather use a shorter one.

```
my previous [post]({{ root_url }}/blog/2013/07/18/sidebar/)

```
Note that the default root directory is `/`, so you need to add {{ root\_url }} before `/blog`
 
my previous [post]({{ root_url }}/blog/2013/07/18/sidebar/)
