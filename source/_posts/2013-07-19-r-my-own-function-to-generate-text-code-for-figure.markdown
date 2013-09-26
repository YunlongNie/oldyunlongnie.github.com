---
layout: post
title: "R: my own function to generate text code for figure"
date: 2013-07-19 14:53
comments: true
categories: [r,latex] 
tags: r&latex
---

This topic belongs to the reproducable research topic. **Sweave** is actually a good way of combining R and Latex. However sometime we just need to generate a `.tex` file so that we can input into main `.tex` file. 

Here is my way: 

```
print.figure <- function(writeto,filename,placement="H",caption,label)
{
  ## writeto is the location like ~/mytex.tex
  ## filename is the pic location usually a pdf 
  ##  placement can be H or h
  sink(writeto)
  cat("\\begin{figure}[",placement,"]\n",sep="")
  cat("\\begin{center}\n",sep="")
  cat("\\includegraphics{",filename,"}\n",sep="")
  cat("\\end{center}\n",sep="")
  if(!missing(caption)) {cat("\\caption{", caption,"}\n",sep="")}
  if(!missing(label)) {cat("\\label{", label,"}\n",sep="")}
  cat("\\end{figure}\n",sep="")
  sink()
  system(paste("cat",writeto))
}
```

`sink` and `cat` can be a powerful combination. They can make latex files in R adn do a lot of things. 


