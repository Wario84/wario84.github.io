---
title: "Stan Multilevel Model Ability"
output: github_document
---


## The model
The model explains academic performance as a function of PhD training. We distinguish domestic and foreign PhD training, Each group has universities clustered by prestige. 


The model has three layers or clusters, 


## Stan Data Chunk

We define the following sets.
$n \in N$ is a set of researchers (individuals)
$m \in M$ is a set of master universities such that $n:m$, If a researcher $n$ graduated from university $m$.
$q \in Q$ is a set of factors factors related to innate ability.
$p \in P$ is a set of Phd. Universities$.
$l \in L$ is a set of factors affecting university selection.


```
  data {
    ##########
    # INDICES
    
    # indices - pre-selection
    int<lower=1> M; / nb. of master universities [MG – minimum value of 1]
    int<lower=1> Q; / nb. of factors related to innate quality after master [MG – minimum value of 1]
    
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
