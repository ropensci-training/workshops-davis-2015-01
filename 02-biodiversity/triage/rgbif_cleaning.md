## rgbif data quality/data cleaning

> In development version only

### Load some libraries


```r
library('rgbif')
```

### Parsing output by issue


```r
(res <- occ_search(geometry='POLYGON((30.1 10.1, 10 20, 20 40, 40 40, 30.1 10.1))', limit = 50))
```

```
## Records found [961726] 
## Records returned [50] 
## No. unique hierarchies [47] 
## No. media records [41] 
## Args [geometry=POLYGON((30.1 10.1, 10 20, 20 40, 40 40, 30.1 10.1)),
##      limit=50, fields=minimal] 
## First 10 rows of data
## 
##                    name       key decimalLatitude decimalLongitude
## 1     Mullus surmuletus 883516592           39.95            23.69
## 2           Coris julis 883499301           39.95            23.69
## 3      Egretta garzetta 891031709           33.10            35.61
## 4         Corvus cornix 891037853           31.13            33.80
## 5  Acridotheres tristis 891053255           32.50            34.90
## 6    Diplodus annularis 883500975           39.95            23.69
## 7         Ardea cinerea 891052609           33.10            35.61
## 8            Psittacula 891040906           30.02            31.22
## 9  Phoenicurus ochruros 891037944           31.13            33.80
## 10    Motacilla cinerea 891045146           33.25            35.65
## ..                  ...       ...             ...              ...
## Variables not shown: issues (chr)
```

Can print whole table, or search for matches


```r
head(gbifissues)
```

```
##    code                              issue
## 1   bri            BASIS_OF_RECORD_INVALID
## 2   ccm         CONTINENT_COUNTRY_MISMATCH
## 3   cdc CONTINENT_DERIVED_FROM_COORDINATES
## 4 conti                  CONTINENT_INVALID
## 5  cdiv                 COORDINATE_INVALID
## 6 cdout            COORDINATE_OUT_OF_RANGE
##                                                                                                    description
## 1 The given basis of record is impossible to interpret or seriously different from the recommended vocabulary.
## 2                                                       The interpreted continent and country do not match up.
## 3                  The interpreted continent is based on the coordinates, not the verbatim string information.
## 4                                                                      Uninterpretable continent values found.
## 5                                      Coordinate value given in some form but GBIF is unable to interpret it.
## 6                                        Coordinate has invalid lat/lon values out of their decimal max range.
```

```r
gbifissues[ gbifissues$code %in% c('cdround','cudc','gass84','txmathi'), ]
```

```
##       code                            issue
## 10 cdround               COORDINATE_ROUNDED
## 12    cudc COUNTRY_DERIVED_FROM_COORDINATES
## 23  gass84     GEODETIC_DATUM_ASSUMED_WGS84
## 39 txmathi           TAXON_MATCH_HIGHERRANK
##                                                                                                                                 description
## 10                                                                                  Original coordinate modified by rounding to 5 decimals.
## 12                                                The interpreted country is based on the coordinates, not the verbatim string information.
## 23 Indicating that the interpreted coordinates assume they are based on WGS84 datum as the datum was either not indicated or interpretable.
## 39                                        Matching to the taxonomic backbone can only be done on a higher rank and not the scientific name.
```

Or parse issues in various ways, e,g. remove data rows with certain issue classes


```r
library('magrittr')
res %>% occ_issues(-gass84, -mdatunl)
```

```
## Records found [961726] 
## Records returned [9] 
## No. unique hierarchies [47] 
## No. media records [41] 
## Args [geometry=POLYGON((30.1 10.1, 10 20, 20 40, 40 40, 30.1 10.1)),
##      limit=50, fields=minimal] 
## First 10 rows of data
## 
##                  name       key decimalLatitude decimalLongitude
## 1   Mullus surmuletus 883516592           39.95            23.69
## 2         Coris julis 883499301           39.95            23.69
## 6  Diplodus annularis 883500975           39.95            23.69
## 21      Labrus merula 883514095           39.95            23.69
## 27    Apogon imberbis 883492366           39.95            23.69
## 35    Chromis chromis 883498119           39.95            23.69
## 36        Sarpa salpa 884056896           39.95            23.69
## 43    Diplodus sargus 883500984           39.95            23.69
## 44    Serranus scriba 884134809           39.95            23.69
## Variables not shown: issues (chr)
```

split issues into separate columns


```r
res %>% occ_issues(mutate = "split")
```

