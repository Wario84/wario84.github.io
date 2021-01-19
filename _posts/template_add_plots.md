---
layout: post
title: "Easy peasy plotting with ggplot2"
date: 2017--04--24
---

## Introduction

`ggplot2` is an excellent alternative if you want to produce fast, colourful and elegant graphics. Very often we want to use graphics not only as an exploratory tool, but as part of a presentation, dissertation, paper, or even a blog like this. In order to achieve that, we would like to use tools that pay attention to the quality minimizing the coding and learning curve required to used them. `ggplot2` is an excellent example of such a tool.

## Requirements

For this script, we will be using the package `ggplot2` and the data.frame `mtcars` which is included in `R`. 



```r
summary(mtcars[,c(1,2)])
```

```
##       mpg             cyl       
##  Min.   :10.40   Min.   :4.000  
##  1st Qu.:15.43   1st Qu.:4.000  
##  Median :19.20   Median :6.000  
##  Mean   :20.09   Mean   :6.188  
##  3rd Qu.:22.80   3rd Qu.:8.000  
##  Max.   :33.90   Max.   :8.000
```

## Plotting with the base

If we would like plot the change of miles per gallon,`mpg`, in the vertical axis versus a number of cylinders, `cyl`. Using the [r-base](https://stat.ethz.ch/R-manual/R-devel/library/base/html/00Index.html), we can use the `plot` command.


```r
plot(x=mtcars$cyl, y=mtcars$mpg)
```

![](https://github.com/Wario84/wario84.github.io/blob/master/assets/img/plot-1.png)<!-- -->

This plot is already informative, we can easily see that as the number of `cylinders` in the engine increases in the horizontal axis, the efficiency measured by `miles per gallon` reduces. However, visually it might not be so appealing. 

## Plotting with `ggplot2`

Let's start by installing and loading the package into the environment.


```r
install.packages("ggplo2")
library(ggplot2)
```

Next, lets plot again `mpg` versus `cyl`.

```r
ggplot(mtcars, aes(x=cyl,y=mpg))+geom_point()
```

![](~/assets/img/ggplot1-1.png)<!-- -->

Notice, that `ggplot` is taking the data.frame `mtcars` as a first argument, then `cyl` is specified in the horizontal axis by the argument `x` and similarly for `mpg` in the vertical axis (`y`). Finally we can think of `geom_point()` as templates for different kinds of graphs. Here we will explore the most common ones.

Now lets add a color to differentiate the cars by `gear`.

```r
summary(mtcars$gear)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   3.000   3.000   4.000   3.688   4.000   5.000
```
And plot again.

```r
ggplot(mtcars, aes(x=cyl,y=mpg, color=gear))+geom_point()
```

![](assets/img/ggplot2-1.png)<!-- -->




