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

# Cleaning MESA_E5 datafile (Clean this first because this is the data we’ll primalry using, from E1 we only need diabetes info to make the ‘ever having diabetes’ variable)

# Cleaning MESA_E1 datafile

- Observations: 6814
- Variables kept-
  - Idno: Participant ID number
  - age: age
  - age1c: age categories
  - race1c: race/ethnicity
  - mexican1: Mexican, Chicano, Mexican-American
  - dominic1: Dominican
  - puert1: Puerto Rican
  - cuban1: Cuban
  - othhisp1: Other Hispanic
  - lang1: Language spoken at Exam 1
  - gender1: Gender
  - site1c: Site
  - bmi1c: BMI
  - cig1c: Cigarette smoking status
  - dbp1c: Seated diastolic blood pressure
  - sbp1c: seated systolic blood pressure
  - glucos1c: Fasting glucose calibrated
  - glucos1u: Fasting glucose originial
  - dm031c: Exam 1 Diabetes Mellitus by 2003 ADA Fasting Criteria
    Algorithm
  - ldl1: LDL cholesterol
  - ldlcat1c: LDL cholesterol (categorical)
  - hdl1: HDL Cholesterol
  - hdlcat1c: HDL cholesterol (categorical)
  - chol1: Total cholesterol
  - highbp1: Hypertension
  - diabet1: Diabetes Self-Reported
  - bth1: Birth Place-Self
  - ctrybth1: Birth country
  - langhm1: Language Spoken at home
  - educ1: education: highest level completed
  - income1: total gross family income, past 12 months
  - yrsalc1c: \# of years drinking alcohol (current and former drinkers)
  - alcwk1c: \# of drinks per week (current and former drinkers)
  - exercm1c: Total intentional exercises- Min/Week
  - casisum6c: Total cognitive assessment score
  - valid6: Validity of score (for the CASI score)
  - nviolen1: Violence Problem in Neighborhood
  - nlfshop1: Lack of adequate food shopping in neighborhood
  - nnoise1: Excessive noise in neighborhood
  - nvalues1: People in neighborhood do not share the same values
  - nclose1: Close-knit neighborhood
  - Nhdtim1c or nhdyrs1: \# of years in the neighborhood
  - ncohes1c: Neighborhood social cohesion score
  - nprob1c: Neighborhood problems score
  - numhhld1: \# of people supported by family income
- Total missing variables for
