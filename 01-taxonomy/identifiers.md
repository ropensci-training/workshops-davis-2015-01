## taxize tries to make it easy to get identifiers from the various database sources


```r
knitr::opts_chunk$set(
  comment = "# ",
  error = FALSE,
  cache = TRUE,
  message = FALSE,
  warning = FALSE
)
```


Here, get identifiers from 5 different sources for *Poa annua*. Then we can pass those ids to other functions that act on those ids without any other input

*p.s. this also demonstrates the interactive prompt, as you'll see*


```r
library('taxize')
out <- get_ids(names="Poa annua", db = c('ncbi','itis','col','tropicos'))
```

## Get a classification

### From ITIS


```r
classification(out$itis)
```

```
#  $`41107`
#                name          rank
#  1          Plantae       Kingdom
#  2   Viridaeplantae    Subkingdom
#  3     Streptophyta  Infrakingdom
#  4     Tracheophyta      Division
#  5  Spermatophytina   Subdivision
#  6     Angiospermae Infradivision
#  7    Magnoliopsida         Class
#  8         Lilianae    Superorder
#  9           Poales         Order
#  10         Poaceae        Family
#  11             Poa         Genus
#  12       Poa annua       Species
#  
#  attr(,"class")
#  [1] "classification"
#  attr(,"db")
#  [1] "itis"
```

### From COL


```r
classification(out$col)
```

```
#  $`9791858`
#            name    rank
#  1      Plantae Kingdom
#  2 Tracheophyta  Phylum
#  3   Liliopsida   Class
#  4       Poales   Order
#  5      Poaceae  Family
#  6          Poa   Genus
#  7    Poa annua Species
#  
#  attr(,"class")
#  [1] "classification"
#  attr(,"db")
#  [1] "col"
```

### From NCBI


```r
classification(out$ncbi)
```

```
#  $`93036`
#                   name         rank
#  1  cellular organisms      no rank
#  2           Eukaryota superkingdom
#  3       Viridiplantae      kingdom
#  4        Streptophyta       phylum
#  5      Streptophytina      no rank
#  6         Embryophyta      no rank
#  7        Tracheophyta      no rank
#  8       Euphyllophyta      no rank
#  9       Spermatophyta      no rank
#  10      Magnoliophyta      no rank
#  11    Mesangiospermae      no rank
#  12         Liliopsida        class
#  13      Petrosaviidae      no rank
#  14        commelinids     subclass
#  15             Poales        order
#  16            Poaceae       family
#  17          BEP clade      no rank
#  18           Pooideae    subfamily
#  19              Poeae        tribe
#  20             Poinae     subtribe
#  21                Poa        genus
#  22          Poa annua      species
#  
#  attr(,"class")
#  [1] "classification"
#  attr(,"db")
#  [1] "ncbi"
```

## Get synonyms from Tropicos


```r
synonyms(out$itis)
```

```
#  $`41107`
#                            name    tsn
#  1      Poa annua var. aquatica 538978
#  2       Poa annua var. reptans 538979
#  3                  Aira pumila 785854
#  4             Catabrosa pumila 787993
#  5               Ochlopoa annua 791574
#  6               Poa aestivalis 793946
#  7                   Poa algida 793954
#  8         Poa annua var. annua 802116
#  9     Poa annua var. eriolepis 802117
#  10 Poa annua var. rigidiuscula 802119
#  11        Poa annua f. reptans 803667
```

## Many names - the ids class

In this case get many identifiers for many names, then pass in identifiers to get many classifications


```r
mynames <- c("Helianthus annuus","Pinus contorta","Collomia grandiflora")
out <- get_ids(names=mynames, db = c('ncbi','itis','col','tropicos'))
```


```r
out$tropicos
```

```
#     Helianthus annuus       Pinus contorta Collomia grandiflora
#             "2700851"           "24900183"           "25800485"
#  attr(,"class")
#  [1] "tpsid"
#  attr(,"uri")
#  [1] "http://tropicos.org/Name/2700851"  "http://tropicos.org/Name/24900183"
#  [3] "http://tropicos.org/Name/25800485"
```

```r
class(out)
```

```
#  [1] "ids"
```

```r
class(out$col)
```

```
#  [1] "colid"
```

```r
classification(out$col)
```

```
#  $`17800756`
#                 name    rank
#  1           Plantae Kingdom
#  2      Tracheophyta  Phylum
#  3     Magnoliopsida   Class
#  4         Asterales   Order
#  5        Asteraceae  Family
#  6        Helianthus   Genus
#  7 Helianthus annuus Species
#  
#  $`18158354`
#              name    rank
#  1        Plantae Kingdom
#  2   Tracheophyta  Phylum
#  3      Pinopsida   Class
#  4        Pinales   Order
#  5       Pinaceae  Family
#  6          Pinus   Genus
#  7 Pinus contorta Species
#  
#  $`18772549`
#                    name    rank
#  1              Plantae Kingdom
#  2         Tracheophyta  Phylum
#  3        Magnoliopsida   Class
#  4             Ericales   Order
#  5        Polemoniaceae  Family
#  6             Collomia   Genus
#  7 Collomia grandiflora Species
#  
#  attr(,"class")
#  [1] "classification"
#  attr(,"db")
#  [1] "col"
```