```
## Records found [961726] 
## Records returned [50] 
## No. unique hierarchies [47] 
## No. media records [41] 
## Args [geometry=POLYGON((30.1 10.1, 10 20, 20 40, 40 40, 30.1 10.1)),
##      limit=50, fields=minimal] 
## First 10 rows of data
## 
##                    name       key decimalLatitude decimalLongitude cdround
## 1     Mullus surmuletus 883516592           39.95            23.69       y
## 2           Coris julis 883499301           39.95            23.69       y
## 3      Egretta garzetta 891031709           33.10            35.61       y
## 4         Corvus cornix 891037853           31.13            33.80       y
## 5  Acridotheres tristis 891053255           32.50            34.90       y
## 6    Diplodus annularis 883500975           39.95            23.69       y
## 7         Ardea cinerea 891052609           33.10            35.61       y
## 8            Psittacula 891040906           30.02            31.22       y
## 9  Phoenicurus ochruros 891037944           31.13            33.80       y
## 10    Motacilla cinerea 891045146           33.25            35.65       y
## ..                  ...       ...             ...              ...     ...
## Variables not shown: cudc (chr), gass84 (chr), mdatunl (chr)
```

expand issues to more descriptive names


```r
res %>% occ_issues(mutate = "expand")
```

```
## Records found [961726] 
## Records returned [50] 
## No. unique hierarchies [47] 
## No. media records [41] 
## Args [geometry=POLYGON((30.1 10.1, 10 20, 20 40, 40 40, 30.1 10.1)),
##      limit=50, fields=minimal] 
## First 10 rows of data
## 
##                    name       key decimalLatitude decimalLongitude
## 1     Mullus surmuletus 883516592           39.95            23.69
## 2           Coris julis 883499301           39.95            23.69
## 3      Egretta garzetta 891031709           33.10            35.61
## 4         Corvus cornix 891037853           31.13            33.80
## 5  Acridotheres tristis 891053255           32.50            34.90
## 6    Diplodus annularis 883500975           39.95            23.69
## 7         Ardea cinerea 891052609           33.10            35.61
## 8            Psittacula 891040906           30.02            31.22
## 9  Phoenicurus ochruros 891037944           31.13            33.80
## 10    Motacilla cinerea 891045146           33.25            35.65
## ..                  ...       ...             ...              ...
## Variables not shown: issues (chr)
```

split and expand


```r
res %>% occ_issues(mutate = "split_expand")
```

```
## Records found [961726] 
## Records returned [50] 
## No. unique hierarchies [47] 
## No. media records [41] 
## Args [geometry=POLYGON((30.1 10.1, 10 20, 20 40, 40 40, 30.1 10.1)),
##      limit=50, fields=minimal] 
## First 10 rows of data
## 
##                    name       key decimalLatitude decimalLongitude
## 1     Mullus surmuletus 883516592           39.95            23.69
## 2           Coris julis 883499301           39.95            23.69
## 3      Egretta garzetta 891031709           33.10            35.61
## 4         Corvus cornix 891037853           31.13            33.80
## 5  Acridotheres tristis 891053255           32.50            34.90
## 6    Diplodus annularis 883500975           39.95            23.69
## 7         Ardea cinerea 891052609           33.10            35.61
## 8            Psittacula 891040906           30.02            31.22
## 9  Phoenicurus ochruros 891037944           31.13            33.80
## 10    Motacilla cinerea 891045146           33.25            35.65
## ..                  ...       ...             ...              ...
## Variables not shown: COORDINATE_ROUNDED (chr),
##      COUNTRY_DERIVED_FROM_COORDINATES (chr), GEODETIC_DATUM_ASSUMED_WGS84
##      (chr), MODIFIED_DATE_UNLIKELY (chr)
```

split, expand, and remove an issue class


```r
res %>% occ_issues(-gass84, mutate = "split_expand")
```

```
## Records found [961726] 
## Records returned [9] 
## No. unique hierarchies [47] 
## No. media records [41] 
## Args [geometry=POLYGON((30.1 10.1, 10 20, 20 40, 40 40, 30.1 10.1)),
##      limit=50, fields=minimal] 
## First 10 rows of data
## 
##                  name       key decimalLatitude decimalLongitude
## 1   Mullus surmuletus 883516592           39.95            23.69
## 2         Coris julis 883499301           39.95            23.69
## 6  Diplodus annularis 883500975           39.95            23.69
## 21      Labrus merula 883514095           39.95            23.69
## 27    Apogon imberbis 883492366           39.95            23.69
## 35    Chromis chromis 883498119           39.95            23.69
## 36        Sarpa salpa 884056896           39.95            23.69
## 43    Diplodus sargus 883500984           39.95            23.69
## 44    Serranus scriba 884134809           39.95            23.69
## Variables not shown: COORDINATE_ROUNDED (chr),
##      COUNTRY_DERIVED_FROM_COORDINATES (chr)
```


### Other cleaning

* Contextual cleaning based on 
  * impossible lat/long values
  * expected habitat type
  * expected range of values
  * etc.
  
