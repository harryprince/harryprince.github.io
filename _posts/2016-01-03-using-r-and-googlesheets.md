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

In that, inspired by gspread, a python package, I am trying googlesheets package, a counterpart of another R package.

Thanks for [Jennifer](https://speakerdeck.com/jennybc/googlesheets-talk-at-user2015)

Firstly, download the git repository and install.

```{cli}
library(devtools)
devtools::install_github("jennybc/googlesheets")
```

If you're network blocked, you could download manually.

```{cli}
git clone git@github.com:jennybc/googlesheets.git
R CMD INSTALL googlesheets
```

```{r}
library(googlesheets)
gs_ls()                           # authenticated in a popup website
ss <- gs_title("My_December_Table") # read a SpreadSheet from your accout
gs_read(bb,ws=3,range="A1:D20")    # read a sheet, ws means WorkSheet number

bb <- gs_edit_cells(ss, input = head(iris), trim = TRUE) # edit the table
gs_read(ss)
```

the more method you can see the official manual!

Reference: (Jennifer in UsingR Conference 2015)[https://speakerdeck.com/jennybc/googlesheets-talk-at-user2015]
