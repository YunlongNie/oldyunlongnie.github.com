---
layout: post
title: "Find by file extension and do sth"
date: 2013-07-19 00:03
comments: true
categories: [linux]
tags: bash 
---

### say we wanna find all the file with the same extension within one folder and do sth else

         cd ~/Downloads;
         find . -iname "*.mp3" -exec mv {}  ~/Dropbox/OwnCloud/mp3/ \;
         # first locate all the files with .mp3 then mv to a new folder

         find . -iname "*.mp3" -exec rm {}  \;
         # first locate all the files with .mp3 then delete them all

 
         


