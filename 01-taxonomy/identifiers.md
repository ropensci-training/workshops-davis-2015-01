## taxize tries to make it easy to get identifiers from the various database sources

Here, get identifiers from 5 different sources for *Poa annua*. Then we can pass those ideas to other functions that act on those ids without any other input

*p.s. this also demonstrates the interactive prompt, as you'll see*


```r
library(taxize)
out <- get_ids(names = "Poa annua", db = c("ncbi", "itis", "col", "eol", "tropicos"))
```

```
##      colid      name    rank        status    acc_name
## 1  9791858 Poa annua Species accepted name        <NA>
## 2 10003530 Poa annua Species       synonym Poa infirma
##       eolid                                   name source
## 1  43530222                           Poa annua L.   GBIF
## 2  46196944                           Poa annua L.   ITIS
## 3  53014630                           Poa annua L.    COL
## 4  43531857       Poa aestivalis J.Presl & C.Presl   GBIF
## 5  43530223 Poa annua var. rigidiuscula L.H. Dewey   GBIF
## 6  43530884            Poa royleana Nees ex Steud.   GBIF
## 7  43531303                       Poa meyenii Nees   GBIF
## 8  43531601                  Poa hohenackeri Trin.   GBIF
## 9  43565964          Ochlopoa annua (L.) H. Scholz   GBIF
## 10 50836543                              Poa annua   NCBI
## 11 43518589                      Aira pumila Pursh   GBIF
##        tpsid                        name         rank       status
## 1   25509881                   Poa annua          sp.   Legitimate
## 2   25512377      Poa annua var. reptans         var.   No opinion
## 3   25514155 Poa annua var. rigidiuscula         var.   No opinion
## 4   25516124   Poa annua subsp. pratense       subsp.   No opinion
## 5   25517736        Poa annua var. annua         var.   No opinion
## 6   25537474         Poa annua fo. annua          fo.   No opinion
## 7   25538408      Poa annua subsp. annua       subsp.   No opinion
## 8   25538823     Poa annua var. aquatica         var.   No opinion
## 9   25538851      Poa annua var. stricta         var.   No opinion
## 10  25540127       Poa annua var. typica         var.      Invalid
## 11  25543952   Poa annua subsp. pilantha       subsp.   No opinion
## 12  25547854       Poa annua var. exilis         var.   No opinion
## 13  25549585      Poa annua var. pygmaea         var.      Invalid
## 14  25550450  Poa annua var. sikkimensis         var.   No opinion
## 15  25550451   Poa annua var. nepalensis         var.   No opinion
## 16  25550455    Poa annua var. maroccana         var.   No opinion
## 17  25550983       Poa annua fo. reptans          fo.   No opinion
## 18  25552610   Poa annua var. hypsophila         var.   No opinion
## 19  25556963     Poa annua var. pilantha         var.   No opinion
## 20  25557595             Poa ser. Annuae         ser.   No opinion
## 21  25558635   Poa annua var. tommasinii         var. Illegitimate
## 22  50062684     Poa [ unranked ] Annuae [ unranked ]   Legitimate
## 23  50062691     Poa [ unranked ] Annuae [ unranked ] Illegitimate
## 24  50062695            Poa sect. Annuae        sect.      Invalid
## 25  50063800     Poa annua subsp. exilis       subsp.   No opinion
## 26  50063801     Poa annua subsp. supina       subsp. Illegitimate
## 27  50077909      Poa annua subsp. varia       subsp.      Invalid
## 28  50077910    Poa annua unranked varia   [unranked]   No opinion
## 29  50119145    Poa annua var. eriolepis         var.   No opinion
## 30  50133141      Poa annua subsp. varia       subsp.   Legitimate
## 31  50154055       Poa annua var. supina         var.   No opinion
## 32  50155725   Poa annua var. raniglumis         var.   No opinion
## 33  50157106     Poa annua proles supina       proles   No opinion
## 34  50157109     Poa annua var. racemosa         var.   No opinion
## 35  50157110     Poa annua var. rigidula         var.   No opinion
## 36  50157407     Poa annua var. triflora         var.   No opinion
## 37  50158097    Poa annua subvar. minima      subvar.   No opinion
## 38  50158098       Poa annua var. minima         var.   No opinion
## 39  50182047       Poa annua var. supina         var.   Legitimate
## 40  50240461        Poa annua fo. maxima          fo.   No opinion
## 41  50243156     Poa annua fo. macarrima          fo.      Invalid
## 42  50267768   Poa annua fo. remotiflora          fo.   No opinion
## 43  50267769      Poa annua var. viridis         var.   No opinion
## 44  50267770       Poa annua fo. viridis          fo.   No opinion
## 45  50267771    Poa annua fo. lanuginosa          fo.   No opinion
## 46  50267772        Poa annua fo. ovalis          fo.   No opinion
## 47  50267774        Poa annua var. picta         var.   No opinion
## 48  50267776         Poa annua fo. picta          fo.   No opinion
## 49  50267778    Poa annua var. rivulorum         var.   No opinion
## 50  50267779   Poa annua fo. macranthera          fo.   No opinion
## 51  50278321   Poa annua var. pauciflora         var.   No opinion
## 52  50315599  Poa annua subsp. notabilis       subsp.   No opinion
## 53  50315610 Poa annua subsp. raniglunis       subsp.   No opinion
## 54  50315616      Poa annua fo. purpurea          fo.   No opinion
## 55 100386563      Poa annua var. arenosa         var.      Invalid
## 56 100386564     Poa annua var. alpigena         var.   No opinion
```


