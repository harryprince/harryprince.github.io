---
layout: post
title: "Making an Import Wheel in R"
comments: true
author: "Harry Zhu"
date: "January 5, 2016"
output: html_document
---

When we switch from a *nix development environment to a Windows one, or reverse the process, we have to be confront with the dependancies problem.

In that, despite of the previous wheel packrat existing, which is built by Rstudio, a robust tool for virtualizing the environment, I am glad to make another wheel, an import function, which inspired from Python.

This import function will load the dependancies, and install these uninstalled one. These will improve the environment problem.


{% highlight r %}
import <- function(packages){
  for (i in 1:length(packages)){
    package = packages[i];
    char_package = package;
    # char_package <- as.character(substitute(char_package))
    loaded <- paste("package", char_package, sep = ":") %in% search() #

    # is it existing the package
    if(loaded){
      library(char_package,character.only = TRUE)
      cat(paste0("load  ",char_package," package"),"\n")
    }
    else{
      cat(paste0("can not find ",char_package,", we need to install it"),"\n");
      install.packages(package);
      library(char_package,character.only = TRUE)
    }
  }
}
# import dependencies

dependencies = c("RMySQL","ggplot2","httr")
import(dependencies)
{% endhighlight %}



{% highlight text %}
## can not find RMySQL, we need to install it
{% endhighlight %}



{% highlight text %}
## Warning: unable to access index for repository https://
## mran.revolutionanalytics.com/snapshot/2015-08-27/src/contrib
{% endhighlight %}



{% highlight text %}
## Warning: package 'RMySQL' is not available (for R version 3.2.2)
{% endhighlight %}



{% highlight text %}
## Loading required package: DBI
## Loading required package: methods
{% endhighlight %}



{% highlight text %}
## can not find ggplot2, we need to install it 
## 
## The downloaded binary packages are in
## 	/var/folders/f2/9jwh0h8s4y70r1jl3s7cq_5c0000gn/T//Rtmpqbv9uE/downloaded_packages
## can not find httr, we need to install it 
## 
## The downloaded binary packages are in
## 	/var/folders/f2/9jwh0h8s4y70r1jl3s7cq_5c0000gn/T//Rtmpqbv9uE/downloaded_packages
{% endhighlight %}
