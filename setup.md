# Setup {.unnumbered}  

## Installing and Using Required Packages {.unnumbered}  
Throughout this tutorial, we’ll use a few essential R packages to manipulate data, run models, and create plots.   
Below are the core packages, what they do, and how to install them.  

Packages we’ll use:  

**ggplot2** – For plotting (e.g., scatterplots, regression lines)    
**dplyr** – For data wrangling (filtering, mutating, summarizing, etc.)     
**gridExtra** – To combine multiple plots into one figure    
**stats** – Comes with base R and used for regression (lm())    
**pacman** – Simplifies package management in R
**broom (optional)** – Makes model summaries easier to work with    


``` r
# install.packages(c("ggplot2", "dplyr", "gridExtra", "pacman", "broom"))
```

## Loading Packages {.unnumbered}  


``` r
library(ggplot2)
library(dplyr)
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

``` r
library(gridExtra)
```

```
## 
## Attaching package: 'gridExtra'
```

```
## The following object is masked from 'package:dplyr':
## 
##     combine
```

``` r
# Optional if using tidy model outputs:
# library(broom)
```

## Difference Between install.packages() and library() {.unnumbered}

- install.packages("dplyr") downloads and installs the package — you only need to do this once per computer.  
- library(dplyr) loads the package into your R session — you need to run this each time you use it.  

## Session Information {.unnumbered}

It's always good practice to include your session info at the end of your analysis. This gives a snapshot of:  

- Your R version and system details  
- All the packages that were loaded  
- The versions of those packages  

This is especially useful when:  
- You're debugging errors  
- You're submitting assignments  
- You're collaborating with others  

## Why include this? {.unnumbered}

Sometimes code behaves differently depending on the version of a package or even the version of R itself. Including your session info makes your work **reproducible and easier to troubleshoot**.

## Base R version (simple) {.unnumbered}

This function comes with R and gives you basic session details.


``` r
sessionInfo()
```

```
## R version 4.5.1 (2025-06-13 ucrt)
## Platform: x86_64-w64-mingw32/x64
## Running under: Windows 11 x64 (build 26100)
## 
## Matrix products: default
##   LAPACK version 3.12.1
## 
## locale:
## [1] LC_COLLATE=English_United States.utf8 
## [2] LC_CTYPE=English_United States.utf8   
## [3] LC_MONETARY=English_United States.utf8
## [4] LC_NUMERIC=C                          
## [5] LC_TIME=English_United States.utf8    
## 
## time zone: America/New_York
## tzcode source: internal
## 
## attached base packages:
## [1] stats     graphics  grDevices utils     datasets  methods   base     
## 
## other attached packages:
## [1] gridExtra_2.3 dplyr_1.1.4   ggplot2_3.5.2
## 
## loaded via a namespace (and not attached):
##  [1] vctrs_0.6.5        cli_3.6.5          knitr_1.50         rlang_1.1.6       
##  [5] xfun_0.52          generics_0.1.4     jsonlite_2.0.0     glue_1.8.0        
##  [9] htmltools_0.5.8.1  sass_0.4.10        scales_1.4.0       rmarkdown_2.29    
## [13] grid_4.5.1         evaluate_1.0.4     jquerylib_0.1.4    tibble_3.3.0      
## [17] fastmap_1.2.0      yaml_2.3.10        lifecycle_1.0.4    bookdown_0.43     
## [21] compiler_4.5.1     RColorBrewer_1.1-3 pkgconfig_2.0.3    farver_2.1.2      
## [25] digest_0.6.37      R6_2.6.1           tidyselect_1.2.1   pillar_1.11.0     
## [29] magrittr_2.0.3     bslib_0.9.0        withr_3.0.2        tools_4.5.1       
## [33] gtable_0.3.6       cachem_1.1.0
```
