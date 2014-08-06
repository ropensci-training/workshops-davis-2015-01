## Collect common names from taxonomic names

You may want to collect taxonomic names for some reason in your research. taxize has a number of ways to do this. One is using `sci2comm` function


```r
splist <- c("Helianthus annuus", "Pinus contorta", "Collomia grandiflora", "Abies magnifica", 
    "Rosa californica", "Datura wrightii", "Mimulus bicolor", "Nicotiana glauca", 
    "Madia sativa", "Bartlettia scaposa")

comnames <- sci2comm(splist, db = "itis", simplify = TRUE)

# Unfortunately, common names are not standardized like species names, so
# there are multiple common names for each taxon
sapply(comnames, nrow)
```

```
##    Helianthus annuus       Pinus contorta Collomia grandiflora 
##                    4                   20                    2 
##      Abies magnifica     Rosa californica      Datura wrightii 
##                    5                    1                    3 
##      Mimulus bicolor     Nicotiana glauca         Madia sativa 
##                    1                    2                    3 
##   Bartlettia scaposa 
##                    1
```

```r

# So let's just take the first common name for each species
comnames_vec <- sapply(comnames, function(x) as.character(x$comname[[1]]), USE.NAMES = FALSE)

# And we can make a data.frame of our scientific and common names
(allnames <- data.frame(spname = splist, comname = comnames_vec))
```

```
##                                    spname                       comname
## Helianthus annuus       Helianthus annuus              common sunflower
## Pinus contorta             Pinus contorta                lodgepole pine
## Collomia grandiflora Collomia grandiflora        largeflowered collomia
## Abies magnifica           Abies magnifica                    golden fir
## Rosa californica         Rosa californica           California wildrose
## Datura wrightii           Datura wrightii            sacred thorn-apple
## Mimulus bicolor           Mimulus bicolor yellow and white monkeyflower
## Nicotiana glauca         Nicotiana glauca                  tree tobacco
## Madia sativa                 Madia sativa                 coast tarweed
## Bartlettia scaposa     Bartlettia scaposa                Bartlett daisy
```

