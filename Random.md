---
title: "Random number generation"
author: "km"
date: "2019/7/19"
output: 
  html_document: 
    keep_md: TRUE
---





## uniform distribution

### in R


```r
seed <- 71
N <- 100

unif_R <- runif(N)

unif_R %>% head(10)
```

```
##  [1] 0.78386602 0.27940215 0.08823758 0.84667689 0.49747770 0.65701754
##  [7] 0.77580759 0.44024030 0.10642277 0.02512283
```

```r
unif_R %>% mean()
```

```
## [1] 0.5368584
```


### in Numpy


```python
import numpy as np

seed = int(r.seed)
N = int(r.N)

np.random.seed(seed=seed)
unif_np = np.random.rand(N)

unif_np[:10]
```

```
## array([0.18557527, 0.3865993 , 0.8318962 , 0.19869745, 0.91655797,
##        0.7883107 , 0.72260428, 0.99569452, 0.84537214, 0.23372659])
```

```python
np.mean(unif_np)
```

```
## 0.5331716825009918
```

### in random (python)


```python
import random

random.seed(seed)

unif_rd = np.array([random.random() for i in range(N)])

unif_rd[:10]
```

```
## array([0.32375335, 0.62002949, 0.00848   , 0.98285779, 0.82215851,
##        0.99901979, 0.2633503 , 0.19948865, 0.05473797, 0.19380238])
```

```python
np.mean(unif_rd)
```

```
## 0.45940250662734816
```


### in R with imported python random pkg


```r
rd <- import("random")
rd$seed(seed)
map_dbl(1:N, ~rd$random()) %>% head(10)
```

```
##  [1] 0.323753346 0.620029485 0.008479999 0.982857787 0.822158506
##  [6] 0.999019788 0.263350301 0.199488651 0.054737975 0.193802375
```

### in R

```r
set.seed(71)
runif(10, 0, 1)
```

```
##  [1] 0.3329281 0.5551039 0.3273700 0.2116670 0.3161214 0.9472664 0.6617140
##  [8] 0.8894212 0.3380099 0.4347503
```

### in Python with Pyper


```python
import pyper

r = pyper.R()
r("set.seed(71); unif_r <- runif(10, 0, 1)")

result = r.get("unif_r")
result
```




```
## array([0.33292806, 0.55510387, 0.32736996, 0.21166696, 0.31612136,
##        0.94726643, 0.66171397, 0.88942116, 0.33800988, 0.43475031])
```


----

----

### ex.env.


```r
py_config()$version
```

```
## [1] "3.7"
```

```r
py_config()$numpy$version
```

```
## [1] '1.16.4'
```

```r
sessioninfo::session_info()
```

```
## ─ Session info ──────────────────────────────────────────────────────────
##  setting  value                       
##  version  R version 3.6.1 (2019-07-05)
##  os       macOS Mojave 10.14.3        
##  system   x86_64, darwin15.6.0        
##  ui       X11                         
##  language (EN)                        
##  collate  ja_JP.UTF-8                 
##  ctype    ja_JP.UTF-8                 
##  tz       Asia/Tokyo                  
##  date     2019-07-24                  
## 
## ─ Packages ──────────────────────────────────────────────────────────────
##  package     * version date       lib source                            
##  assertthat    0.2.1   2019-03-21 [1] CRAN (R 3.6.0)                    
##  cli           1.1.0   2019-03-19 [1] CRAN (R 3.6.0)                    
##  crayon        1.3.4   2017-09-16 [1] CRAN (R 3.6.0)                    
##  digest        0.6.20  2019-07-04 [1] CRAN (R 3.6.0)                    
##  dplyr       * 0.8.3   2019-07-04 [1] CRAN (R 3.6.0)                    
##  evaluate      0.14    2019-05-28 [1] CRAN (R 3.6.0)                    
##  glue          1.3.1   2019-03-12 [1] CRAN (R 3.6.0)                    
##  htmltools     0.3.6   2017-04-28 [1] CRAN (R 3.6.0)                    
##  jsonlite      1.6     2018-12-07 [1] CRAN (R 3.6.0)                    
##  knitr         1.23    2019-05-18 [1] CRAN (R 3.6.0)                    
##  lattice       0.20-38 2018-11-04 [1] CRAN (R 3.6.1)                    
##  magrittr      1.5     2014-11-22 [1] CRAN (R 3.6.0)                    
##  Matrix        1.2-17  2019-03-22 [1] CRAN (R 3.6.1)                    
##  pillar        1.4.2   2019-06-29 [1] CRAN (R 3.6.0)                    
##  pkgconfig     2.0.2   2018-08-16 [1] CRAN (R 3.6.0)                    
##  purrr       * 0.3.2   2019-03-15 [1] CRAN (R 3.6.0)                    
##  R6            2.4.0   2019-02-14 [1] CRAN (R 3.6.0)                    
##  Rcpp          1.0.1   2019-03-17 [1] CRAN (R 3.6.0)                    
##  reticulate  * 1.12    2019-04-12 [1] CRAN (R 3.6.0)                    
##  rlang         0.4.0   2019-06-25 [1] CRAN (R 3.6.0)                    
##  rmarkdown     1.14.1  2019-07-19 [1] Github (rstudio/rmarkdown@3c33142)
##  sessioninfo   1.1.1   2018-11-05 [1] CRAN (R 3.6.0)                    
##  stringi       1.4.3   2019-03-12 [1] CRAN (R 3.6.0)                    
##  stringr       1.4.0   2019-02-10 [1] CRAN (R 3.6.0)                    
##  tibble        2.1.3   2019-06-06 [1] CRAN (R 3.6.0)                    
##  tidyselect    0.2.5   2018-10-11 [1] CRAN (R 3.6.0)                    
##  withr         2.1.2   2018-03-15 [1] CRAN (R 3.6.0)                    
##  xfun          0.8     2019-06-25 [1] CRAN (R 3.6.0)                    
##  yaml          2.2.0   2018-07-25 [1] CRAN (R 3.6.0)                    
## 
## [1] /Library/Frameworks/R.framework/Versions/3.6/Resources/library
```
