## rnbn examples

### Load package


```r
library('rnbn')
```

### Login


```r
nbnLogin(getOption('nbnusername'), getOption('nbnkey'))
```

```
## [1] "Login successful"
```

### Search for taxon information using the query 'badger'


```r
dt <- getTVKQuery(query = "badger")
# Display two columns of the data 'ptaxonVersionKey' and 'name'
dt[, c("ptaxonVersionKey", "name")]
```

```
##   ptaxonVersionKey            name
## 1 NHMSYS0000080191          Badger
## 2 NBNSYS0000013055     Badger Flea
## 3 NHMSYS0000545919   a Badger flea
## 4 NHMSYS0000080191 Eurasian Badger
```

### Get some data for Wild cat with attributes

First I need the TVK for wild cat


```r
tvkQuery <- getTVKQuery(query = "wildcat")
```

Now, get the data with attributes


```r
WCresults <- getOccurrences(tvks = tvkQuery$ptaxonVersionKey, startYear = 1999,
                            endYear = 1999, attributes = TRUE, acceptTandC = TRUE)
```

```
## Requesting batch 1 of 1 
## Requesting data providers' information
```

```r
head(WCresults)
```

```
##   observationID fullVersion datasetKey        surveyKey
## 1     117160758       FALSE   GA000967 CI0000340000000A
## 2     117160770       FALSE   GA000967 CI00004200000007
## 3     117160780       FALSE   GA000967 CI0000420000001E
## 4     117160795       FALSE   GA000967 CI0000420000002W
## 5     117160830       FALSE   GA000967 CI000042000000FY
## 6     117160858       FALSE   GA000967 CI000042000000FY
##                 sampleKey   observationKey featureID location resolution
## 1 CI0000340000000A-SAMPLE CI00003400000406    212945   NN8867        1km
## 2 CI00004200000007-SAMPLE CI0000420000012E    570341   NJ5415        1km
## 3 CI0000420000001E-SAMPLE CI00004200000PYA    209165   NJ6619        1km
## 4 CI0000420000002W-SAMPLE CI000042000075DV    288393   NO6589        1km
## 5 CI000042000000FY-SAMPLE CI0000420000Q5UI    480249   NJ1422        1km
## 6 CI000042000000FY-SAMPLE CI0000420000Q5UJ    250670   NH9017        1km
##    taxonVersionKey pTaxonVersionKey       pTaxonName pTaxonAuthority
## 1 NBNSYS0000005134 NHMSYS0000332741 Felis silvestris  Schreber, 1777
## 2 NBNSYS0000005134 NHMSYS0000332741 Felis silvestris  Schreber, 1777
## 3 NBNSYS0000005134 NHMSYS0000332741 Felis silvestris  Schreber, 1777
## 4 NBNSYS0000171863 NHMSYS0000332741 Felis silvestris  Schreber, 1777
## 5 NHMSYS0000332741 NHMSYS0000332741 Felis silvestris  Schreber, 1777
## 6 NHMSYS0000332741 NHMSYS0000332741 Felis silvestris  Schreber, 1777
##    startDate    endDate sensitive absence publicAttribute dateTypekey
## 1 1999-01-01 1999-12-31     FALSE   FALSE           FALSE          Y 
## 2 1999-02-25 1999-02-25     FALSE   FALSE           FALSE          D 
## 3 1994-01-01 2000-12-31     FALSE   FALSE           FALSE          YY
## 4 1999-06-01 1999-08-31     FALSE   FALSE           FALSE          OO
## 5 1999-06-26 1999-06-26     FALSE   FALSE           FALSE          D 
## 6 1999-08-11 1999-08-11     FALSE   FALSE           FALSE          D 
##                      siteKey     siteName recorder determiner
## 1                       <NA>         <NA>     <NA>       <NA>
## 2                       <NA>         <NA>     <NA>       <NA>
## 3                       <NA>         <NA>     <NA>       <NA>
## 4                       <NA>         <NA>     <NA>       <NA>
## 5                       <NA>         <NA>     <NA>       <NA>
## 6 NBN-SITE-GA000967-14940707 Laggantygown     <NA>       <NA>
##   attributes.Abundance attributes.Comment attributes.SampleMethod latitude
## 1                 <NA>               <NA>                    <NA>    56.79
## 2                 <NA>               <NA>                    <NA>    57.23
## 3                 <NA>               <NA>                    <NA>    57.26
## 4                 <NA>               <NA>                    <NA>    57.00
## 5                 <NA>               <NA>                    <NA>    57.29
## 6                 <NA>               <NA>                    <NA>    57.24
##   longitude
## 1    -3.827
## 2    -2.755
## 3    -2.557
## 4    -2.569
## 5    -3.420
## 6    -3.816
```

### Get contact information for datasets


```r
dataProviders(c("GA000426", "GA000832"))
```

```
##   id                                          name
## 1  4                     Biological Records Centre
## 2 34 Bristol Regional Environmental Records Centre
## 3 19                        Butterfly Conservation
##                                                                              address
## 1 Biological Records CentreCEH Wallingford,Crowmarsh Gifford,Wallingford,Oxfordshire
## 2                BRERC\nThird Floor\nBristol Central Library\nCollege Green\nBristol
## 3                                         Manor Yard, East Lulworth, Wareham, Dorset
##     postcode                contactName                    contactEmail
## 1 OX10 8BB                 Dr David Roy                   brc@ceh.ac.uk
## 2 BS1 5TL    BRERC Manager - Tim Corner               info@brerc.org.uk
## 3 BH20 5QP                  Richard Fox rfox@butterfly-conservation.org
##                          website
## 1                  www.brc.ac.uk
## 2               www.brerc.org.uk
## 3 www.butterfly-conservation.org
```

