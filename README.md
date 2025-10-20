# ECON567B-Southern Ililinois University Carbondale

Instructor: Soo Jeong Lee

**Stata Session** using datasets from __Jeffrey M. Wooldridge__'s <i>``Econometric Analysis of Cross Section and Panel Data.''</i>


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

>**NOTE:** Problem Set 10.11 is the course assignment, due November 10, 2025.

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

hint
```
,vce(cluster id)
,vce(robust)
```
**.... All other codes will be available during the session.**



<br>

## [3] Problem Set 10.12.
We will use the dataset `WAGEPAN.DTA` to solve problem set 10.12.

```
use wagepan, replace
discribe
```

**.... All other codes will be available during the session.**




<br>






