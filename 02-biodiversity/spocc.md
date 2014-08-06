### spocc - Make some maps!

### Load libraries


```r
library(spocc)
library(rCharts)
```


### spocc unifies access to biodiversity data across sources


```r
out <- occ(query = "Accipiter striatus", from = "gbif")
out$gbif  # GBIF data w/ metadata
```

```
## $meta
## $meta$source
## [1] "gbif"
## 
## $meta$time
## [1] "2013-12-11 22:23:22 EST"
## 
## $meta$query
## [1] "Accipiter striatus"
## 
## $meta$type
## [1] "sci"
## 
## $meta$opts
## list()
## 
## 
## $data
## $data$Accipiter_striatus
##                                 name       key longitude latitude prov
## 1  Accipiter striatus Vieillot, 1808 773414146   -122.27   37.771 gbif
## 2  Accipiter striatus Vieillot, 1808 773408845    -97.28   32.876 gbif
## 3  Accipiter striatus Vieillot, 1808 768992325    -76.10    4.724 gbif
## 4  Accipiter striatus Vieillot, 1808 773423188    -76.54   38.688 gbif
## 5  Accipiter striatus Vieillot, 1808 773430206   -117.06   32.552 gbif
## 6  Accipiter striatus Vieillot, 1808 773440541    -98.00   32.800 gbif
## 7  Accipiter striatus Vieillot, 1808 773432602   -122.78   38.613 gbif
## 8  Accipiter striatus Vieillot, 1808 833024105   -105.16   40.678 gbif
## 9  Accipiter striatus Vieillot, 1808        NA        NA       NA gbif
## 10 Accipiter striatus Vieillot, 1808 579121888    -71.54   43.545 gbif
## 11 Accipiter striatus Vieillot, 1808 579122449    -76.54   39.193 gbif
## 12 Accipiter striatus Vieillot, 1808 579126904    -97.33   30.107 gbif
## 13 Accipiter striatus Vieillot, 1808 579129121    -73.26   41.128 gbif
## 14 Accipiter striatus Vieillot, 1808 579130369   -111.75   43.871 gbif
## 15 Accipiter striatus Vieillot, 1808 579130765    -74.96   38.939 gbif
## 16 Accipiter striatus Vieillot, 1808 579131656   -108.13   39.164 gbif
## 17 Accipiter striatus Vieillot, 1808 579131887   -121.97   36.972 gbif
## 18 Accipiter striatus Vieillot, 1808 579134989   -106.88   33.802 gbif
## 19 Accipiter striatus Vieillot, 1808 579135814    -85.39   44.422 gbif
## 20 Accipiter striatus Vieillot, 1808 579137173   -123.24   44.716 gbif
```

```r
out$ebird$data  # empty
```

```
## $Accipiter_striatus
## data frame with 0 columns and 0 rows
```

```r
out$gbif$meta  #  metadata, your query parameters, time the call executed, etc. 
```

```
## $source
## [1] "gbif"
## 
## $time
## [1] "2013-12-11 22:23:22 EST"
## 
## $query
## [1] "Accipiter striatus"
## 
## $type
## [1] "sci"
## 
## $opts
## list()
```

```r
out$gbif$data  # just data
```

```
## $Accipiter_striatus
##                                 name       key longitude latitude prov
## 1  Accipiter striatus Vieillot, 1808 773414146   -122.27   37.771 gbif
## 2  Accipiter striatus Vieillot, 1808 773408845    -97.28   32.876 gbif
## 3  Accipiter striatus Vieillot, 1808 768992325    -76.10    4.724 gbif
## 4  Accipiter striatus Vieillot, 1808 773423188    -76.54   38.688 gbif
## 5  Accipiter striatus Vieillot, 1808 773430206   -117.06   32.552 gbif
## 6  Accipiter striatus Vieillot, 1808 773440541    -98.00   32.800 gbif
## 7  Accipiter striatus Vieillot, 1808 773432602   -122.78   38.613 gbif
## 8  Accipiter striatus Vieillot, 1808 833024105   -105.16   40.678 gbif
## 9  Accipiter striatus Vieillot, 1808        NA        NA       NA gbif
## 10 Accipiter striatus Vieillot, 1808 579121888    -71.54   43.545 gbif
## 11 Accipiter striatus Vieillot, 1808 579122449    -76.54   39.193 gbif
## 12 Accipiter striatus Vieillot, 1808 579126904    -97.33   30.107 gbif
## 13 Accipiter striatus Vieillot, 1808 579129121    -73.26   41.128 gbif
## 14 Accipiter striatus Vieillot, 1808 579130369   -111.75   43.871 gbif
## 15 Accipiter striatus Vieillot, 1808 579130765    -74.96   38.939 gbif
## 16 Accipiter striatus Vieillot, 1808 579131656   -108.13   39.164 gbif
## 17 Accipiter striatus Vieillot, 1808 579131887   -121.97   36.972 gbif
## 18 Accipiter striatus Vieillot, 1808 579134989   -106.88   33.802 gbif
## 19 Accipiter striatus Vieillot, 1808 579135814    -85.39   44.422 gbif
## 20 Accipiter striatus Vieillot, 1808 579137173   -123.24   44.716 gbif
```


And you can squash together data from sources easily


```r
out <- occ(query = "Accipiter striatus", from = c("gbif", "bison"))
head(occ2df(out))
```

```
##                                name longitude latitude prov
## 1 Accipiter striatus Vieillot, 1808   -122.27   37.771 gbif
## 2 Accipiter striatus Vieillot, 1808    -97.28   32.876 gbif
## 3 Accipiter striatus Vieillot, 1808    -76.10    4.724 gbif
## 4 Accipiter striatus Vieillot, 1808    -76.54   38.688 gbif
## 5 Accipiter striatus Vieillot, 1808   -117.06   32.552 gbif
## 6 Accipiter striatus Vieillot, 1808    -98.00   32.800 gbif
```



### Make a map using Shiny locally (uses rCharts)

Try changing the species names to whatever you like and press **Submit**

Or change the background map, or the color palette. 

**This may not work using RStudio server**


```r
mapshiny()
```



### Make a map using rCharts


```r
spp <- c("Danaus plexippus", "Accipiter striatus", "Pinus contorta")
dat <- occ(query = spp, from = "gbif", gbifopts = list(georeferenced = TRUE))
dat <- occ2df(dat)
maprcharts(data = dat)
```



### Make a map using GitHub gists

If you have a Github Account, you can get an interactive map on Github in one line of code. The map will open in your default browser. 


```r
mapgist(data = dat, color = c("#976AAE", "#6B944D", "#BD5945"))
```

