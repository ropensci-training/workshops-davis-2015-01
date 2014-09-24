---
title       : ropensci ~ taxize
subtitle    : all things taxonomic names
author      : 
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
assets:
  css: "http://netdna.bootstrapcdn.com/font-awesome/4.2.0/css/font-awesome.css"
---

## Large package - two organizing principles

- Data sources
  - Lots of data sources, currently 20
- Verbs (ish)
  - `classification()`
  - `children()`
  - `downstream()`
  - `comm2sci()`, `sci2comm()`
  - `resolve()`
  - `synonyms()`

---

## Why?

<br>
> # A single easy to use user interface to many data sources can simplify science, and make it more reproducible

---

## Why...more

* Many biologists deal with names at some point in their research = taxonomy is fundamental data
* Integrations: After names are cleaned, integrate with other parts of research workflow
  * taxonomy -> biodiversity data
  * taxonomy -> phylogenetics
  * taxonomy -> molecular work

---

<br><br><br>
## Let's try it
