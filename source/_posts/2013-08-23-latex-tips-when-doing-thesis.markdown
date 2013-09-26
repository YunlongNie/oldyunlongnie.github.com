---
layout: post
title: "Latex Tips when doing Thesis"
date: 2013-08-23 12:02
comments: true
categories: latex	 
tags: [latex,thesis]
---

I just finish my thesis recently and it is time now to summary some the techniques that I feel quite handy. 

# Template 

The template can be downloaded from this [website]('http://www.phys.washington.edu/users/mforbes/projects/ubcthesis/'). In fact, all the need is the following files: 
```
genthesis.cls
sample.bib
ubcthesis.cls
ubcthesis.dtx
ubcthesis.ins
ubcthesis.tex
```

# Bibliography

I use the package called __natbib__ to control the style of Biblography. __natbib__ is a latex packages. Please refer to this [web page](http://merkel.zoneo.net/Latex/natbib.php).

## Step 1 make a bib file. 
For example, my bib file is called `mybib.bib`, in which all the citation information is stored. Each term looks like this, which you can download easily from __Google Scholar__.
```
@article{iwai1996boostrap,
  title={The boostrap theory of money: A search-theoretic foundation of monetary economics},
  author={Iwai, Katsuhito},
  journal={Structural Change and Economic Dynamics},
  volume={7},
  number={4},
  pages={451--477},
  year={1996},
  publisher={Elsevier}
}
``` 

## Step 2 annouce the package in your latex file. 

```
\usepackage[authoryear,round]{natbib}
```

The `autheryear,round` are certain option. In this case, the reference will be displayed like `AutherName(1988)`. More optionns are available. Please refer to this [web page](http://merkel.zoneo.net/Latex/natbib.php)


## Step 3 cite in the article

```
\citet[iwai1996boostrap]
```

## Step 4 creat reference section 

Put the folllowing code after last chapter and before the appendix
```
\bibliographystyle{plainnat}
\bibliography{mybib}
```

## Step 5 complile

complile the latex file in Latex twice. Then complile it with BibTex twice. Once again, complile it in Latex twice. 

Bingo! 


# ```\Input``` command in latex

Often, I recommmand to use input when you are writing a long article in latex so that you can put tex code in each chapter into seperate tex files. The main latex file for to generate the whole pdf is just a skeletion of your book or thesis. For me, it is always a pain in the ass to track a long tex files, say including 10,000 lines of code. 

you can even use \input in your ```input``` files. But \include cannot be used in that way. 

\input is super useful when you like to creat figures and tables. It allows reproducible work. See my older [post](http://yunlongnie.github.io/blog/2013/07/19/r-my-own-function-to-generate-text-code-for-figure/) about how you generate a tex code for figure. 





