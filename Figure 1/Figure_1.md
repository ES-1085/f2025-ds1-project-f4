Figure_1
================

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.1     ✔ stringr   1.5.2
    ## ✔ ggplot2   4.0.0     ✔ tibble    3.3.0
    ## ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
    ## ✔ purrr     1.1.0     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(broom)
# install.packages("skimr")
library(skimr)
library(stringr)
library(sf)
```

    ## Linking to GEOS 3.8.0, GDAL 3.0.4, PROJ 6.3.1; sf_use_s2() is TRUE

``` r
library(RColorBrewer)
library(htmltools)
library(leafsync)
library(leaflet)
library(kableExtra)
```

    ## 
    ## Attaching package: 'kableExtra'
    ## 
    ## The following object is masked from 'package:dplyr':
    ## 
    ##     group_rows

``` r
df <- read_csv("../data/vdem3.csv")
```

    ## Rows: 17290 Columns: 19
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr   (7): country_name, histname, country_text_id, country, iso3c, region, ...
    ## dbl  (11): year, country_id, v2x_polyarchy, v2x_libdem, v2x_partipdem, v2x_d...
    ## date  (1): historical_date
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
df <- df %>% 
  rename(polyarchy = v2x_polyarchy, 
         libdem = v2x_libdem, 
         delibdem = v2x_delibdem,
         partidem = v2x_partipdem,
         egaldem = v2x_egaldem, 
         countryid = country_text_id,
         gdppc = gdp_per_capita
         )
```
