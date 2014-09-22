# Rstudio server

The RStudio you used for the workshop today is available as a public Amazon Machine Image (AMI). The machine ID is:

```coffee
ami-81b8f7e8
```

This means that you can use your own [personal Amazon account](https://console.aws.amazon.com/console/home) to launch an instance of this machine image at your convenience. We'll keep all the stable versions of rOpenSci packages and tools updated at all times. 

You will most likely just want to work locally on your copy of RStudio. In that case, you'll need the latest version of R (currently `3.0.1`) and [RStudio](http://www.rstudio.com/) for your platform. Then install the following packages:

```coffee
# First install the devtools package since it will allow you to install packages directly from GitHub that haven't yet been submitted to CRAN.

install.packages("devtools")
library(devtools)
```

Next install:

```coffee
install.packages("ggplot2", dependencies = TRUE)
install.packages(c("taxize","rgbif","rbison","rWBclimate","rebird","knitr","maptools","dismo","scales","doMC","plyr","vegan","shiny"))
```

# from GitHub

```coffee
install_github(c("ropensci/spocc","ropensci/rnpn","ropensci/rinat","ropensci/rnoaa","ramnathv/rCharts"))
```

I may have missed a few dependencies. If so, apologies in advance. 