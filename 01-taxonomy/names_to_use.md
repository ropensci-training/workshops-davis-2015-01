# You can get some plant names using `names_list`

By default gets generic names, and returns 10 items


```r
names_list()
```

```
##  [1] "Campylanthera"   "Elatine"         "Conocephalum"   
##  [4] "Dicranella"      "Muraltia"        "Trachyphyllum"  
##  [7] "Ropalon"         "Orthostichidium" "Micromitrium"   
## [10] "Pleurocladopsis"
```


Get 5 species names


```r
names_list("species", 5)
```

```
## [1] "Metteniusa tessmanniana"      "Metzgeria leptoneura"        
## [3] "Betula zinserlingii"          "Rinorea multivenosa"         
## [5] "Bryolawtonia vancouveriensis"
```


Get 10 family names


```r
names_list("family", 10)
```

```
##  [1] "Cacaoaceae"     "Vernoniaceae"   "Platycladaceae" "Potaliaceae"   
##  [5] "Roxburghiaceae" "Rhinanthaceae"  "Polygalaceae"   "Tussilagaceae" 
##  [9] "Moraceae"       "Tapisciaceae"
```

