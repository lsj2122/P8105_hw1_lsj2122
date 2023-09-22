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

``` r
mean(pull(early_january_weather, humid))
```

    ## [1] 65.4767

The structure of the dataset is looking at the meteorological weather
during early January. The 15 variables included are origin, year, month,
day, hour, temperature, dew point, humidity, wind direction, wind speed,
wind gust, precipitation, pressure, visibility, and the time hour. The
dataset has 358 rows and 15 columns. The values of important values are
the ones that are dependent and changing in the dataset such as temp,
dewp, humid, wind_dir, wind_speed, wind_gust, and pressure. However, the
important value that we are focusing on now is the temperature and
humidity. The mean temperature 39.58212 or around 40 degrees. The mean
humidity is 65.4767 or around 65.

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
    ##  1      -1.34         1 High       FALSE    
    ##  2      -1.73         2 High       FALSE    
    ##  3      -0.177        3 Low        FALSE    
    ##  4      -0.192        4 Medium     FALSE    
    ##  5       0.331        5 Medium     TRUE     
    ##  6       0.864        6 Low        TRUE     
    ##  7       0.888        7 High       TRUE     
    ##  8      -0.987        8 Low        FALSE    
    ##  9       0.586        9 Low        TRUE     
    ## 10      -1.56        10 Low        FALSE

``` r
# Now I will find the mean of each variable in the dataframe.

mean(pull(hw_df, vec_numeric))
```

    ## [1] -0.3320828

``` r
# This code chunk applies the as.numeric function to the logical, character, and factor variables.

as.numeric(pull(hw_df, vec_char))
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10

``` r
as.numeric(pull(hw_df, vec_factor))
```

    ##  [1] 1 1 2 3 3 2 1 2 2 2

``` r
as.numeric(pull(hw_df, vec_logic))
```

    ##  [1] 0 0 0 0 1 1 1 0 1 0

``` r
eval = FALSE
```

When I ran the as.numeric function, it converted the logical, character,
and factor variables into numeric variables. It does this to make my
data frame variables more interpretable as numbers instead of as
phrases. This helps explains what happens when I try to get the mean
because you cannot get the mean of variables from phrases, however by
turning the phrases into numerical variables you can then use the
formula of mean. For example, the mean of the factor variables (which
were in the form of High, Medium, and Low) were converted so that each
variable is represented numerically (High = 1, Medium = 3, Low = 3), you
can take the sum of those numbers which is 19, and divide it by the
number of variables in the data frame which is 10 to get a mean of 1.9.
