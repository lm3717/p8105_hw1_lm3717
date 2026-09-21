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

![](homework_1_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

## Problem 2

``` r
problem2_df =
  tibble(
    random_sample = rnorm(10),
    sample_positive = random_sample > 0,
    character_vector = c(
      "a", "b", "c", "d", "e",
      "f", "g", "h", "i", "j"
    ),
    factor_vector = factor(
      c(
        "A", "B", "C", "A", "B",
        "C", "A", "B", "C", "A"
      )
    )
  )

problem2_df
```

    ## # A tibble: 10 × 4
    ##    random_sample sample_positive character_vector factor_vector
    ##            <dbl> <lgl>           <chr>            <fct>        
    ##  1        -0.314 FALSE           a                A            
    ##  2         0.947 TRUE            b                B            
    ##  3         1.21  TRUE            c                C            
    ##  4         1.76  TRUE            d                A            
    ##  5         2.70  TRUE            e                B            
    ##  6         0.398 TRUE            f                C            
    ##  7        -0.935 FALSE           g                A            
    ##  8         2.11  TRUE            h                B            
    ##  9        -0.675 FALSE           i                C            
    ## 10         0.709 TRUE            j                A

``` r
mean(pull(problem2_df, random_sample))
```

    ## [1] 0.7911901

``` r
mean(pull(problem2_df, sample_positive))
```

    ## [1] 0.7

``` r
mean(pull(problem2_df, character_vector))
```

    ## Warning in mean.default(pull(problem2_df, character_vector)): argument is not
    ## numeric or logical: returning NA

    ## [1] NA

``` r
mean(pull(problem2_df, factor_vector))
```

    ## Warning in mean.default(pull(problem2_df, factor_vector)): argument is not
    ## numeric or logical: returning NA

    ## [1] NA
