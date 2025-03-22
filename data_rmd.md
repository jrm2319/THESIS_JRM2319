Data Importing & Cleaning
================

## Data Import

Data is stored in OneDrive, importing those data files into R to begin
data processing and cleaning.

## Cleaning time_to_diabetes datafile

- **Observations**: 6814  
- **Variables kept:** 2
  <details>

  - idno: Participant ID number  
  - dmage: Age at Diabetes diagnosis

  </details>
- **Missing values**

``` r
colSums(is.na(time_to_diabetes))
```

    ##  idno dmage 
    ##     0  4917

    - *What are we doing with missing values*: Missing values will be left as 'NA' because the regression models that will be ran into this project can handle the 'NA' automatically or I can explicitly state to omit those values. However, this variable has a lot of missing data with a complete rate of about 27.8%. We may or may not need this variable--I am assuming that most of the diabetes data will come from the E1 or E5 files. At least for the 'ever having diabetes' variables will come from the E1 and E3 files, *not* this file, as previously thought. 

## Cleaning MESA_E5 datafile

- **Time frame for data file**: April 2010-Feb 2012
- **Observations**: 4716
- **Variables Kept:** 31
  <details>

  - idno: Participant ID number
  - ecomp5c: Exam 5 Completion Status
  - age1c: age at Exam 1
  - agecat1c: age categories at Exam 1
  - age5c: Age at Exam 5
  - agecat5c: age categories at Exam 5
  - race1c: race/ethnicity
  - mexican1: Mexican, Chicano, Mexican-American
  - dominic1: Dominican
  - puert1: Puerto Rican
  - cuban1: Cuban
  - othhisp1: Other Hispanic
  - lang1: Language spoken at Exam 1
  - gender1: Gender
  - site5c: Site at Exam 5
  - bmi5c: BMI
  - cig5c: Cigarette smoking status
  - dbp5c: Seated diastolic blood pressure
  - sbp5c: seated systolic blood pressure
  - glucose5: Fasting glucose (mg/dl)
  - dm035c: Diabetes 2003 ADA Fasting Criteria
  - ldl5: LDL cholesterol
  - ldlcat5c: LDL cholesterol (categorical)
  - hdl5: HDL Cholesterol
  - hdlcat5c: HDL cholesterol (categorical)
  - chol5: Total cholesterol
  - htn5c: Hypertension by JNC VI (1997) Creteria
  - income5: total gross family income, past 12 months
  - exercm5c: Total intentional exercises- Min/Week
  - casisum5c: Total cognitive assessment score
  - numhhld5: \# of people supported by family income

  </details>
- **Missing Values:**

``` r
colSums(is.na(MESA_E5))
```

    ##      idno   ecomp5c     age1c  agecat1c     age5c  agecat5c    race1c  mexican1 
    ##         0         0         0         0         0         0         0         9 
    ##  dominic1    puert1    cuban1  othhisp1     lang1   gender1    site5c     bmi5c 
    ##         9         9         9         9         0         0         0        74 
    ##     cig5c     dbp5c     sbp5c  glucose5    dm035c      ldl5  ldlcat5c      hdl5 
    ##         0        63        63       129       121       157       157       135 
    ##  hdlcat5c     chol5     htn5c   income5  exercm5c casisum5c  numhhld5 
    ##       135       134        63       213        78       125       109

At this point, I’ll only be removing participants who are not
Hispanic/Latino (from race1c) and those who are missing values for the
CASI assessment at Exam 5. Participants with missing values for
exposures of interests will be potentially removed after merging Exam 1
and Exam 5.

The reasoning for this is because variables across both Exam 1 and Exam
5 will be used in the creation of the acculturation score and the ‘ever
having diabetes’ variables, therefore the full extent to missing-ness
cannot be assessed until I get to that merged dataset.

``` r
MESA_E5 = MESA_E5 %>% 
          filter(race1c == 4,
                 casisum5c != 'NA')
```

There are 999 Hispanic/Latino’s in the sample, of these 15 have a
missing CASI Score in Exam 5–we will exclude these participants. **Our
final sample for Exam 5 is 984, with 31 variables.**

