Table 1
================

``` r
MESA_final <- readRDS("MESA_final.rds")
```

### Tabulation

#### Gender

0: female  
1: Male

``` r
table(MESA_final$gender1)
```

    ## 
    ##   0   1 
    ## 521 463

``` r
prop.table(table(MESA_final$gender1))
```

    ## 
    ##         0         1 
    ## 0.5294715 0.4705285

#### Nativity

1: One of 50 US states  
2: Puerto Rico  
3: Another country

``` r
table(MESA_final$bth1)
```

    ## 
    ##   1   2   3 
    ## 339 110 535

``` r
prop.table(table(MESA_final$bth1))
```

    ## 
    ##         1         2         3 
    ## 0.3445122 0.1117886 0.5436992

#### Nationality

Mexican, Chicano, Mexican-American  
0: No  
1: Yes

``` r
table(MESA_final$mexican1)
```

    ## 
    ##   0   1 
    ## 477 505

``` r
prop.table(table(MESA_final$mexican1))
```

    ## 
    ##         0         1 
    ## 0.4857434 0.5142566

Dominican  
0: N  
1: Y

``` r
table(MESA_final$dominic1)
```

    ## 
    ##   0   1 
    ## 843 139

``` r
prop.table(table(MESA_final$dominic1))
```

    ## 
    ##         0         1 
    ## 0.8584521 0.1415479

Puerto Rican  
0: No  
1: yes

``` r
table(MESA_final$puert1)
```

    ## 
    ##   0   1 
    ## 841 141

``` r
prop.table(table(MESA_final$puert1))
```

    ## 
    ##         0         1 
    ## 0.8564155 0.1435845

Cuban  
0: No  
1: Yes

``` r
table(MESA_final$cuban1)
```

    ## 
    ##   0   1 
    ## 946  36

``` r
prop.table(table(MESA_final$cuban1))
```

    ## 
    ##          0          1 
    ## 0.96334012 0.03665988

Other Hispanic  
0: No  
1: Yes

``` r
table(MESA_final$othhisp1)
```

    ## 
    ##   0   1 
    ## 848 134

``` r
prop.table(table(MESA_final$othhisp1))
```

    ## 
    ##         0         1 
    ## 0.8635438 0.1364562

#### Preferred Language

*Using “Language spoken at Exam 1*  
1:English  
2: Spanish  
3: Chinese

``` r
table(MESA_final$lang1)
```

    ## 
    ##   1   2 
    ## 498 486

``` r
prop.table(table(MESA_final$lang1))
```

    ## 
    ##         1         2 
    ## 0.5060976 0.4939024

*Using “Language spoken at home*  
1: ENGLISH  
2: SPANISH  
3: CANTONESE  
4: MANDARIN  
5: OTHER

``` r
table(MESA_final$langhm1)
```

    ## 
    ##   1   2   5 
    ## 118 214   1

``` r
prop.table(table(MESA_final$langhm1))
```

    ## 
    ##           1           2           5 
    ## 0.354354354 0.642642643 0.003003003

*Question* Should we create another variable using “Language spoken at
Exam 1” and “Language spoken at home”?

#### Geographic Location

3: WFU = Winston-Salem, NC  
4: COL = New York, NY  
5: JHU = Baltimore, MD  
6: UMN = Minneapolis, MN  
7: NWU = Chicago, IL  
8: UCLA = Los Angeles, CA

``` r
table(MESA_final$site1c)
```

    ## < table of extent 0 >

``` r
prop.table(table(MESA_final$site1c))
```

    ## numeric(0)

#### Cigarette Smoking Status

0: Never  
1: Former  
2: Current

``` r
table(MESA_final$cig1c)
```

    ## < table of extent 0 >

``` r
prop.table(table(MESA_final$cig1c))
```

    ## numeric(0)

#### Hypertension

0: No  
1: Yes  
9: Do not know

``` r
table(MESA_final$highbp1)
```

    ## < table of extent 0 >

``` r
prop.table(table(MESA_final$highbp1))
```

    ## numeric(0)

#### Diabetes at Exam

“Exam 1 Diabetes Mellitus by 2003 ADA Fasting Criteria Algorithm”  
0: Normal  
1: IFG (“impaired fasting glucose”)  
2: Untreated Diabetes  
3: Treated Diabetes

``` r
table(MESA_final$dm031c)
```

    ## < table of extent 0 >

``` r
prop.table(table(MESA_final$dm031c))
```

    ## numeric(0)

*Question*: Should I create new variable combining Normal and IFG as “no
diabetes” and untrested diabetes and treated diabetes as “diabetes”?

### Mean & SDs

Age BMI Average intentional exercises, minutes per week Average age of
diabetes diagnosis, yrs Average LDL cholesterol Average HDL cholesterol
Average cognitive assessment score-CASI
