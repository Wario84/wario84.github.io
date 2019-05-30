---
title: "Stan Multilevel Model Ability"
output: github_document
---


## GitHub Documents

This is an R Markdown format used for publishing markdown documents to GitHub. When you click the **Knit** button all R code chunks are run and a markdown file (.md) suitable for publishing to GitHub is generated.
Equation Test $y^2=f(x)$


## Including Code

You can include R code in the document as follows:

```{stan cars}
  data {
    ##########
    # INDICES
    
    # indices - pre-selection
    int<lower=1> M; # nb. of master universities [MG – minimum value of 1]
    int<lower=1> Q; # nb. of factors related to innate quality after master [MG – minimum value of 1]
    
    # indices - selection equation 
    int<lower=1> N; # number of students
    int<lower=1> P; # number of phd universities
    int<lower=1> L; # nb. of factors affecting Phd university selection
    
    # indices - rating equation
    int<lower=0> NT; # number of observations with T_i varying - JR nb of observations-years for student 1 + nb of observations-years for student 2 + ...
    int<lower=0> K; # nb. of factors affecting rating
    int<lower=0> C; # nb. of levels in ordered rating
    
    # periods after phd 
    int<lower=0> nbPeriods;
    
    # DATA
    # data pre-selection
    matrix[N,Q] V; # ability related factors [MG no of students * no of factors affecting innate ability]
    
    # data - selection
    matrix[N,P] Z1; # alt.-varying factor
    matrix[N,L] Z2; # indiv.-varying factor 
    int<lower=1> D_int[N]; # indicator vector of phd uni
    
    # concordance - rating (NT) to individual (N)
    int<lower=1,upper=NT> id[NT]; # connects NT with N, i.e. id[NT]=N
    
    # data - rating
    matrix[NT,K] X; # K factors affecting rating
    int<lower=0> R[NT]; # ordered rating outcome
    
  }
  

```
