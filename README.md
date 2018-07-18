
<!-- README.md is generated from README.Rmd. Please edit that file -->
blendR
======

The goal of blendR is to provide statistically valid estimators of total (and standard errors) when blending a non-probability sample with a probability sample. The two samples are considered to follow capture-recapture methodology, with the capture sample being the non-probability sample and the recapture sample being the probability sample. This package is based upon research by Liu et al (2017) and the dissertation work of the package author. Additionaal estimators will be released in future versions.

Installation
------------

You can install blendR from github with:

``` r
# install.packages("devtools")
devtools::install_github("williamsbenjamin/blendR")
```

Example
-------

This is a basic example which shows you how to solve a common problem:

``` r
## basic example code
library(blendR)
s_design <- survey::svydesign(id = ~psu,
                              strat = ~stratum,
                              prob = ~prob,
                              nest = T,
                              data = red_snapper_sampled)

t_p(data = red_snapper_sampled,
    recapture_total = number_caught_ps,
    captured = captured_indicator,
    survey_design = s_design,
    capture_units = nrow(self_reports))
#> $total
#> [1] 41723.39
#> 
#> $se
#> [1] 13098.89
```
