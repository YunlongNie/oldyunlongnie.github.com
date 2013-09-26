---
layout: post
title: "SAS: unqiue value of a variable"
date: 2013-09-26 13:27
comments: true
categories: SAS
tags: [sas, retain, automatic variable, put]
---

Just started working recently and got used to software called SAS, which is quite difference from R. However, R is super-slow when dealing with large dataset. I didn't realize this until two days ago. I guess sas doesn't really store the data set in its memory and that is why it is not that easy to creat a simple sequence compared to R. Another example would be in SAS you cannot change data like `a[1,2] = 3`. 

# How to count unique levels of a discrete variable. 
1. by using first.value 
2. by using proc freq and nlevels
  

## 1
Below is an example. The dataset, cars, contain information about cars brand, which is named as `maker`. We wish to see how many different brands there are. 
```
proc sort data=sashelp.cars out=cars; *First sort the data by make;
by make;
run;
ods listing;
data _null_; *we only need to put the result into screen so we do not need to specify any dataset;
set cars end = lastobs; *end option mark the last observation;
by make;
if _N_ =1 then n=1; *_N_ = 1 mark the first observation;
else do;
retain n; * retain means n stay at its value when next loop starts;
if first.make then n = n+1;
end;
if lastobs then put n=;  * put output to screens when the loop ends;
run;
```
## Key points
### retain 
### end=
### put n=

A relative easiier way is to change the second part of the code by
```
data _null_;
set cars end=last; * end = last if last=1 the loop is on the last obs;* if like to detect the first obs use _N_=1;
by make;
retain n 0; * here retain n and the initial value is set to be 0;
if first.make then n = n+1;
if last then put n= _N_=;
if _N_ = 1 then put n=;   
run;
```
## 2

`proc freq` step will generate a value counting the number of different levels in the target variable. We only need to put that value on the screen. Here the `ods select nlevels` tells sas to trace the value of `nlevels`. If one has no idea what results sas will generate during the process, ods tracing can help you. 

```
ods select nlevels;

proc freq data=cars nlevels;
table make/noprint;
run;
```
