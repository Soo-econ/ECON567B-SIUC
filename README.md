# ECON567B-SIUC, Fall 2025

**Stata Session** using datasets from __Jeffrey M. Wooldridge__'s <i>``Econometric Analysis of Cross Section and Panel Data.''</i>
>  Instructor: **Soo Jeong Lee** (soojeong.lee@siu.edu)
> 
> _School of Analytics, Finance and Economics @ Southern Ililinois University Carbondale_


# First Stata Session
In this session, we will cover __Problem Sets 8.15., 10.11.__ and __10.12. (RE/FE/FD estimators)__ from our textbook:

> **Wooldridge, J. M. (2002), <i>``Econometric analysis of cross section and panel data,''</i> MIT press. Cambridge, ma, 108(2), 245-254.**
> 
> **Chapters from Textbook and Corresponding Class Notes:**
> - **Chapter 8.** *System Estimation by Instrumental Variables* — *(Lecture Note 5)*  
> - **Chapter 10.** *Basic Linear Unobserved Effects Panel Data Models* — *(Lecture Note 6)*
>

All related codes will be discussed in class, but this page serves as the starting point for the session.

We will walk through how to download __the Wooldridge datasets__ and apply them to selected exercises.

<br>

**After the session update:**
> **NOTE:** The course assignment is due **Monday, November 17, 2025.**
> 1. Problem Set 10.11 (a) & (b)
> 2. Problem Set 10.12 (a) through (f)
>
> Please read each question thoroughly and submit your answers, results, and code file on D2L.
I’ve included some code hints below that may be helpful as you work through the problems!

<br>

## [1] Downlowd Datasets
Run the following commands in Stata to access wooldridge's datasets:
```
net from http://www.stata.com/data/jwooldridge/
```
and
```
net describe eacsap
```
It will display all available dataset in the `eacsap` package. 

To download all datasets, run:
```
net get eacsap, replace
```

## [2] Problem Set 8.15.
We will use the dataset `AIRFARE.DTA` to solve problem set 8.15.
```
use airfare, replace
```
To review available variables and their types, run:
```
describe
```
### 8.15. (a) Pooled OLS
```
reg lpass y98 y99 y00 lfare ldist ldistsq
```


**.... All other codes will be available during the session.**



<br>

## [3] Problem Set 10.12.
We will use the dataset `WAGEPAN.DTA` to solve problem set 10.12.

```
use wagepan, replace
discribe
```

```
xtset nr year
```
```
reg lwage i.year educ black hisp exper expersq married union
```
```
reg lwage i.year educ black hisp exper expersq married union, cluster(nr)
```
>**Hint: ...  fully robust standard error ..** `cluster(nr)` vs. `vce(robust)`
>
> robust to both heteroskedasticity and serial correlation

## 10.12-(b) Random Effect 
```
xtreg lwage i.year educ black hisp exper expersq married union, re
```
## 10.12-(c) Fixed Effects 
```
xtreg lwage i.year educ black hisp exper expersq married union, fe
```
## 10.12-(d) 
> `c.educ##i.year` includes main effects and their interactions; equivalent to writing  `i.year educ c.educ#i.year`
> 
> `c.educ#i.year` includes only the interation terms.
```
xtreg lwage c.educ##i.year expersq married union i.year, fe
```

## 10.12-(e) FE assumption: strict exogeneity
> After setting the panel structure using the `xtset` command, you can easily create lagged and lead variables using the prefixes `L.` and `F.`, respectively.
>
> For example:
- To include $y_{t-1}$ (the one-period lag of $y$) as a regressor, use:
```stata
L1.y
```
- To include $y_{t+1}$ (the one-period lead of $y$), use:
```
F1.y
```
Similary, $y_{t+2}$ would be `F2.y`. `L'i'.` or  `F'i'.` indicates the $i$-th lag or $i$-th lead of the variable. 
  

<br>






