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

``` r
df_year <- df %>%
  group_by(year) %>%
  summarise(
    Polyarchy = median(polyarchy, na.rm = TRUE),
    `Liberal Democracy` = median(libdem, na.rm = TRUE),
    `Deliberative Democracy` = median(delibdem, na.rm = TRUE),
    `Participatory Democracy` = median(partidem, na.rm = TRUE),
    `Egalitarian Democracy` = median(egaldem, na.rm = TRUE),
    `GDP Per Capita` = median(gdppc, na.rm = TRUE)
  )

df_long <- df_year %>%
  pivot_longer(
    cols = c(Polyarchy, `Liberal Democracy`, `Deliberative Democracy`, `Participatory Democracy`,  `Egalitarian Democracy`),
    names_to = "index",
    values_to = "value"
  )

df_long <- df_long %>%
  mutate(
    index = factor(
      index,
      levels = c(
        "Polyarchy",
        "Liberal Democracy",
        "Deliberative Democracy",
        "Participatory Democracy",
        "Egalitarian Democracy"
      )))


scale_factor <- max(df_year$`GDP Per Capita`, na.rm = TRUE) /
                max(df_long$value, na.rm = TRUE)

ggplot(df_year, aes(x = year)) +
  geom_line(aes(y = `GDP Per Capita`, color = "GDP per capita"), size = 1.2) +
  geom_line(
    data = df_long,
    aes(y = value * scale_factor, color = index),
    size = 1.2
  ) +
  scale_y_continuous(
    name = "GDP per capita",
    sec.axis = sec_axis(~ . / scale_factor, name = "Democracy Indices")
  ) +
  labs(
    title = "Democracy and Economy (1960–2024)",
    x = "Year",
    color = "Variables",
    caption = "Source: V-Dem Dataset v13; World Bank World Development Indicators (GDP per capita) "
  ) +
  theme_minimal() +
  scale_color_viridis_d() +
  annotate("rect", 
  xmin = 1975, 
  xmax = 1990, 
  ymin = 0, 
  ymax = 8000, 
  alpha = 0.05, 
  fill = "#440154FF") +
   # geom_vline(xintercept = 1975, linetype = "dotted", color = "#440154FF") +
   # geom_vline(xintercept = 1990, linetype = "dotted", color = "#440154FF") +
   # geom_text(aes(x = 1966, y = 7000), 
   # label = "Third Wave \n Democratization", size = 3.5)
    geom_vline(xintercept = 1975, linetype = "dotted", color = "#440154FF") +
   geom_vline(xintercept = 1990, linetype = "dotted", color = "#440154FF") +
   geom_text(aes(x = 1982, y = 7000),
   label = "Third Wave \n Democratization", size = 3.2)
```

    ## Warning: Using `size` aesthetic for lines was deprecated in ggplot2 3.4.0.
    ## ℹ Please use `linewidth` instead.
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

    ## Warning in geom_text(aes(x = 1982, y = 7000), label = "Third Wave \n Democratization", : All aesthetics have length 1, but the data has 65 rows.
    ## ℹ Please consider using `annotate()` or provide this layer with data containing
    ##   a single row.

![](Figure_1_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->