## get classification from ITIS


```r
classification(out$itis)
```

```
## $`Poa annua`
##         rankName       taxonName    tsn
## 1        Kingdom         Plantae 202422
## 2     Subkingdom  Viridaeplantae 846492
## 3   Infrakingdom    Streptophyta 846494
## 4       Division    Tracheophyta 846496
## 5    Subdivision Spermatophytina 846504
## 6  Infradivision    Angiospermae 846505
## 7          Class   Magnoliopsida  18063
## 8     Superorder        Lilianae 846542
## 9          Order          Poales 846620
## 10        Family         Poaceae  40351
## 11         Genus             Poa  41074
## 12       Species       Poa annua  41107
```


## get synonyms from Tropicos


```r
synonyms(out$tropicos)
```

```
## $`Poa annua`
##       NameId              ScientificName
## 1   25503923                 Aira pumila
## 8   25503925                 Aira pumila
## 9   25513515            Catabrosa pumila
## 16  25513642          Eragrostis infirma
## 20  25521823         Festuca tenuiculmis
## 21  25513728         Megastachya infirma
## 24  50231428              Ochlopoa annua
## 28  25512823              Poa aestivalis
## 39  25538791                  Poa algida
## 40  25512724                  Poa algida
## 48  25550983       Poa annua fo. reptans
## 53  25517736        Poa annua var. annua
## 56  25538823     Poa annua var. aquatica
## 60  50119145    Poa annua var. eriolepis
## 63  25512377      Poa annua var. reptans
## 68  25514155 Poa annua var. rigidiuscula
## 73  25555526            Poa bipollicaris
## 77  25515915            Poa crassinervis
## 79  25561445             Poa hohenackeri
## 81 100391965                 Poa humilis
## 82  25514158                 Poa infirma
## 87  25512725                 Poa meyenii
## 93  50200166                Poa puberula
## 94  25528166                Poa royleana
##                      ScientificNameWithAuthors  Family
## 1                            Aira pumila Pursh Poaceae
## 8                   Aira pumila Vill. ex Trin. Poaceae
## 9     Catabrosa pumila (Pursh) Roem. & Schult. Poaceae
## 16           Eragrostis infirma (Kunth) Steud. Poaceae
## 20                   Festuca tenuiculmis Tovar Poaceae
## 21 Megastachya infirma (Kunth) Roem. & Schult. Poaceae
## 24               Ochlopoa annua (L.) H. Scholz Poaceae
## 28                     Poa aestivalis J. Presl Poaceae
## 39                     Poa algida (Sol.) Rupr. Poaceae
## 40                            Poa algida Trin. Poaceae
## 48  Poa annua fo. reptans (Hausskn.) T. Koyama Poaceae
## 53                       Poa annua var. annua  Poaceae
## 56               Poa annua var. aquatica Asch. Poaceae
## 60           Poa annua var. eriolepis E. Desv. Poaceae
## 63             Poa annua var. reptans Hausskn. Poaceae
## 68      Poa annua var. rigidiuscula L.H. Dewey Poaceae
## 73                    Poa bipollicaris Hochst. Poaceae
## 77                      Poa crassinervis Honda Poaceae
## 79                       Poa hohenackeri Trin. Poaceae
## 81                            Poa humilis Lej. Poaceae
## 82                           Poa infirma Kunth Poaceae
## 87                    Poa meyenii Nees & Meyen Poaceae
## 93                         Poa puberula Steud. Poaceae
## 94                 Poa royleana Nees ex Steud. Poaceae
```


