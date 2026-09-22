Homework 1
================
Lina Marcinczyk
2026-09-21

``` r
library(tidyverse)
```

## Problem 1

``` r
data("penguins", package = "palmerpenguins")
```

### Description of the ‘penguins’ dataset

The `penguins` dataset contains measurements on penguins from three
species: Adelie, Gentoo, Chinstrap. Important variables include species,
island, bill length, bill depth, flipper length, body mass, sex, and
year.

The dataset contains 344 rows and 8 columns.

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

### Dataframe

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
    ##  1      -1.05    FALSE           a                A            
    ##  2       1.08    TRUE            b                B            
    ##  3      -0.428   FALSE           c                C            
    ##  4       0.765   TRUE            d                A            
    ##  5      -0.216   FALSE           e                B            
    ##  6       1.26    TRUE            f                C            
    ##  7      -0.00320 FALSE           g                A            
    ##  8       0.389   TRUE            h                B            
    ##  9       2.16    TRUE            i                C            
    ## 10       0.656   TRUE            j                A

### Mean Values

``` r
mean(pull(problem2_df, random_sample))
```

    ## [1] 0.4602322

``` r
mean(pull(problem2_df, sample_positive))
```

    ## [1] 0.6

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

The mean can be correctly calculated for the numeric and logical
variables. For the logical variable, R treats TRUE as 1 and FALSE as 0,
so the mean represents the proportion of TRUE values. The character and
factor variables do not produce numerical means, which is expected.

``` r
as.numeric(pull(problem2_df, sample_positive))
as.numeric(pull(problem2_df, character_vector))
as.numeric(pull(problem2_df, factor_vector))
```

Converting the logical variable to numeric changes TRUE to 1 and FALSE
to 0. The character variable cannot be converted to numeric values, so
the conversion produces NAs. The factor variable is converted to the
numeric codes corresponding to its factor levels. This helps explain why
the mean works for logical variables but not directly for character or
factor variables.
