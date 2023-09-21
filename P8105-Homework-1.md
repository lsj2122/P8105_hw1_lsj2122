P8105 Homework 1
================
Laylah Jones
2023-09-21

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.3     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(moderndive)
```

# Problem 1

``` r
# Accessing dataset information

data("early_january_weather")
nrow(early_january_weather)
```

    ## [1] 358

``` r
ncol(early_january_weather)
```

    ## [1] 15

``` r
# Finding the mean

mean(pull(early_january_weather, temp))
```

    ## [1] 39.58212

The structure of the dataset is looking at the meteorological weather
during early January. The 15 variables included are origin, year, month,
day, hour, temperature, dew point, humidity, wind direction, wind speed,
wind gust, precipitation, pressure, visibility, and the time hour. The
values of important values are the ones that are dependent and changing
in the dataset such as temp, dewp, humid, wind_dir, wind_speed,
wind_gust, and pressure. However, the important value that we are
focusing on now is the temperature. The dataset has 358 rows and 15
columns. The mean is 39.58212.

``` r
# Making a scatter plot

ggplot(early_january_weather, aes(x = time_hour, y = temp, color = humid)) + geom_point()
```

![](P8105-Homework-1_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

The apparent pattern is that as the time increases the temperature
fluctuates. As time goes on, the humidity and temperature have a general
increase.

``` r
ggsave("early_january_weather.pdf")
```

    ## Saving 7 x 5 in image

# Problem 2

``` r
# This code chunk creates a data frame 

hw_df = 
  tibble(
    vec_numeric = rnorm(10),
    vec_char = c(1, 2, 3, 4, 5, 6, 7, 8, 9, 10),
    vec_factor = factor(c("High", "High", "Low", "Medium", "Medium", "Low", "High", "Low", "Low", "Low"))
  )
hw_df
```

    ## # A tibble: 10 × 3
    ##    vec_numeric vec_char vec_factor
    ##          <dbl>    <dbl> <fct>     
    ##  1      -0.648        1 High      
    ##  2      -0.771        2 High      
    ##  3      -0.548        3 Low       
    ##  4       0.500        4 Medium    
    ##  5      -1.50         5 Medium    
    ##  6       0.131        6 Low       
    ##  7      -1.26         7 High      
    ##  8       0.947        8 Low       
    ##  9       0.888        9 Low       
    ## 10      -1.50        10 Low