Homework 1
================
Lina Marcinczyk
2026-09-21

``` r
library(tidyverse) 
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.2.1     ✔ readr     2.2.0
    ## ✔ forcats   1.0.1     ✔ stringr   1.6.0
    ## ✔ ggplot2   4.0.3     ✔ tibble    3.3.1
    ## ✔ lubridate 1.9.5     ✔ tidyr     1.3.2
    ## ✔ purrr     1.2.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

## Problem 1

``` r
data("penguins", package = "palmerpenguins")
```

### Description of the pengiuns dataset

The `penguins` dataset contains measurements on penguins from three
species: Adelie, Gentoo, Chinstrap. Important variables include species,
island, bill length, bill depth, flipper length, body mass, sex, and
year.

The dataset contains 344 rows and 8 columns

The mean flipper length is 200.9152047 mm.

### Scatterplot

``` r
penguin_plot =
  ggplot(
    penguins,
    aes(
      x = bill_length_mm,
      y = flipper_length_mm,
      color = species
    )
  ) +
  geom_point()

penguin_plot
```

    ## Warning: Removed 2 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](github_document_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->
