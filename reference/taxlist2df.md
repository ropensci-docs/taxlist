# Coerce taxlist objects to data frames

Transform
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects into data frames.

## Usage

``` r
taxlist2df(x, ...)

# S3 method for class 'taxlist'
taxlist2df(
  x,
  include_traits = FALSE,
  include_views = FALSE,
  standard = c("taxlist", "dwc"),
  ...
)
```

## Arguments

- x:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object to be coerced.

- ...:

  Further arguments passed among methods.

- include_traits:

  A logical value indicating whether taxon concept attributes have to be
  included in the output or not.

- include_views:

  A logical value indicating whether taxon views have to be included in
  the output or not.

- standard:

  A character value indicating the standard used to name columns in the
  output data frame. Per default `taxlist` names are used but it can be
  set to `dwc` for renaming some columns according to [Darwin
  Core](https://dwc.tdwg.org/terms/#taxon).