## Many names

In this case get many identifiers for many names, then pass in identifiers to get many classifications


```r
mynames <- c("Helianthus annuus", "Pinus contorta", "Collomia grandiflora")
out <- get_ids(names = mynames, db = c("ncbi", "itis", "col", "eol", "tropicos"))
```

```
##       eolid                                                         name
## 1  43835813                                         Helianthus annuus L.
## 2  46180859                                         Helianthus annuus L.
## 3  52926497                                         Helianthus annuus L.
## 4  43835841 Helianthus annuus L. subsp. lenticularis (Douglas) Cockerell
## 5  43835842             Helianthus annuus subsp. jaegeri (Heiser) Heiser
## 6  43835826          Helianthus annuus L. var. texanus (Heiser) Shinners
## 7  50883433                                            Helianthus annuus
## 8  53417541                     Helianthus annuus fasciation phytoplasma
## 9  50883498                   Helianthus annuus x Helianthus argophyllus
## 10 43836079                   Helianthus annuus × Helianthus argophyllus
## 11 50883499        Helianthus annuus x Helianthus debilis subsp. debilis
## 12 43836080        Helianthus annuus × Helianthus debilis subsp. debilis
##    source
## 1    GBIF
## 2    ITIS
## 3     COL
## 4    GBIF
## 5    GBIF
## 6    GBIF
## 7    NCBI
## 8    NCBI
## 9    NCBI
## 10   GBIF
## 11   NCBI
## 12   GBIF
##       eolid                                               name source
## 1  44398364                   Pinus contorta Douglas ex Loudon   GBIF
## 2  46216292                   Pinus contorta Douglas ex Loudon   ITIS
## 3  53084713                   Pinus contorta Douglas ex Loudon    COL
## 4  24954444                                     Pinus contorta   IUCN
## 5  50827991                                     Pinus contorta   NCBI
## 6  44398365      Pinus contorta var. murrayana (Balf.) Engelm.   GBIF
## 7  46216296      Pinus contorta var. murrayana (Balf.) Engelm.   ITIS
## 8  53084715      Pinus contorta var. murrayana (Balf.) Engelm.    COL
## 9  50827994                      Pinus contorta var. murrayana   NCBI
## 10 46216294        Pinus contorta var. bolanderi (Parl.) Vasey   ITIS
## 11 50827993                      Pinus contorta var. bolanderi   NCBI
## 12 44398367              Pinus contorta var. latifolia Engelm.   GBIF
## 13 53084714              Pinus contorta var. latifolia Engelm.    COL
## 14 46216295 Pinus contorta var. latifolia Engelm. ex S. Watson   ITIS
## 15 53084716                       Pinus contorta var. contorta    COL
## 16 50827992                     Pinus contorta subsp. contorta   NCBI
## 17 44398366     Pinus contorta var. contorta Douglas ex Loudon   GBIF
## 18 46216293     Pinus contorta var. contorta Douglas ex Loudon   ITIS
## 19 44398369         Pinus contorta var. yukonensis W.L. Strong   GBIF
##      eolid                                   name source
## 1 46170153 Collomia grandiflora Douglas ex Lindl.   ITIS
## 2 52804720 Collomia grandiflora Douglas ex Lindl.    COL
## 3 50873299                   Collomia grandiflora   NCBI
## 4 44178704  Collomia grandiflora Dougl. ex Lindl.   GBIF
##        tpsid                                  name   rank     status
## 1    2700851                     Helianthus annuus    sp. Legitimate
## 2    2700852   Helianthus annuus subsp. couplandii subsp. No opinion
## 3    2700853 Helianthus annuus subsp. lenticularis subsp. No opinion
## 4    2702619         Helianthus annuus var. annuus   var. No opinion
## 5    2702620    Helianthus annuus var. armavirskij   var. No opinion
## 6    2702621        Helianthus annuus var. bicolor   var. No opinion
## 7    2702622   Helianthus annuus var. californicus   var. No opinion
## 8    2702623 Helianthus annuus var. gallardiflorus   var. No opinion
## 9    2702624       Helianthus annuus var. globosus   var.    Invalid
## 10   2702625    Helianthus annuus var. intermedius   var. No opinion
## 11   2702626     Helianthus annuus var. primulinus   var. No opinion
## 12   2702627      Helianthus annuus var. uniflorus   var. No opinion
## 13   2702628  Helianthus annuus var. vinossissimus   var. No opinion
## 14   2702629        Helianthus annuus var. zonatus   var. No opinion
## 15   2724044    Helianthus annuus var. macrocarpus   var. No opinion
## 16   2724045      Helianthus annuus subsp. jaegeri subsp. No opinion
## 17   2724046       Helianthus annuus subsp. annuus subsp. No opinion
## 18   2724756          Helianthus annuus fo. fallax    fo. No opinion
## 19   2724757          Helianthus annuus fo. annuus    fo. No opinion
## 20   2726013      Helianthus annuus subsp. texanus subsp. No opinion
## 21  50069938      Helianthus annuus var. coronatus   var. No opinion
## 22  50069939         Helianthus annuus var. aridus   var. No opinion
## 23  50069940      Helianthus annuus var. latibasis   var. No opinion
## 24  50069941    Helianthus annuus fo. lenticularis    fo. No opinion
## 25  50071063   Helianthus annuus subsp. petiolaris subsp. No opinion
## 26  50071132   Helianthus annuus var. lenticularis   var. No opinion
## 27  50229527        Helianthus annuus var. texanus   var. No opinion
## 28  50289543       Helianthus annuus var. citrinus   var. No opinion
## 29 100000278        Helianthus annuus x petiolaris   var. No opinion
##        tpsid                                name       rank     status
## 1   24900183                      Pinus contorta        sp. No opinion
## 2   24900184       Pinus contorta var. bolanderi       var. No opinion
## 3   24900185       Pinus contorta var. latifolia       var. No opinion
## 4   24900186       Pinus contorta var. murrayana       var. No opinion
## 5   24900317     Pinus contorta subsp. murrayana     subsp. No opinion
## 6   24900318     Pinus contorta subsp. latifolia     subsp. No opinion
## 7   24900433     Pinus contorta var. hendersonii       var. No opinion
## 8   24900487 Pinus contorta unranked hendersonii [unranked] No opinion
## 9   24900528        Pinus contorta var. contorta       var. No opinion
## 10  24900627      Pinus contorta subsp. contorta     subsp. No opinion
## 11  24900810     Pinus contorta subsp. bolanderi     subsp. No opinion
## 12  24901682       Pinus contorta var. bolanderi       var. No opinion
## 13  50231950       Pinus contorta var. bolanderi       var. No opinion
## 14  50231960     Pinus contorta subsp. murrayana     subsp. No opinion
## 15 100351799             Pinus subsect. Contorta   subsect. No opinion
## 16 100363705      Pinus contorta var. yukonensis       var. No opinion
##        tpsid                                  name rank     status
## 1   25800485                  Collomia grandiflora  sp. No opinion
## 2   50130471   Collomia grandiflora var. axillaris var. No opinion
## 3   50130472 Collomia grandiflora var. grandiflora var. No opinion
## 4  100314137    Collomia grandiflora fo. axillaris  fo. No opinion
## 5  100314138   Collomia grandiflora fo. cryptantha  fo. No opinion
## 6  100314139      Collomia grandiflora fo. diffusa  fo. No opinion
## 7  100314140       Collomia grandiflora fo. scabra  fo. No opinion
## 8  100314141   Collomia grandiflora fo. tenuiflora  fo. No opinion
## 9  100314142     Collomia grandiflora var. diffusa var. No opinion
## 10 100314143  Collomia grandiflora var. tenuiflora var. No opinion
```

