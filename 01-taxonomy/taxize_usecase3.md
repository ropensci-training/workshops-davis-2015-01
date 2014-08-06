## Taxonomic hierarchy

A common task is getting the taxonomic tree upstream from your study taxa. We often know what family or order our taxa are in, but it we often don't know the tribes, subclasses, and superfamilies. taxize provides many avenues to getting classifications. Many are accessible via a single function (*classification*), including the Integrated Taxonomic Information System (ITIS) and National Center for Biotechnology Information (NCBI); and via the Catalogue of Life (see function *col_classification*):


```r
# Let's get classifications from ITIS using Taxonomic Serial Numbers. Note
# that we could use uBio instead.
class_list <- classification(splist, db = "itis")
```

```
## 
## Retrieving data for taxon 'Helianthus annuus'
## 
## 
## Retrieving data for taxon 'Pinus contorta'
## 
## 
## Retrieving data for taxon 'Collomia grandiflora'
## 
## 
## Retrieving data for taxon 'Abies magnifica'
## 
## 
## Retrieving data for taxon 'Rosa californica'
## 
## 
## Retrieving data for taxon 'Datura wrightii'
## 
## 
## Retrieving data for taxon 'Mimulus bicolor'
## 
## 
## Retrieving data for taxon 'Nicotiana glauca'
## 
## 
## Retrieving data for taxon 'Madia sativa'
## 
## 
## Retrieving data for taxon 'Bartlettia scaposa'
```

```r

# And we can attach these names to our allnames data.frame
library(plyr)
gethiernames <- function(x) {
    temp <- x[, c("rankName", "taxonName")]
    values <- data.frame(t(temp[, 2]))
    names(values) <- temp[, 1]
    return(values)
}
class_df <- ldply(class_list, gethiernames)
allnames_df <- merge(allnames, class_df, by.x = "spname", by.y = "Species")
allnames_df$spname <- as.character(allnames_df$spname)

# Now that we have allnames_df, we can start to see some relationships among
# species simply by their shared taxonomic names
allnames_df[1:2, ]
```

```
##               spname        comname                .id Kingdom
## 1    Abies magnifica     golden fir    Abies magnifica Plantae
## 2 Bartlettia scaposa Bartlett daisy Bartlettia scaposa Plantae
##       Subkingdom Infrakingdom     Division     Subdivision Infradivision
## 1 Viridaeplantae Streptophyta Tracheophyta Spermatophytina  Gymnospermae
## 2 Viridaeplantae Streptophyta Tracheophyta Spermatophytina  Angiospermae
##           Class Superorder     Order     Family      Genus
## 1     Pinopsida       <NA>   Pinales   Pinaceae      Abies
## 2 Magnoliopsida  Asteranae Asterales Asteraceae Bartlettia
```


We can also get downstream names, in this case all species from the genus *Apis*


```r
col_downstream(name = "Apis", downto = "Species")
```

```
## $Apis
##   childtaxa_id     childtaxa_name childtaxa_rank
## 1      6971712 Apis andreniformis        Species
## 2      6971713        Apis cerana        Species
## 3      6971714       Apis dorsata        Species
## 4      6971715        Apis florea        Species
## 5      6971716 Apis koschevnikovi        Species
## 6      6845885     Apis mellifera        Species
## 7      6971717   Apis nigrocincta        Species
```

