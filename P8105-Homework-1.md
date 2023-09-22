P8105 Homework 1
================
Laylah Jones
2023-09-22

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
# Accessing dataset information.

data("early_january_weather")
nrow(early_january_weather)
```

    ## [1] 358

``` r
ncol(early_january_weather)
```

    ## [1] 15

``` r
# Finding the mean.

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
# Making a scatter plot.

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
# Creating a data frame. 

hw_df = 
  tibble(
    vec_numeric = rnorm(10),
    vec_char = c(1, 2, 3, 4, 5, 6, 7, 8, 9, 10),
    vec_factor = factor(c("High", "High", "Low", "Medium", "Medium", "Low", "High", "Low", "Low", "Low")),
    vec_logic = vec_numeric > 0
  )
hw_df
```

    ## # A tibble: 10 × 4
    ##    vec_numeric vec_char vec_factor vec_logic
    ##          <dbl>    <dbl> <fct>      <lgl>    
    ##  1      -0.267        1 High       FALSE    
    ##  2      -2.10         2 High       FALSE    
    ##  3       0.771        3 Low        TRUE     
    ##  4      -0.877        4 Medium     FALSE    
    ##  5      -0.500        5 Medium     FALSE    
    ##  6       0.438        6 Low        TRUE     
    ##  7       0.262        7 High       TRUE     
    ##  8      -1.92         8 Low        FALSE    
    ##  9       1.36         9 Low        TRUE     
    ## 10       0.313       10 Low        TRUE

``` r
# Now I will find the mean of each variable in the dataframe.

mean(pull(hw_df, vec_numeric))
```

    ## [1] -0.2525495
