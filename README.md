[![R-CMD-check](https://github.com/hsonne/findblobs/workflows/R-CMD-check/badge.svg)](https://github.com/hsonne/findblobs/actions?query=workflow%3AR-CMD-check)
[![pkgdown](https://github.com/hsonne/findblobs/workflows/pkgdown/badge.svg)](https://github.com/hsonne/findblobs/actions?query=workflow%3Apkgdown)
[![codecov](https://codecov.io/github/hsonne/findblobs/branch/main/graphs/badge.svg)](https://codecov.io/github/hsonne/findblobs)
[![Project Status](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/#experimental)
[![CRAN_Status_Badge](https://www.r-pkg.org/badges/version/findblobs)]()

This package provides functions to find blobs of connected cells
in a matrix of logical. This is also known as Blob Colouring.

## Installation

```r
# Install package "remotes" from CRAN
if (! require("remotes")) {
  install.packages("remotes", repos = "https://cloud.r-project.org")
}

# Install hsonne`s package 'findblobs' from GitHub
remotes::install_github("hsonne/findblobs")
```

Plot an Integer Matrix
----------------------

``` r
findblobs::plot_integer_matrix(matrix(nrow = 5, byrow = TRUE, c(
  2, 2, 2, 2, 2,
  2, 0, 1, 0, 2,
  2, 1, 1, 1, 2,
  2, 0, 1, 0, 2,
  2, 2, 2, 2, 2
)))
```

![](README_files/figure-markdown_github/unnamed-chunk-2-1.png)

Create Random Blobs
-------------------

``` r
random_blobs <- findblobs::place_random_blobs(
  n_blobs = 5, min_fields = 3, max_fields = 10
)
```

![](README_files/figure-markdown_github/unnamed-chunk-3-1.png)

Find Blobs
----------

``` r
# Provide matrix of logical
M <- random_blobs > 0

# Find the blobs
found_blobs <- findblobs:::get_blobs(M)
```

    ## Getting column blobs ... ok. (0.00s) 
    ## Getting row blobs ... ok. (0.04s) 
    ## Merging group info with method 6 ... ok. (0.01s)

``` r
# Plot the blobs. Compare with random_blobs above
findblobs::plot_integer_matrix(found_blobs)
```

![](README_files/figure-markdown_github/unnamed-chunk-4-1.png)
