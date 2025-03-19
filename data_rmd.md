Data Importing & Cleaning
================

## Data Import

Data is stored in OneDrive, importing those data files into R to begin
data processing and cleaning.

## Cleaning time_to_diabetes datafile

- Observations: 6814  
- Variables kept-
  - idno: Participant ID number  
  - dmage: Age at Diabetes diagnosis

``` r
time_to_diabetes = select(time_to_diabetes, idno, dmage)
skimr::skim(time_to_diabetes$dmage)
```

|                                                  |                         |
|:-------------------------------------------------|:------------------------|
| Name                                             | time_to_diabetes\$dmage |
| Number of rows                                   | 6814                    |
| Number of columns                                | 1                       |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |                         |
| Column type frequency:                           |                         |
| numeric                                          | 1                       |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |                         |
| Group variables                                  | None                    |

Data summary

**Variable type: numeric**

| skim_variable | n_missing | complete_rate | mean |    sd |  p0 | p25 | p50 | p75 | p100 | hist  |
|:--------------|----------:|--------------:|-----:|------:|----:|----:|----:|----:|-----:|:------|
| data          |      4917 |          0.28 | 63.5 | 11.67 |  12 |  56 |  64 |  72 |   94 | ▁▁▆▇▂ |

- Total number of missing values for **dmage**: 4917
  - *What are we doing with missing values*: Missing values will be left
    as ‘NA’ because the regression models that will be ran into this
    project can handel the ‘NA’ automatically or I can explciitly state
    to omit those values.
- Mean for variables:
  - dmage: Average age of diabetes diagnosis among study participants is
    63.50, with a SD of 11.67.
- **Note**: This variable has a lot of missing data with a complete rate
  of about 27.8%. We may or may not need this variable–I am assuming
  that most of the diabetes data will come from the E1 or E5 files. At
  least for the ‘ever having daiabetes’ variables will come from the E1
  and E3 files, *not* this file, as previously thought.

## Cleaning MESA_E5 datafile

- Time frame for data file: April 2010-Feb 2012
- Observations:
- Variables Kept-
  - Idno: Participant ID number
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
- Total missing:
  - (per variable)
- Means/SD
  - (per variable)
- To consider: for the Exam 5 Completion Status (ecomp5c), should I only
  include 1 = complete? or also include 2 = partially complete (home
  admin) or 3 = partially complete (phone admin)?

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
