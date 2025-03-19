Data Importing & Cleaning
================

# Data Import

Data is stored in OneDrive, importing those data files into R to begin
data processing and cleaning.

# Cleaning time_to_diabetes datafile

- Observations: 6814  
- Variables kept-
  - idno: Participant ID number  
  - dmage: Age at Diabetes diagnosis
- Total number of missing values for **dmage**: 4917
  - *What are we doing with missing values*: Missing values will be left
    as ‘NA’ because the regression models that will be ran into this
    project can handel the ‘NA’ automatically or I can explciitly state
    to omit those values.

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
time_to_diabetes = select(time_to_diabetes, idno, dmage)
sum(is.na(time_to_diabetes$dmage))
```

    ## [1] 4917

# Cleaning MESA_E1 datafile

# Cleaning MESA_E5 datafile
