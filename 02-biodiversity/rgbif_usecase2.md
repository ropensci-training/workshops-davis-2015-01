## rgbif use case No. 3 - Finding countries species are found in using rgbif

### Load some libraries


```r
library(rgbif)
```

```r
library(plyr)
library(doMC)
```


### List of bird species


```r
spplist <- c("Geothlypis trichas", "Tiaris olivacea", "Pterodroma axillaris", 
    "Calidris ferruginea", "Pterodroma macroptera", "Gallirallus australis", 
    "Falco cenchroides", "Telespiza cantans", "Oreomystis bairdi", "Cistothorus palustris")
```


### Get GBIF keys for each taxon


```r
keys <- sapply(spplist, function(x) name_backbone(x, rank = "species")$usageKey)
```

```
## Loading required package: rjson
```

```r
# remove NULLs
keys <- compact(keys)
```


### Get country names (from rgbif package)

For brevity we'll just use 25 countries


```r
countrynames <- as.character(isocodes$gbif_name)[1:25]
```


### Get data

Function to get data for each name


```r
occ_by_countries <- function(spkey) {
    occ_count_safe <- plyr::failwith(NULL, occ_count)
    tmp <- lapply(countrynames, function(x) occ_count_safe(spkey, country = x))
    names(tmp) <- countrynames
    tmp[grep("No enum", tmp)] <- NA
    tmp
}
```


Get data for each species


```r
registerDoMC(cores = 4)
out <- llply(keys, occ_by_countries, .parallel = TRUE)
```


Or you could do the same without doing in parallel, but will be slower of course


```r
out <- lapply(keys, occ_by_countries)
```


### Assign species name to each output element

Then make a data.frame, then remove NA rows


```r
names(out) <- spplist
df <- ldply(out, function(x) {
    tmp <- ldply(x)
    names(tmp)[1] <- "country"
    tmp
})
df <- na.omit(df)  # remove NAs (which were caused by errors in country names)
```


And you can get only countries they're found in by removing zeros


```r
# Get only countries found in
df_foundin <- df[!df$V1 == 0, ]
```


Look at first and last six rows


```r
head(df_foundin)
```

```
##                  .id        country     V1
## 1 Geothlypis trichas  UNITED_STATES 605628
## 2 Geothlypis trichas         CANADA  52983
## 3 Geothlypis trichas         MEXICO   7702
## 4 Geothlypis trichas     COSTA_RICA    115
## 8 Geothlypis trichas         PANAMA     40
## 9 Geothlypis trichas UNITED_KINGDOM      6
```

```r
tail(df_foundin)
```

```
##                       .id          country     V1
## 175     Falco cenchroides PAPUA_NEW_GUINEA      9
## 176     Telespiza cantans    UNITED_STATES    352
## 201     Oreomystis bairdi    UNITED_STATES     83
## 226 Cistothorus palustris    UNITED_STATES 182071
## 227 Cistothorus palustris           CANADA  19120
## 228 Cistothorus palustris           MEXICO   1396
```

