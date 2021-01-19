---
title: "Multinomial logistic regression using R: Bayesian and Frequentist models."
output: github_document
---

## Introduction.

Multinomial models are suitable to estimate the probability of $$i$$ *units* falling into $$K$$ categories. These $$K$$ do not have an order, but rather are options or *choices*. For instance, an ice cream flavor, an occupational choice or university selection. All $$K>2$$ categories are the outcome of a variable  $$y_n^*$$. The multinomial logistic model is an extension of the binary logistic model, you can revise the derivation from [Wikipedia](https://en.wikipedia.org/wiki/Multinomial_logistic_regression). The basic idea is that each pair of $$K$$ categories is an output of a binary logistic model. One of the $$K$$ categories serves a *pivot* for each $$K-1$$ system of equations.

Given that we have $K-1$ equations, Each $j$ explanatory variable in $X_{ij}$ has an $\beta_{k-1}$  unknown parameters to estimate if we include the intercept. For instance, for a model with $K=3$ categories and $4$ explanatory variables (including intercept) has $4*(3-1)=8$ unknown $\beta$ parameters to estimate.

## Data

I use data from
[UCLA](https://stats.idre.ucla.edu/r/dae/multinomial-logistic-regression/)
for this example. The dependent variable \(y_n\) contains realizations
of \(K=3\) academic program choices from students (general, academic,
vocation). There are two explanatory variables, \(x_1\) is a categorical
variable with three levels for each socio-economic status (low, middle
and high income). The predictor \(x_2\) is a continuous variable of
writing score.

## Read data

``` r
library(foreign)

dat <- read.dta("https://stats.idre.ucla.edu/stat/data/hsbdemo.dta")

# y, dependent variable, program choices from students (general, academic, vocation): prog
# x1, ordinal variable, the social economic status: ses
# x2, continuous variable, writing score: write

# summary
cols <- c('prog', 'ses', 'write')
lapply(dat[,which(colnames(dat) %in% cols)], summary, 'prog')
```

    ## $ses
    ##    low middle   high 
    ##     47     95     58 
    ## 
    ## $prog
    ##  general academic vocation 
    ##       45      105       50 
    ## 
    ## $write
    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   31.00   45.75   54.00   52.77   60.00   67.00

## Multinomial Logistic from \`nnet’ package (Frequentist)

Lets take the *general* program choice as pivot and *academic* and
*vocational* as \(K-1\) categories.

``` r
# change pivot category
dat$prog2 <- relevel(dat$prog, ref = "general")

# load nnet package
require(nnet)
```

    ## Loading required package: nnet

``` r
# run model
m1 <- multinom(prog2 ~ ses + write, data = dat)
```

    ## # weights:  15 (8 variable)
    ## initial  value 219.722458 
    ## iter  10 value 179.985215
    ## final  value 179.981726 
    ## converged

``` r
summary(m1)
```

    ## Call:
    ## multinom(formula = prog2 ~ ses + write, data = dat)
    ## 
    ## Coefficients:
    ##          (Intercept) sesmiddle   seshigh       write
    ## academic   -2.851973 0.5332914 1.1628257  0.05792480
    ## vocation    2.366097 0.8246384 0.1802176 -0.05567514
    ## 
    ## Std. Errors:
    ##          (Intercept) sesmiddle   seshigh      write
    ## academic    1.166437 0.4437319 0.5142215 0.02141092
    ## vocation    1.174251 0.4901237 0.6484508 0.02333135
    ## 
    ## Residual Deviance: 359.9635 
    ## AIC: 375.9635

``` r
# save coefficients
coef_m1 <- coefficients(m1)
rownames(coef_m1) <- paste0(row.names(coef_m1), '_nnet')
```

## Multinomial Logistic form the \`brms’ package (Bayesian)

``` r
# load package
require('brms')

# run model
m2 <- brm(prog2 ~ ses + write, data = dat, family = categorical(link = "logit"))
```

``` r
# save coefficients.
summ_m2 <- summary(m2)
coef_m2 <- summ_m2$fixed
colnames(coef_m2)
```

    ## [1] "Estimate"  "Est.Error" "l-95% CI"  "u-95% CI"  "Rhat"      "Bulk_ESS" 
    ## [7] "Tail_ESS"

``` r
coef_m2[, c("Estimate", "Est.Error", "l-95% CI", "u-95% CI") ]
```

    ##                         Estimate  Est.Error   l-95% CI    u-95% CI
    ## muacademic_Intercept -2.90522969 1.18387182 -5.2446002 -0.67217529
    ## muvocation_Intercept  2.49127964 1.19490828  0.1819196  4.85516282
    ## muacademic_sesmiddle  0.52648057 0.44738567 -0.3662220  1.39457641
    ## muacademic_seshigh    1.18916213 0.51341377  0.2165600  2.18016911
    ## muacademic_write      0.05919791 0.02177092  0.0179450  0.10196252
    ## muvocation_sesmiddle  0.84310757 0.49515015 -0.1281855  1.81891316
    ## muvocation_seshigh    0.16869099 0.64464083 -1.1150168  1.43414411
    ## muvocation_write     -0.05841079 0.02345308 -0.1051993 -0.01290782

## Comparisson.

We can use *regex* to sort the coefficients from the `brm' output to
reshape into the`nnet’ output. As we can see, the models yield similar
estimates.

``` r
# regex each variable
coef_m2 <- cbind(coef_m2[grepl('Intercept', rownames(coef_m2)), 1L], 
      coef_m2[grepl('middle', rownames(coef_m2)), 1L], 
      coef_m2[grepl('high', rownames(coef_m2)), 1L],
      coef_m2[grepl('write', rownames(coef_m2)), 1L]
      )

# comparisson.
rownames(coef_m2) <- paste0(c('academic', 'vocation'), '_brms')
rbind(coef_m1, coef_m2)
```

    ##               (Intercept) sesmiddle   seshigh       write
    ## academic_nnet   -2.851973 0.5332914 1.1628257  0.05792480
    ## vocation_nnet    2.366097 0.8246384 0.1802176 -0.05567514
    ## academic_brms   -2.905230 0.5264806 1.1891621  0.05919791
    ## vocation_brms    2.491280 0.8431076 0.1686910 -0.05841079