``` r
library(dplyr)
glimpse(MESA_E5)
```

    ## Rows: 984
    ## Columns: 31
    ## $ idno      <dbl> 3015556, 3015700, 4010019, 4010051, 4010078, 4010108, 401011…
    ## $ ecomp5c   <dbl> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, …
    ## $ age1c     <dbl> 60, 47, 82, 65, 76, 65, 61, 53, 73, 47, 77, 48, 52, 80, 52, …
    ## $ agecat1c  <dbl> 2, 1, 4, 3, 4, 3, 2, 1, 3, 1, 4, 1, 1, 4, 1, 3, 1, 1, 1, 1, …
    ## $ age5c     <dbl> 69, 57, 92, 74, 85, 75, 70, 62, 83, 57, 86, 58, 62, 89, 61, …
    ## $ agecat5c  <dbl> 3, 2, 5, 3, 5, 4, 3, 2, 4, 2, 5, 2, 2, 5, 2, 3, 2, 2, 3, 2, …
    ## $ race1c    <dbl> 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, …
    ## $ mexican1  <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, …
    ## $ dominic1  <dbl> 0, 0, 0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, …
    ## $ puert1    <dbl> 0, 1, 0, 1, 1, 1, 1, 0, 0, 1, 0, 0, 1, 0, 0, 0, 1, 1, 1, 1, …
    ## $ cuban1    <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 1, 0, 0, 0, 0, 0, 1, …
    ## $ othhisp1  <dbl> 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, …
    ## $ lang1     <dbl> 1, 1, 1, 2, 2, 2, 2, 2, 2, 1, 1, 2, 2, 2, 2, 1, 1, 1, 2, 1, …
    ## $ gender1   <dbl> 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, …
    ## $ site5c    <dbl> 3, 3, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, …
    ## $ bmi5c     <dbl> 28.06424, 20.95642, 29.71071, 28.31443, 26.87518, 36.59724, …
    ## $ cig5c     <dbl> 0, 2, 0, 2, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 1, 1, 0, 0, …
    ## $ dbp5c     <dbl> 84.0, 59.0, 76.5, 64.5, 79.0, 61.0, 70.0, 68.5, 65.5, 74.0, …
    ## $ sbp5c     <dbl> 137.5, 100.5, 148.0, 129.5, 131.5, 119.5, 117.0, 163.5, 135.…
    ## $ glucose5  <dbl> 95, 83, 106, 178, NA, 94, 98, 210, 152, 95, 106, 85, 101, 87…
    ## $ dm035c    <dbl> 0, 0, 1, 3, NA, 0, 0, 3, 3, 0, 1, 0, 1, 0, 0, 0, 0, 3, 1, 0,…
    ## $ ldl5      <dbl> 79, 118, 72, 110, NA, 115, 95, 182, 106, 121, 66, 118, 131, …
    ## $ ldlcat5c  <dbl> 1, 2, 1, 2, NA, 2, 1, 4, 2, 2, 1, 2, 3, 1, 2, 1, 2, 1, 2, 2,…
    ## $ hdl5      <dbl> 42, 71, 53, 35, NA, 58, 46, 41, 48, 68, 52, 90, 63, 67, 61, …
    ## $ hdlcat5c  <dbl> 2, 1, 2, 3, NA, 2, 2, 2, 2, 1, 2, 1, 1, 1, 1, 1, 1, 2, 2, 1,…
    ## $ chol5     <dbl> 148, 199, 137, 171, NA, 192, 151, 256, 164, 199, 131, 224, 2…
    ## $ htn5c     <dbl> 1, 0, 1, 0, 0, 1, 0, 1, 1, 0, 1, 0, 0, 1, 0, 0, 1, 0, 0, 1, …
    ## $ income5   <dbl> 9, NA, 10, 10, 3, 6, 1, 9, 4, 11, 4, 7, 5, 3, 10, 9, 8, 11, …
    ## $ exercm5c  <dbl> 2217.5, 2625.0, 45.0, 105.0, 5040.0, 540.0, 542.5, 1380.0, 3…
    ## $ casisum5c <dbl> 94.0, 89.0, 67.8, 75.0, 61.2, 65.4, 87.5, 85.0, 80.0, 90.9, …
    ## $ numhhld5  <dbl> 1, 2, 2, 5, 1, 1, 2, 1, 2, 1, 1, 3, 1, 2, 4, 1, 2, 5, 2, 2, …

*To consider:* For the Exam 5 Completion Status (ecomp5c), should I only
include 1 = complete? or also include 2 = partially complete (home
admin) or 3 = partially complete (phone admin)? N’s are below:

    ## 
    ##   1   2 
    ## 971  13

# Cleaning MESA_E1 datafile

- Observations: 6814
- Variables kept-
  - Idno: Participant ID number
  - bth1: Birth Place-Self
  - ctrybth1: Birth country
  - langhm1: Language Spoken at home
  - educ1: education: highest level completed
  - yrsalc1c: \# of years drinking alcohol (current and former drinkers)
  - alcwk1c: \# of drinks per week (current and former drinkers)
  - nviolen1: Violence Problem in Neighborhood
  - nlfshop1: Lack of adequate food shopping in neighborhood
  - nnoise1: Excessive noise in neighborhood
  - nvalues1: People in neighborhood do not share the same values
  - nclose1: Close-knit neighborhood
  - Nhdtim1c or nhdyrs1: \# of years in the neighborhood
  - ncohes1c: Neighborhood social cohesion score
  - nprob1c: Neighborhood problems score
- Total missing variables for
