## Taxonomic hierarchy



### Hierarchies

A common task is getting the taxonomic tree upstream from your study taxa. We often know what family or order our taxa are in, but it we often don't know the tribes, subclasses, and superfamilies. taxize provides many avenues to getting classifications. Many are accessible via a single function (*classification*), including the Integrated Taxonomic Information System (ITIS) and National Center for Biotechnology Information (NCBI); and via the Catalogue of Life (see function *col_classification*):


Let's get classifications from ITIS using Taxonomic Serial Numbers. Note that we could use uBio instead.


```r
library('taxize')
splist <- c("Helianthus annuus","Pinus contorta","Collomia grandiflora","Abies magnifica","Rosa californica","Datura wrightii","Mimulus bicolor","Nicotiana glauca","Madia sativa","Bartlettia scaposa")
class_list <- classification(splist, db="itis")
```

And we can attach these names to our allnames data.frame


```r
class_df <- cbind(class_list)
class_df$spname <- splist
```

Now that we have allnames_df, we can start to see some relationships among species simply by their shared taxonomic names


```r
class_df[1:2,]
```

```
#    kingdom     subkingdom infrakingdom     division     subdivision
#  1 Plantae Viridaeplantae Streptophyta Tracheophyta Spermatophytina
#  2 Plantae Viridaeplantae Streptophyta Tracheophyta Spermatophytina
#    infradivision         class superorder     order     family      genus
#  1  Angiospermae Magnoliopsida  Asteranae Asterales Asteraceae Helianthus
#  2  Gymnospermae     Pinopsida       <NA>   Pinales   Pinaceae      Pinus
#              species            spname
#  1 Helianthus annuus Helianthus annuus
#  2    Pinus contorta    Pinus contorta
```

### downstream

We can also get downstream names, in this case all species from the genus *Apis*


```r
downstream("Apis", db="col", downto="Species")
```

```
#  $Apis
#    childtaxa_id     childtaxa_name childtaxa_rank
#  1      6971712 Apis andreniformis        Species
#  2      6971713        Apis cerana        Species
#  3      6971714       Apis dorsata        Species
#  4      6971715        Apis florea        Species
#  5      6971716 Apis koschevnikovi        Species
#  6      6845885     Apis mellifera        Species
#  7      6971717   Apis nigrocincta        Species
#  
#  attr(,"class")
#  [1] "downstream"
#  attr(,"db")
#  [1] "col"
```

Other searches:

* Get all genera in the rush family `downstream('Juncaceae', db='col', downto='Genus')`
* Get all phyla in the animal kingdom `downstream('Animalia', db='col', downto='Phylum')`

### Coming soon....

__UPSTREAM!__


```r
upstream ("Helianthus annuus", rank="genus")

$Helianthus annuus`
             name             rank
1            Helianthus       Genus
2            Iva              Genus
3            Achillea         Genus
4            ...etc         ...etc
```

