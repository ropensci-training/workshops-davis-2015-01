## A more intuitive workflow


```r
knitr::opts_chunk$set(
  comment = "# ",
  error = FALSE,
  cache = TRUE,
  message = FALSE,
  warning = FALSE
)
```

So there's a different way to work in R. It's all about pipes. Load `magrittr` and `dplyr`


```r
library('magrittr')
```

> %>% - pronounced "then" Pipe an object forward into a function call/expression.


```r
iris %>%
  head
```

```
#    Sepal.Length Sepal.Width Petal.Length Petal.Width Species
#  1          5.1         3.5          1.4         0.2  setosa
#  2          4.9         3.0          1.4         0.2  setosa
#  3          4.7         3.2          1.3         0.2  setosa
#  4          4.6         3.1          1.5         0.2  setosa
#  5          5.0         3.6          1.4         0.2  setosa
#  6          5.4         3.9          1.7         0.4  setosa
```

```r
iris %>%
  str
```

```
#  'data.frame':	150 obs. of  5 variables:
#   $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
#   $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
#   $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
#   $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
#   $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...
```

But more complicated as well


```r
library('dplyr')
library('magrittr')
```


```r
diamonds %>%
  group_by(color) %>%
  summarise(total = sum(price)) %>%
  arrange(desc(total)) %>%
  head(5)
```

```
#  Source: local data frame [5 x 2]
#  
#    color    total
#  1     G 45158240
#  2     H 37257301
#  3     F 35542866
#  4     E 30142944
#  5     I 27608146
```

Pretty intuitive, right?

------

We can use this with your workflow of getting data, manipulating, analysis, etc.

Here, we'll use the `rnoaa` package to search for stations around Athens, GA with `noaa_stations()`, pass those to `ncdc()`, then `filter()` and `arrange()` rows, then plot, and save the plot.


```r
library(rnoaa)
```


```r
ids <- ncdc_stations(...)
ncdc('GHCND', stationid = ids, startdate = '2010-05-01', enddate = '2010-05-31') %>%
  filter(...) %>%
  arrange(...) %>%
  ggplot(aes(x, y)) + geom_line %>%
  ggsave("myplot.png")
```
