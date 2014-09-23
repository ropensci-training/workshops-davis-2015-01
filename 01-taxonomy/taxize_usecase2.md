## Get common names from taxonomic names



You may want to collect taxonomic names for some reason in your research. taxize has a number of ways to do this. One is using `sci2comm` function

Define names


```r
library('taxize')
splist <- c("Helianthus annuus","Pinus contorta","Collomia grandiflora","Abies magnifica","Rosa californica","Datura wrightii","Mimulus bicolor","Nicotiana glauca","Madia sativa","Bartlettia scaposa")
```

Search for common names


```r
comnames <- sci2comm(splist, db="itis", simplify=TRUE)
```

Unfortunately, common names are not standardized like species names, so there are multiple common names for each taxon


```r
sapply(comnames, length)
```

```
#     Helianthus annuus       Pinus contorta Collomia grandiflora 
#                     4                    4                    2 
#       Abies magnifica     Rosa californica      Datura wrightii 
#                     5                    1                    3 
#       Mimulus bicolor     Nicotiana glauca         Madia sativa 
#                     1                    2                    3 
#    Bartlettia scaposa 
#                     1
```

So let's just take the first common name for each species


```r
comnames_vec <- unname(sapply(comnames, function(x) x[[1]]))
```

And we can make a `data.frame` of our scientific and common names


```r
(allnames <- data.frame(spname = splist, comname = comnames_vec))
```

```
#                   spname                       comname
#  1     Helianthus annuus              common sunflower
#  2        Pinus contorta                lodgepole pine
#  3  Collomia grandiflora        largeflowered collomia
#  4       Abies magnifica                    golden fir
#  5      Rosa californica           California wildrose
#  6       Datura wrightii            sacred thorn-apple
#  7       Mimulus bicolor yellow and white monkeyflower
#  8      Nicotiana glauca                  tree tobacco
#  9          Madia sativa                 coast tarweed
#  10   Bartlettia scaposa                Bartlett daisy
```
