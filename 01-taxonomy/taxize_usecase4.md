## Aggregate a data set to a taxonomic level



### Load libraries


```r
library('taxize')
library('vegan')
```

### Use the dune dataset from the vegan package


```r
data(dune, package='vegan')
dune <- dune[,-c(22:30)] # take a subset
species <- c("Bellis perennis", "Empetrum nigrum", "Juncus bufonius",
"Juncus articulatus","Aira praecox", "Eleocharis parvula", "Rumex acetosa", "Vicia lathyroides",
"Brachythecium rutabulum", "Ranunculus flammula", "Cirsium arvense",
"Hypochaeris radicata", "Leontodon autumnalis", "Potentilla palustris",
"Poa pratensis", "Calliergonella cuspidata", "Trifolium pratense",
"Trifolium repens", "Anthoxanthum odoratum", "Salix repens", "Achillea millefolium")
colnames(dune) <- species
head(dune)
```

```
#     Bellis perennis Empetrum nigrum Juncus bufonius Juncus articulatus
#  2                3               0               0                  0
#  13               0               0               3                  0
#  4                2               0               0                  0
#  16               0               0               0                  3
#  6                0               0               0                  0
#  1                0               0               0                  0
#     Aira praecox Eleocharis parvula Rumex acetosa Vicia lathyroides
#  2             0                  0             0                 0
#  13            0                  0             0                 0
#  4             0                  0             0                 0
#  16            0                  8             0                 0
#  6             0                  0             6                 0
#  1             0                  0             0                 0
#     Brachythecium rutabulum Ranunculus flammula Cirsium arvense
#  2                        0                   0               0
#  13                       0                   2               0
#  4                        2                   0               2
#  16                       4                   2               0
#  6                        6                   0               0
#  1                        0                   0               0
#     Hypochaeris radicata Leontodon autumnalis Potentilla palustris
#  2                     0                    5                    0
#  13                    0                    2                    0
#  4                     0                    2                    0
#  16                    0                    0                    0
#  6                     0                    3                    0
#  1                     0                    0                    0
#     Poa pratensis Calliergonella cuspidata Trifolium pratense
#  2              4                        0                  0
#  13             2                        0                  0
#  4              4                        0                  0
#  16             0                        3                  0
#  6              3                        0                  5
#  1              4                        0                  0
#     Trifolium repens Anthoxanthum odoratum Salix repens
#  2                 5                     0            0
#  13                2                     0            0
#  4                 1                     0            0
#  16                0                     0            0
#  6                 5                     3            0
#  1                 0                     0            0
#     Achillea millefolium
#  2                     3
#  13                    0
#  4                     0
#  16                    0
#  6                     2
#  1                     1
```

### Aggregate sample to families


```r
agg <- tax_agg(dune, rank = 'family', db = 'ncbi')
agg
```

```
#  
#  	Aggregated community data
#  
#  Level of Aggregation: FAMILY
#  No. taxa before aggregation: 21
#  No. taxa after aggregation: 12
#  No. taxa not found: 0
```

### Extract aggregated community data matrix for further usage

See that data is now aggregated from the original at the species level to the family level


```r
head(dune)
```

```
#     Bellis perennis Empetrum nigrum Juncus bufonius Juncus articulatus
#  2                3               0               0                  0
#  13               0               0               3                  0
#  4                2               0               0                  0
#  16               0               0               0                  3
#  6                0               0               0                  0
#  1                0               0               0                  0
#     Aira praecox Eleocharis parvula Rumex acetosa Vicia lathyroides
#  2             0                  0             0                 0
#  13            0                  0             0                 0
#  4             0                  0             0                 0
#  16            0                  8             0                 0
#  6             0                  0             6                 0
#  1             0                  0             0                 0
#     Brachythecium rutabulum Ranunculus flammula Cirsium arvense
#  2                        0                   0               0
#  13                       0                   2               0
#  4                        2                   0               2
#  16                       4                   2               0
#  6                        6                   0               0
#  1                        0                   0               0
#     Hypochaeris radicata Leontodon autumnalis Potentilla palustris
#  2                     0                    5                    0
#  13                    0                    2                    0
#  4                     0                    2                    0
#  16                    0                    0                    0
#  6                     0                    3                    0
#  1                     0                    0                    0
#     Poa pratensis Calliergonella cuspidata Trifolium pratense
#  2              4                        0                  0
#  13             2                        0                  0
#  4              4                        0                  0
#  16             0                        3                  0
#  6              3                        0                  5
#  1              4                        0                  0
#     Trifolium repens Anthoxanthum odoratum Salix repens
#  2                 5                     0            0
#  13                2                     0            0
#  4                 1                     0            0
#  16                0                     0            0
#  6                 5                     3            0
#  1                 0                     0            0
#     Achillea millefolium
#  2                     3
#  13                    0
#  4                     0
#  16                    0
#  6                     2
#  1                     1
```

```r
head(agg$x)
```

```
#     Asteraceae Brachytheciaceae Cyperaceae Ericaceae Fabaceae Hypnaceae
#  2          11                0          0         0        5         0
#  13          2                0          0         0        2         0
#  4           6                2          0         0        1         0
#  16          0                4          8         0        0         3
#  6           5                6          0         0       10         0
#  1           1                0          0         0        0         0
#     Juncaceae Poaceae Polygonaceae Ranunculaceae Rosaceae Salicaceae
#  2          0       4            0             0        0          0
#  13         3       2            0             2        0          0
#  4          0       4            0             0        0          0
#  16         3       0            0             2        0          0
#  6          0       6            6             0        0          0
#  1          0       4            0             0        0          0
```

Check which taxa have been aggregated


```r
agg$by
```

```
#                     variable              agg
#  1           Bellis perennis       Asteraceae
#  2           Empetrum nigrum        Ericaceae
#  3           Juncus bufonius        Juncaceae
#  4        Juncus articulatus        Juncaceae
#  5              Aira praecox          Poaceae
#  6        Eleocharis parvula       Cyperaceae
#  7             Rumex acetosa     Polygonaceae
#  8         Vicia lathyroides         Fabaceae
#  9   Brachythecium rutabulum Brachytheciaceae
#  10      Ranunculus flammula    Ranunculaceae
#  11          Cirsium arvense       Asteraceae
#  12     Hypochaeris radicata       Asteraceae
#  13     Leontodon autumnalis       Asteraceae
#  14     Potentilla palustris         Rosaceae
#  15            Poa pratensis          Poaceae
#  16 Calliergonella cuspidata        Hypnaceae
#  17       Trifolium pratense         Fabaceae
#  18         Trifolium repens         Fabaceae
#  19    Anthoxanthum odoratum          Poaceae
#  20             Salix repens       Salicaceae
#  21     Achillea millefolium       Asteraceae
```
