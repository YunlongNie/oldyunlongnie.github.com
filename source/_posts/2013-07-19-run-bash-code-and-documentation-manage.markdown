---
layout: post
title: "Run Bash Code and documentation manage"
date: 2013-07-19 12:00
comments: true
categories: linux 
tags: bash
---

I tried to manage my chrome download folder. Say, put all the mp3 files into one folder and all the pdf to another folder. We can simply write a   **bash** code script and make use of the `source` command.

My script is like this: 

          find ~/Downloads -iname "*.mp3" -exec mv {}  ~/Dropbox/OwnCloud/mp3/ \;
          find ~/Downloads -iname "*.torrent" -exec rm {} \;
          find ~/Downloads -iname "*.pdf" -exec mv {} ~/Downloads/PDFs/ \;

save the above script in a txt file named `johadload.txt` and you can simply run 

         source johadload.txt

bingo! 