```r
classification(out)
```

```
## $ncbi
## $ncbi$`Helianthus annuus`
##          ScientificName         Rank    UID
## 1    cellular organisms      no rank 131567
## 2             Eukaryota superkingdom   2759
## 3         Viridiplantae      kingdom  33090
## 4          Streptophyta       phylum  35493
## 5        Streptophytina      no rank 131221
## 6           Embryophyta      no rank   3193
## 7          Tracheophyta      no rank  58023
## 8         Euphyllophyta      no rank  78536
## 9         Spermatophyta      no rank  58024
## 10        Magnoliophyta      no rank   3398
## 11       eudicotyledons      no rank  71240
## 12  core eudicotyledons      no rank  91827
## 13             asterids     subclass  71274
## 14          campanulids      no rank  91882
## 15            Asterales        order   4209
## 16           Asteraceae       family   4210
## 17          Asteroideae    subfamily 102804
## 18 Heliantheae alliance      no rank 911341
## 19          Heliantheae        tribe 102814
## 20           Helianthus        genus   4231
## 21    Helianthus annuus      species   4232
## 
## $ncbi$`Pinus contorta`
##        ScientificName         Rank    UID
## 1  cellular organisms      no rank 131567
## 2           Eukaryota superkingdom   2759
## 3       Viridiplantae      kingdom  33090
## 4        Streptophyta       phylum  35493
## 5      Streptophytina      no rank 131221
## 6         Embryophyta      no rank   3193
## 7        Tracheophyta      no rank  58023
## 8       Euphyllophyta      no rank  78536
## 9       Spermatophyta      no rank  58024
## 10      Coniferophyta      no rank   3312
## 11      Coniferopsida        class  58019
## 12        Coniferales        order   3313
## 13           Pinaceae       family   3318
## 14              Pinus        genus   3337
## 15              Pinus     subgenus 139271
## 16     Pinus contorta      species   3339
## 
## $ncbi$`Collomia grandiflora`
##          ScientificName         Rank    UID
## 1    cellular organisms      no rank 131567
## 2             Eukaryota superkingdom   2759
## 3         Viridiplantae      kingdom  33090
## 4          Streptophyta       phylum  35493
## 5        Streptophytina      no rank 131221
## 6           Embryophyta      no rank   3193
## 7          Tracheophyta      no rank  58023
## 8         Euphyllophyta      no rank  78536
## 9         Spermatophyta      no rank  58024
## 10        Magnoliophyta      no rank   3398
## 11       eudicotyledons      no rank  71240
## 12  core eudicotyledons      no rank  91827
## 13             asterids     subclass  71274
## 14             Ericales        order  41945
## 15        Polemoniaceae       family  24584
## 16             Collomia        genus  40760
## 17 Collomia grandiflora      species  66234
## 
## 
## $itis
## $itis$`Helianthus annuus`
##         rankName         taxonName    tsn
## 1        Kingdom           Plantae 202422
## 2     Subkingdom    Viridaeplantae 846492
## 3   Infrakingdom      Streptophyta 846494
## 4       Division      Tracheophyta 846496
## 5    Subdivision   Spermatophytina 846504
## 6  Infradivision      Angiospermae 846505
## 7          Class     Magnoliopsida  18063
## 8     Superorder         Asteranae 846535
## 9          Order         Asterales  35419
## 10        Family        Asteraceae  35420
## 11         Genus        Helianthus  36611
## 12       Species Helianthus annuus  36616
## 
## $itis$`Pinus contorta`
##         rankName       taxonName    tsn
## 1        Kingdom         Plantae 202422
## 2     Subkingdom  Viridaeplantae 846492
## 3   Infrakingdom    Streptophyta 846494
## 4       Division    Tracheophyta 846496
## 5    Subdivision Spermatophytina 846504
## 6  Infradivision    Gymnospermae 846506
## 7          Class       Pinopsida 500009
## 8          Order         Pinales 500028
## 9         Family        Pinaceae  18030
## 10         Genus           Pinus  18035
## 11       Species  Pinus contorta 183327
## 
## $itis$`Collomia grandiflora`
##         rankName            taxonName    tsn
## 1        Kingdom              Plantae 202422
## 2     Subkingdom       Viridaeplantae 846492
## 3   Infrakingdom         Streptophyta 846494
## 4       Division         Tracheophyta 846496
## 5    Subdivision      Spermatophytina 846504
## 6  Infradivision         Angiospermae 846505
## 7          Class        Magnoliopsida  18063
## 8     Superorder            Asteranae 846535
## 9          Order             Ericales  23443
## 10        Family        Polemoniaceae  30896
## 11         Genus             Collomia  31035
## 12       Species Collomia grandiflora  31037
## 
## 
## $col
## $col$`Helianthus annuus`
##    classif_name classif_rank classif_id
## 1       Plantae      Kingdom   15610504
## 2  Tracheophyta       Phylum   15610505
## 3 Magnoliopsida        Class   15610506
## 4     Asterales        Order   15614747
## 5    Asteraceae       Family   15617169
## 6    Helianthus        Genus   15691642
## 
## $col$`Pinus contorta`
##   classif_name classif_rank classif_id
## 1      Plantae      Kingdom   15610504
## 2 Tracheophyta       Phylum   15610505
## 3    Pinopsida        Class   15612223
## 4      Pinales        Order   15612224
## 5     Pinaceae       Family   15613661
## 6        Pinus        Genus   15661926
## 
## $col$`Collomia grandiflora`
##    classif_name classif_rank classif_id
## 1       Plantae      Kingdom   15610504
## 2  Tracheophyta       Phylum   15610505
## 3 Magnoliopsida        Class   15610506
## 4      Ericales        Order   15610507
## 5 Polemoniaceae       Family   15617189
## 6      Collomia        Genus   15702987
## 
## 
## $eol
## $eol$`Helianthus annuus`
## [1] "No hierarchy information for 43835813"
## 
## $eol$`Pinus contorta`
## [1] "No hierarchy information for 44398364"
## 
## $eol$`Collomia grandiflora`
##     taxonID  scientificName     taxonRank
## 1  46150613         Plantae       kingdom
## 2  46159776  Viridaeplantae    subkingdom
## 3  46161961    Streptophyta  infrakingdom
## 4  46167532    Tracheophyta      division
## 5  46169010 Spermatophytina   subdivision
## 6  46169011    Angiospermae infradivision
## 7  46169012   Magnoliopsida         class
## 8  46169016       Asteranae    superorder
## 9  46169017        Ericales         order
## 10 46169946   Polemoniaceae        family
## 11 46170148  Collomia Nutt.         genus
## 
## 
## $tropicos
## $tropicos$`Helianthus annuus`
##      NameId ScientificName       Rank
## 1  43000109  Equisetopsida      class
## 2  43000013    Magnoliidae   subclass
## 3 100352415      Asteranae superorder
## 4  43000082      Asterales      order
## 5  50307371     Asteraceae     family
## 6  40022652     Helianthus      genus
## 
## $tropicos$`Pinus contorta`
##     NameId ScientificName     Rank
## 1 43000109  Equisetopsida    class
## 2 50324780        Pinidae subclass
## 3 50324779        Pinales    order
## 4 42000417       Pinaceae   family
## 5 40009142          Pinus    genus
## 
## $tropicos$`Collomia grandiflora`
##      NameId ScientificName       Rank
## 1  43000109  Equisetopsida      class
## 2  43000013    Magnoliidae   subclass
## 3 100352415      Asteranae superorder
## 4  43000048       Ericales      order
## 5  42000286  Polemoniaceae     family
## 6  40012270       Collomia      genus
```

