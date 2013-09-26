---
layout: post
title: "R: let R run bash code in backgroud"
date: 2013-07-21 00:35
comments: true
categories: r 
tags: [r, bash]
---

Recently, I am making a R package. During this process, I found lots of useful stuff which worth a record. I will talk about how to make R packges with Rcpp, in which R code and C code are combined. 

Below is my R code for making a pacakge:
```

require(Rcpp)

cfiles = paste("Cpp/",list.files("Cpp/"),sep="")
Rfiles = paste("R/",list.files("R/"),sep="")
packageName="BayDR"
verNo=2.2
system(paste("rm -rf",packageName))
#  delete the original bayDR folder 
Rcpp.package.skeleton(name=packageName,cpp_files=cfiles,code_files=Rfiles,author="YL",
                      example_code=FALSE,email="yunlong.nie@stat.ubc.ca")


require(roxygen2)

roxygenise(package.dir="BayDR",overwrite=TRUE) # wirte some in the C++ files too, like in the DatDen_X_C

# add useDynLib(BayDR) at the end of NAMESPACE

system(paste("cp -r data ",paste0(packageName,"/")))
sink(file=paste0(packageName,"/NAMESPACE"),append=TRUE)
cat("useDynLib(",packageName,")",sep="")
sink()
file.copy(from="DESCRIPTION",to=paste0(packageName,"/"),overwrite=TRUE)
desp= readLines(con=paste0(packageName,"/","DESCRIPTION"))
desp[4] = paste("Version: ", verNo)
writeLines(desp,con=paste0(packageName,"/","DESCRIPTION"))
# then copy the description file and data folder, change the verion number in the description file. 

# command line to the the folder which bayDR locates

system(paste("R CMD build",packageName))
filenames = list.files("~/Dropbox/UBC/CinR/FileOnSever/Mypackages/Import/")
system(paste("R CMD check",filenames[grep(as.character(verNo),filenames)]))

```

Sorry for throwing this ugly code first here. But if you look carefully, probably you did notice that there is a `system()` function there. For example, 

        system(paste("cp -r data ",paste0(packageName,"/")))

which I call bash to copy the data file into another directory. It's actually super simple but spares you open your terminal or click your mouse. The problem is sometimes after a long time when you cannot exactly recall every step, but you need to reproduce your work. Running everything on a script avoid that issue. It is especially helpful for file management. 

 


