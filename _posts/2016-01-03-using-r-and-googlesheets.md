---
layout: post
title: "Using R and Google Sheets"
comments: false
author: "Harry Zhu"
date: "January 3, 2016"
output: html_document
---
# Using R and Google Sheets

Today, I meet a big problem about my ERP system built in Google Sheets, and I don't want to shape a too complicated one such as WordPress or Django.

In that, inspired by [gspread](https://github.com/burnash/gspread), a python package, I am trying [googlesheets package](https://github.com/jennybc/googlesheets), a counterpart of another R package.

Firstly, download the git repository and install.


{% highlight r %}
library(devtools)
devtools::install_github("hadley/readr")
{% endhighlight %}



{% highlight text %}
## Downloading GitHub repo hadley/readr@master
{% endhighlight %}



{% highlight text %}
## Error in curl::curl_fetch_memory(url, handle = handle): Timeout was reached
{% endhighlight %}



{% highlight r %}
devtools::install_github("jennybc/googlesheets")
{% endhighlight %}



{% highlight text %}
## Downloading GitHub repo jennybc/googlesheets@master
## Installing googlesheets
## Skipping 5 packages ahead of CRAN: dplyr, jsonlite, mime, Rcpp, tidyr
## '/Library/Frameworks/R.framework/Resources/bin/R' --no-site-file  \
##   --no-environ --no-save --no-restore CMD INSTALL  \
##   '/private/var/folders/f2/9jwh0h8s4y70r1jl3s7cq_5c0000gn/T/RtmpN3HfZO/devtoolsc3c37718540a/jennybc-googlesheets-067e4a3'  \
##   --library='/Library/Frameworks/R.framework/Versions/3.2/Resources/library'  \
##   --install-tests
{% endhighlight %}

If you're network blocked, you could download manually.

```
$git clone $git@github.com:jennybc/googlesheets.git
$R CMD INSTALL googlesheets
```
Now, we could manipulate googlesheets with R.

{% highlight r %}
library(googlesheets)
gs_ls()                           # authenticated in a popup website
{% endhighlight %}



{% highlight text %}
## Error: oauth_listener() needs an interactive environment.
{% endhighlight %}



{% highlight r %}
ss <- gs_title("My_December_Table") # read a SpreadSheet from your accout
{% endhighlight %}



{% highlight text %}
## Error: oauth_listener() needs an interactive environment.
{% endhighlight %}



{% highlight r %}
gs_read(bb,ws=3,range="A1:D20")    # read a sheet, ws means WorkSheet number
{% endhighlight %}



{% highlight text %}
## Error in inherits(ss, "googlesheet"): object 'bb' not found
{% endhighlight %}



{% highlight r %}
bb <- gs_edit_cells(ss, input = head(iris), trim = TRUE) # edit the table
{% endhighlight %}



{% highlight text %}
## Error in inherits(ss, "googlesheet"): object 'ss' not found
{% endhighlight %}



{% highlight r %}
gs_read(ss)
{% endhighlight %}



{% highlight text %}
## Error in inherits(ss, "googlesheet"): object 'ss' not found
{% endhighlight %}

the more method you can see the official manual and [shiny exampl](https://jennybc.shinyapps.io/10_read-write-private-sheet)!

Reference:[Jennifer in UsingR Conference 2015](https://speakerdeck.com/jennybc/googlesheets-talk-at-user2015)

[Related Shiny Examples](https://github.com/jennybc/googlesheets/tree/master/inst/shiny-examples)
<script async class="speakerdeck-embed" data-id="f54a8a6044934d4187118a0ecb1cca16" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>
