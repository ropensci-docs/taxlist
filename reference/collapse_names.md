# Collapse names

Collapse name strings for document contents. It will be used internally
when formatting several names and including them in a text body.

## Usage

``` r
collapse_names(x, collapse)
```

## Arguments

- x:

  A character vector containing a chain of names.

- collapse:

  A character value or vector used to collapse the names and passed to
  [paste0](https://rdrr.io/r/base/paste.html). If its lenght is 2, the
  second value will be used to connect the two last names.
