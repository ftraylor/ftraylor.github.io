---
title: "RMarkdown-demo"
output: 
  html_document: 
    fig_caption: yes
    keep_md: yes
    number_sections: yes
    toc: yes
  html_notebook: 
    fig_caption: yes
    number_sections: yes
    toc: yes
---

In this illustration, the Gapminder package is used for plotting charts.  This data set comes with six variables including country, continent, year, life expectancy, population and GDP per capita. 

Let's install the package, load the data and examine the dataset:

```r
require(gapminder)
```

```
## Warning: package 'gapminder' was built under R version 3.5.3
```

```r
summary(gapminder) # Summary of Gapminder dataset
str(gapminder) # Structure of dataset

gm=gapminder
head(gm)
summary(gm)
```

```r
table(gm$country) # List values of country variable 
```


Simple Scatterplot:


```r
require(ggplot2)
```

```
## Loading required package: ggplot2
```

```
## Warning: package 'ggplot2' was built under R version 3.5.3
```

```r
p <- ggplot(data = gm,
            mapping = aes(x = gdpPercap,
                          y = lifeExp))  # Shows nothing. Why?
p + geom_point()
```

![](RMarkdown-Demo_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

First, we need to start the data component, then add the aesthetic mapping defining the basics (i.e. variables), followed by the geometric objects.  Here is an alternative: 


```r
# Alternative
p <- ggplot(data=gm, aes(x=gdpPercap, y=lifeExp))
```

What is still missing?


```r
p + geom_point()
```

![](RMarkdown-Demo_files/figure-html/unnamed-chunk-5-1.png)<!-- -->

Now, we can add more features to the chart.


```r
# Add some color grouping
p <- ggplot(data = gm,
            mapping = aes(x = gdpPercap,
                          y = lifeExp, color=continent))
p + geom_point()
```

![](RMarkdown-Demo_files/figure-html/unnamed-chunk-6-1.png)<!-- -->
Now you can knit the Markdown file and publish it to either Rpub or your own github website!
