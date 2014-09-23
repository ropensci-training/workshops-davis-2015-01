## Macroecology - testing the species-abundance distribution


```r
library('rbison')
```

```
## 
## 
## New to rbison? Tutorial at http://ropensci.org/tutorials/rbison_tutorial.html 
## citation(package='rbison') for the citation for rbison
## Use suppressPackageStartupMessages() to suppress these startup messages in the future
```

```r
library('ggplot2')
library('plyr')
```

Define species names vector


```r
mynames <- c("Helianthus annuus", "Pinus contorta", "Poa annua", 
  "Madia sativa", "Arctostaphylos glauca", "Heteromeles arbutifolia",
  "Symphoricarpos albus", "Ribes viburnifolium", "Diplacus aurantiacus", 
  "Salvia leucophylla", "Encelia californica", "Ribes indecorum", 
  "Ribes malvaceum", "Cercocarpus betuloides", "Penstemon spectabilis")
```

Define function to get data


```r
getdata <- function(x) {
  out <- bison(species = x, county = "Los Angeles", count = 0, what = "summary")
  out$summary$specimen
}
```

Get data for each name, combine to `data.frame`


```r
out <- sapply(mynames, getdata)
names(out) <- mynames
df <- ldply(out)
```

Fit various models of species abundance distributions


```r
library('vegan')
```

```
## Loading required package: permute
## 
## Attaching package: 'permute'
## 
## The following object is masked from 'package:devtools':
## 
##     check
## 
## Loading required package: lattice
## This is vegan 2.0-10
```

```r
plot(radfit(df$V1))
```

![plot of chunk unnamed-chunk-5](figure/unnamed-chunk-5.png) 
