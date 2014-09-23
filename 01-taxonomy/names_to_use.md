# You can get some plant names using `names_list`

By default gets generic names, and returns 10 items


```r
names_list()
```

```
##  [1] "Epilobium"           "Lundellianthus"      "Tricarpelema"       
##  [4] "Pitavia"             "Schlumbergera"       "Pothos"             
##  [7] "Sterigmapetalum"     "Heterothalamulopsis" "Degenia"            
## [10] "Saccocalyx"
```

Get 5 species names


```r
names_list('species', 5)
```

```
## [1] "Coriaria duthiei"    "Eugenia subundulata" "Abelia spathulata"  
## [4] "Lupinus subcuneatus" "Hieracium canescens"
```

Get 10 family names


```r
names_list('family', 10)
```

```
##  [1] "Codonaceae"       "Pterostemonaceae" "Altingiaceae"    
##  [4] "Coeleanthaceae"   "Dalbergiaceae"    "Salaxidaceae"    
##  [7] "Opiliaceae"       "Smilacaceae"      "Peganaceae"      
## [10] "Koeberliniaceae"
```
