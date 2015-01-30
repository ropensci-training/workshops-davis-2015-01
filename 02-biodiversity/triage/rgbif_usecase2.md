## rgbif use case - Finding countries species are found in using rgbif

### Load some libraries


```r
library(rgbif)
library(plyr)
library(doMC)
```

### List of bird species


```r
spplist <- c('Geothlypis trichas','Tiaris olivacea','Pterodroma axillaris','Calidris ferruginea','Pterodroma macroptera','Gallirallus australis','Falco cenchroides','Telespiza cantans','Oreomystis bairdi','Cistothorus palustris')
```

### Get GBIF keys for each taxon


```r
keys <- sapply(spplist, function(x) name_backbone(x, rank="species")$usageKey)
```

### Get data for each species


```r
out <- count_facet(keys = keys, countries = 50)
out <- out[ out$V1 != 0 , ] # remove zeros
```

Match names to codes


```r
namescodes <- ldply(keys)
names(namescodes) <- c('name','code')
alldata <- merge(namescodes, out, by.x="code", by.y=".id")
head(alldata)
```

```
##      code                  name country     V1
## 1 2474535 Gallirallus australis      AU    128
## 2 2481009     Falco cenchroides      AU 102254
## 3 2481481 Pterodroma macroptera      AQ    662
## 4 2481481 Pterodroma macroptera      AR      4
## 5 2481481 Pterodroma macroptera      AU   1820
## 6 2481741   Calidris ferruginea      AE   1158
```


