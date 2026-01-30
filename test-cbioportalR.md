test-table
================
Édi Correia
2026-01-30

## cbioportalR test

In this test I will try to make a simple graph with data from the
`cbioportalR` package.  
The graph will be a barplot with bars for each type of cancer and their
respective mutated gene.

###### Let’s install the packages

``` r
install.packages("cbioportalR")
install.packages("tidyverse")

library("cbioportalR")
library("tidyverse")
```

###### Checking the database

Set the `cbioportal` database

``` r
set_cbioportal_db(db = "public")
```

    ## ✔ You are successfully connected!

    ## ✔ base_url for this R session is now set to "www.cbioportal.org/api"

Great success! Now let’s have a look at what we’re dealing with…

``` r
available_studies() %>% 
  head(n = 10)
```

    ## # A tibble: 10 × 14
    ##    studyId name  description publicStudy pmid  citation groups status importDate
    ##    <chr>   <chr> <chr>       <lgl>       <chr> <chr>    <chr>   <int> <chr>     
    ##  1 cesc_t… Cerv… "Cervical … TRUE        2962… TCGA, C… "PUBL…      0 2024-12-2…
    ##  2 sarc_t… Sarc… "Sarcoma T… TRUE        2962… TCGA, C… "PUBL…      0 2024-12-2…
    ##  3 crc_or… Colo… "Combined … TRUE        3938… Wala, J… ""          0 2025-06-3…
    ##  4 crc_or… Colo… "Combined … TRUE        3938… Wala, J… ""          0 2025-06-3…
    ##  5 crc_or… Colo… "Combined … TRUE        3938… Wala, J… ""          0 2025-06-3…
    ##  6 lusc_t… Lung… "Lung Squa… TRUE        2962… TCGA, C… "PUBL…      0 2024-12-2…
    ##  7 skcm_t… Skin… "Skin Cuta… TRUE        2962… TCGA, C… "PUBL…      0 2024-12-2…
    ##  8 ov_tcg… Ovar… "Ovarian S… TRUE        2962… TCGA, C… "PUBL…      0 2024-12-2…
    ##  9 hnsc_t… Head… "Head and … TRUE        2962… TCGA, C… "PUBL…      0 2024-12-2…
    ## 10 thym_t… Thym… "Thymoma T… TRUE        2962… TCGA, C… "PUBL…      0 2024-12-2…
    ## # ℹ 5 more variables: allSampleCount <int>, readPermission <lgl>,
    ## #   resourceCounts <list>, cancerTypeId <chr>, referenceGenome <chr>
