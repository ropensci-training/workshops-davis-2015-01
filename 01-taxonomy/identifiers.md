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
out <- get_ids(names="Poa annua", db = c('ncbi','itis','col','eol','tropicos'))
```

```
#       colid      name    rank        status
#  1  9791858 Poa annua Species accepted name
#  2 10003530 Poa annua Species       synonym
#                                              source    acc_name
#  1 WCSP: World Checklist of Selected Plant Families        <NA>
#  2 WCSP: World Checklist of Selected Plant Families Poa infirma
#      pageid    eolid                                     name source
#  1  1114594 43518589                        Aira pumila Pursh   GBIF
#  2  1114594 43546338 Catabrosa pumila (Pursh) Roem. & Schult.   GBIF
#  3  1114594 43565964            Ochlopoa annua (L.) H. Scholz   GBIF
#  4  1114594 43531857         Poa aestivalis J.Presl & C.Presl   GBIF
#  5  1114594 57189638                                Poa annua   NCBI
#  6  1114594 50836543                                Poa annua   NCBI
#  7  1114594 43530222                             Poa annua L.   GBIF
#  8  1114594 46196944                             Poa annua L.   ITIS
#  9  1114594 53014630                             Poa annua L.    COL
#  10 7014286 43530226      Poa annua L. var. pilantha Ronniger   GBIF
#  11 1114594 43530229  Poa annua var. eriolepis E.Desv. in Gay   GBIF
#  12 1114594 43530223   Poa annua var. rigidiuscula L.H. Dewey   GBIF
#  13 1114594 43531601                    Poa hohenackeri Trin.   GBIF
#  14 1114594 43531303                         Poa meyenii Nees   GBIF
#  15 1114594 43530884              Poa royleana Nees ex Steud.   GBIF
#         tpsid                        name         rank       status
#  1   25509881                   Poa annua          sp.   Legitimate
#  2   25512377      Poa annua var. reptans         var.   No opinion
#  3   25514155 Poa annua var. rigidiuscula         var.   No opinion
#  4   25516124   Poa annua subsp. pratense       subsp.   No opinion
#  5   25517736        Poa annua var. annua         var.   No opinion
#  6   25537474         Poa annua fo. annua          fo.   No opinion
#  7   25538408      Poa annua subsp. annua       subsp.   No opinion
#  8   25538823     Poa annua var. aquatica         var.   No opinion
#  9   25538851      Poa annua var. stricta         var.   No opinion
#  10  25540127       Poa annua var. typica         var.      Invalid
#  11  25543952   Poa annua subsp. pilantha       subsp.   No opinion
#  12  25547854       Poa annua var. exilis         var.   No opinion
#  13  25549585      Poa annua var. pygmaea         var.      Invalid
#  14  25550450  Poa annua var. sikkimensis         var.   No opinion
#  15  25550451   Poa annua var. nepalensis         var.   No opinion
#  16  25550455    Poa annua var. maroccana         var.   No opinion
#  17  25550983       Poa annua fo. reptans          fo.   No opinion
#  18  25552610   Poa annua var. hypsophila         var.   No opinion
#  19  25556963     Poa annua var. pilantha         var.   No opinion
#  20  25557595             Poa ser. Annuae         ser.   No opinion
#  21  25558635   Poa annua var. tommasinii         var. Illegitimate
#  22  50062684     Poa [ unranked ] Annuae [ unranked ]   Legitimate
#  23  50062691     Poa [ unranked ] Annuae [ unranked ] Illegitimate
#  24  50062695            Poa sect. Annuae        sect.      Invalid
#  25  50063800     Poa annua subsp. exilis       subsp.   No opinion
#  26  50063801     Poa annua subsp. supina       subsp. Illegitimate
#  27  50077909      Poa annua subsp. varia       subsp.      Invalid
#  28  50077910    Poa annua unranked varia   [unranked]   No opinion
#  29  50119145    Poa annua var. eriolepis         var.   No opinion
#  30  50133141      Poa annua subsp. varia       subsp.   Legitimate
#  31  50154055       Poa annua var. supina         var.   No opinion
#  32  50155725   Poa annua var. raniglumis         var.   No opinion
#  33  50157106     Poa annua proles supina       proles   No opinion
#  34  50157109     Poa annua var. racemosa         var.   No opinion
#  35  50157110     Poa annua var. rigidula         var.   No opinion
#  36  50157407     Poa annua var. triflora         var.   No opinion
#  37  50158097    Poa annua subvar. minima      subvar.   No opinion
#  38  50158098       Poa annua var. minima         var.   No opinion
#  39  50182047       Poa annua var. supina         var.   Legitimate
#  40  50240461        Poa annua fo. maxima          fo.   No opinion
#  41  50243156     Poa annua fo. macarrima          fo.      Invalid
#  42  50267768   Poa annua fo. remotiflora          fo.   No opinion
#  43  50267769      Poa annua var. viridis         var.   No opinion
#  44  50267770       Poa annua fo. viridis          fo.   No opinion
#  45  50267771    Poa annua fo. lanuginosa          fo.   No opinion
#  46  50267772        Poa annua fo. ovalis          fo.   No opinion
#  47  50267774        Poa annua var. picta         var.   No opinion
#  48  50267776         Poa annua fo. picta          fo.   No opinion
#  49  50267778    Poa annua var. rivulorum         var.   No opinion
#  50  50267779   Poa annua fo. macranthera          fo.   No opinion
#  51  50278321   Poa annua var. pauciflora         var.   No opinion
#  52  50315599  Poa annua subsp. notabilis       subsp.   No opinion
#  53  50315610 Poa annua subsp. raniglunis       subsp.   No opinion
#  54  50315616      Poa annua fo. purpurea          fo.   No opinion
#  55 100386563      Poa annua var. arenosa         var.      Invalid
#  56 100386564     Poa annua var. alpigena         var.   No opinion
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
out <- get_ids(names=mynames, db = c('ncbi','itis','col','eol','tropicos'))
```

```
#       colid                 name    rank        status
#  1 18772549 Collomia grandiflora Species accepted name
#  2 18772550 Collomia grandiflora Species       synonym
#                                                                    source
#  1 World Plants: Synonymic Checklists of the Vascular Plants of the World
#  2 World Plants: Synonymic Checklists of the Vascular Plants of the World
#                acc_name
#  1                 <NA>
#  2 Collomia grandiflora
#       pageid    eolid
#  1    468106 50883433
#  2    468106 57237964
#  3  36073160 53417541
#  4    468106 43835813
#  5    468106 46180859
#  6    468106 52926497
#  7    468106 43835841
#  8    468106 43835826
#  9  39893972 57237966
#  10   468106 43835842
#  11 39893971 57237965
#  12   468106 43835840
#  13 39894037 57238031
#  14 39894038 57238032
#  15 39894049 57238043
#                                                             name source
#  1                                             Helianthus annuus   NCBI
#  2                                             Helianthus annuus   NCBI
#  3                      Helianthus annuus fasciation phytoplasma   NCBI
#  4                                          Helianthus annuus L.   GBIF
#  5                                          Helianthus annuus L.   ITIS
#  6                                          Helianthus annuus L.    COL
#  7  Helianthus annuus L. subsp. lenticularis (Douglas) Cockerell   GBIF
#  8           Helianthus annuus L. var. texanus (Heiser) Shinners   GBIF
#  9                               Helianthus annuus subsp. annuus   NCBI
#  10             Helianthus annuus subsp. jaegeri (Heiser) Heiser   GBIF
#  11                             Helianthus annuus subsp. texanus   NCBI
#  12                 Helianthus annuus var. macrocarpus Cockerell   GBIF
#  13                   Helianthus annuus x Helianthus argophyllus   NCBI
#  14        Helianthus annuus x Helianthus debilis subsp. debilis   NCBI
#  15                    Helianthus annuus x Helianthus petiolaris   NCBI
#       pageid    eolid                                                name
#  1   1061758 24954444                                      Pinus contorta
#  2   1061758 50827991                                      Pinus contorta
#  3   1061758 57311251                                      Pinus contorta
#  4   1061758 44398364                    Pinus contorta Douglas ex Loudon
#  5   1061758 46216292                    Pinus contorta Douglas ex Loudon
#  6   1061758 53084713                    Pinus contorta Douglas ex Loudon
#  7   1281916 57311252                      Pinus contorta subsp. contorta
#  8   1281916 50827992                      Pinus contorta subsp. contorta
#  9   2496751 50827993                       Pinus contorta var. bolanderi
#  10  2496751 57311253                       Pinus contorta var. bolanderi
#  11  2496751 46216294         Pinus contorta var. bolanderi (Parl.) Vasey
#  12  1281916 53084716                        Pinus contorta var. contorta
#  13  1281916 44398366      Pinus contorta var. contorta Douglas ex Loudon
#  14  1281916 46216293      Pinus contorta var. contorta Douglas ex Loudon
#  15  1281951 57311255                       Pinus contorta var. latifolia
#  16  1281951 44398367               Pinus contorta var. latifolia Engelm.
#  17  1281951 53084714               Pinus contorta var. latifolia Engelm.
#  18  1281951 46216295  Pinus contorta var. latifolia Engelm. ex S. Watson
#  19  1281913 57311254                       Pinus contorta var. murrayana
#  20  1281913 50827994                       Pinus contorta var. murrayana
#  21  1281913 44398365       Pinus contorta var. murrayana (Balf.) Engelm.
#  22  1281913 46216296       Pinus contorta var. murrayana (Balf.) Engelm.
#  23  1281913 53084715       Pinus contorta var. murrayana (Balf.) Engelm.
#  24 27055547 44398369          Pinus contorta var. yukonensis W.L. Strong
#  25  1281951 44398302 Pinus divaricata var. hendersonii (Lemmon) B.Boivin
#     source
#  1    IUCN
#  2    NCBI
#  3    NCBI
#  4    GBIF
#  5    ITIS
#  6     COL
#  7    NCBI
#  8    NCBI
#  9    NCBI
#  10   NCBI
#  11   ITIS
#  12    COL
#  13   GBIF
#  14   ITIS
#  15   NCBI
#  16   GBIF
#  17    COL
#  18   ITIS
#  19   NCBI
#  20   NCBI
#  21   GBIF
#  22   ITIS
#  23    COL
#  24   GBIF
#  25   GBIF
#    pageid    eolid                                   name source
#  1 580778 50873299                   Collomia grandiflora   NCBI
#  2 580778 57227458                   Collomia grandiflora   NCBI
#  3 580778 44178704  Collomia grandiflora Dougl. ex Lindl.   GBIF
#  4 580778 46170153 Collomia grandiflora Douglas ex Lindl.   ITIS
#  5 580778 52804720 Collomia grandiflora Douglas ex Lindl.    COL
#         tpsid                                  name   rank     status
#  1    2700851                     Helianthus annuus    sp. Legitimate
#  2    2700852   Helianthus annuus subsp. couplandii subsp. No opinion
#  3    2700853 Helianthus annuus subsp. lenticularis subsp. No opinion
#  4    2702619         Helianthus annuus var. annuus   var. No opinion
#  5    2702620    Helianthus annuus var. armavirskij   var. No opinion
#  6    2702621        Helianthus annuus var. bicolor   var. No opinion
#  7    2702622   Helianthus annuus var. californicus   var. No opinion
#  8    2702623 Helianthus annuus var. gallardiflorus   var. No opinion
#  9    2702624       Helianthus annuus var. globosus   var.    Invalid
#  10   2702625    Helianthus annuus var. intermedius   var. No opinion
#  11   2702626     Helianthus annuus var. primulinus   var. No opinion
#  12   2702627      Helianthus annuus var. uniflorus   var. No opinion
#  13   2702628  Helianthus annuus var. vinossissimus   var. No opinion
#  14   2702629        Helianthus annuus var. zonatus   var. No opinion
#  15   2724044    Helianthus annuus var. macrocarpus   var. No opinion
#  16   2724045      Helianthus annuus subsp. jaegeri subsp. No opinion
#  17   2724046       Helianthus annuus subsp. annuus subsp. No opinion
#  18   2724756          Helianthus annuus fo. fallax    fo. No opinion
#  19   2724757          Helianthus annuus fo. annuus    fo. No opinion
#  20   2726013      Helianthus annuus subsp. texanus subsp. No opinion
#  21  50069938      Helianthus annuus var. coronatus   var. No opinion
#  22  50069939         Helianthus annuus var. aridus   var. No opinion
#  23  50069940      Helianthus annuus var. latibasis   var. No opinion
#  24  50069941    Helianthus annuus fo. lenticularis    fo. No opinion
#  25  50071063   Helianthus annuus subsp. petiolaris subsp. No opinion
#  26  50071132   Helianthus annuus var. lenticularis   var. No opinion
#  27  50229527        Helianthus annuus var. texanus   var. No opinion
#  28  50289543       Helianthus annuus var. citrinus   var. No opinion
#  29 100000278        Helianthus annuus x petiolaris   var. No opinion
#         tpsid                                name       rank     status
#  1   24900183                      Pinus contorta        sp. No opinion
#  2   24900184       Pinus contorta var. bolanderi       var. No opinion
#  3   24900185       Pinus contorta var. latifolia       var. No opinion
#  4   24900186       Pinus contorta var. murrayana       var. No opinion
#  5   24900317     Pinus contorta subsp. murrayana     subsp. No opinion
#  6   24900318     Pinus contorta subsp. latifolia     subsp. No opinion
#  7   24900433     Pinus contorta var. hendersonii       var. No opinion
#  8   24900487 Pinus contorta unranked hendersonii [unranked] No opinion
#  9   24900528        Pinus contorta var. contorta       var. No opinion
#  10  24900627      Pinus contorta subsp. contorta     subsp. No opinion
#  11  24900810     Pinus contorta subsp. bolanderi     subsp. No opinion
#  12  24901682       Pinus contorta var. bolanderi       var. No opinion
#  13  50231950       Pinus contorta var. bolanderi       var. No opinion
#  14  50231960     Pinus contorta subsp. murrayana     subsp. No opinion
#  15 100351799             Pinus subsect. Contorta   subsect. No opinion
#  16 100363705      Pinus contorta var. yukonensis       var. No opinion
#         tpsid                                  name rank     status
#  1   25800485                  Collomia grandiflora  sp. No opinion
#  2   50130471   Collomia grandiflora var. axillaris var. No opinion
#  3   50130472 Collomia grandiflora var. grandiflora var. No opinion
#  4  100314137    Collomia grandiflora fo. axillaris  fo. No opinion
#  5  100314138   Collomia grandiflora fo. cryptantha  fo. No opinion
#  6  100314139      Collomia grandiflora fo. diffusa  fo. No opinion
#  7  100314140       Collomia grandiflora fo. scabra  fo. No opinion
#  8  100314141   Collomia grandiflora fo. tenuiflora  fo. No opinion
#  9  100314142     Collomia grandiflora var. diffusa var. No opinion
#  10 100314143  Collomia grandiflora var. tenuiflora var. No opinion
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
