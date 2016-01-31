---
layout: post
title:  "Reading Notebook with Advanced R by Hadley Wickham"
categories: [jekyll, blog]
tags: [knitr, servr, httpuv, websocket]
---
# the difference between closure and builtin

example:


{% highlight r %}
f <- function(){}
typeof(f)
{% endhighlight %}



{% highlight text %}
## [1] "closure"
{% endhighlight %}



{% highlight r %}
# > "closure"
typeof(sum)
{% endhighlight %}



{% highlight text %}
## [1] "builtin"
{% endhighlight %}



{% highlight r %}
# > "builtin"
{% endhighlight %}

mode() is just a shadow of typeof()

To see if an object is a pure base type, i.e., it doesn’t also have S3, S4, or RC behaviour, check that is.object(x) returns FALSE.

# Check Static Class by otype() and ftype()
In S3, methods belong to functions, called generic functions, or generics for short. S3 methods do not belong to objects or classes. This is different from most other programming languages, but is a legitimate OO style.


{% highlight r %}
x = seq(10)
y = rep(1,10)
t = data.frame(x,y)
otype(x)
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): could not find function "otype"
{% endhighlight %}



{% highlight r %}
# > "base"
otype(t)
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): could not find function "otype"
{% endhighlight %}



{% highlight r %}
# > "S3"

ftype(sum)
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): could not find function "ftype"
{% endhighlight %}



{% highlight r %}
# > [1] "primitive" "generic"

ftype(mean)
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): could not find function "ftype"
{% endhighlight %}



{% highlight r %}
# > [1] "s3"      "generic"

methods("mean")
{% endhighlight %}



{% highlight text %}
## [1] mean.Date     mean.default  mean.difftime mean.POSIXct 
## [5] mean.POSIXlt 
## see '?methods' for accessing help and source code
{% endhighlight %}



{% highlight r %}
# > [1] mean.Date     mean.default  mean.difftime mean.POSIXct  mean.POSIXlt
{% endhighlight %}


{% highlight r %}
foo <- structure(list(), class = "foo")
{% endhighlight %}


{% highlight r %}
# 1. Pipe to first-argument of function
rnorm(100) %>>%
  plot
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): could not find function "%>>%"
{% endhighlight %}



{% highlight r %}
# 
# 2. Pipe to . in an expression
# 
rnorm(100) %>>%
  plot(col="red", main=length(.))
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): could not find function "%>>%"
{% endhighlight %}



{% highlight r %}
# pass left side result into right side point.
{% endhighlight %}

a[1, , drop = FALSE]
