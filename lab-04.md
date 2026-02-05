Lab 04 - La Quinta is Spanish for next to Denny’s, Pt. 1
================
Lily Botha
02/05/2026

### Load packages and data

``` r
library(tidyverse) 
library(dsbox) 
```

``` r
states <- read_csv("data/states.csv")
```

### Exercise 1

The Denny’s dataset has 1643 rows and 6 columns. Each row represents a
Denny’s restaurant. The columns are the variables: address, city, state,
zip, longitude, and latitude.

``` r
dn <- dennys
nrow(dn)
```

    ## [1] 1643

``` r
ncol(dn)
```

    ## [1] 6

### Exercise 2

The La Quinta dataset has 909 rows and 6 columns. Each row represents a
La Quinta hotel. The columns are the variables: address, city, state,
zip, longitude, and latitude.

``` r
lq <- laquinta
nrow(lq)
```

    ## [1] 909

``` r
ncol(lq)
```

    ## [1] 6

### Exercise 3

There are La Quinta hotels outside of the US: in New Zealand, Georgia,
Turkey, United Arab Emirates, Colombia, and Ecuador. All of the Denny’s
are located in the US.

### Exercise 4

One possibility is to filter by longitude and latitude, which would
require finding out the coordinate range of the US. I think a simpler
option would be to filter by the state abbreviations, and anything
outside of the US’s 50 states would be cut. Its also possible that the
address of locations outside the US is formatted differently, so we
could filter that way, but that seems risky.

### Exercise 5

There are 0 Denny’s locations outside the US.

``` r
dn %>%
  filter(!(state %in% states$abbreviation)) #filter for states that are not in states$abbreviation
```

    ## # A tibble: 0 × 6
    ## # ℹ 6 variables: address <chr>, city <chr>, state <chr>, zip <chr>,
    ## #   longitude <dbl>, latitude <dbl>

### Exercise 6

``` r
dn %>%
  mutate(country = "United States") #add a country variable to Denny's dataset and set all observations to "United States"
```

    ## # A tibble: 1,643 × 7
    ##    address                        city    state zip   longitude latitude country
    ##    <chr>                          <chr>   <chr> <chr>     <dbl>    <dbl> <chr>  
    ##  1 2900 Denali                    Anchor… AK    99503    -150.      61.2 United…
    ##  2 3850 Debarr Road               Anchor… AK    99508    -150.      61.2 United…
    ##  3 1929 Airport Way               Fairba… AK    99701    -148.      64.8 United…
    ##  4 230 Connector Dr               Auburn  AL    36849     -85.5     32.6 United…
    ##  5 224 Daniel Payne Drive N       Birmin… AL    35207     -86.8     33.6 United…
    ##  6 900 16th St S, Commons on Gree Birmin… AL    35294     -86.8     33.5 United…
    ##  7 5931 Alabama Highway, #157     Cullman AL    35056     -86.9     34.2 United…
    ##  8 2190 Ross Clark Circle         Dothan  AL    36301     -85.4     31.2 United…
    ##  9 900 Tyson Rd                   Hope H… AL    36043     -86.4     32.2 United…
    ## 10 4874 University Drive          Huntsv… AL    35816     -86.7     34.7 United…
    ## # ℹ 1,633 more rows

### Exercise 7

There are La Quinta locations in New Zealand, Georgia, Turkey, United
Arab Emirates, Colombia, and Ecuador.

### Exercise 8
