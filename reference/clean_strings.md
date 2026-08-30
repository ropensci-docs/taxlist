# Cleaning character strings.

Multiple, leading and trailing white spaces as well as wrong encodings
may cause serious problems in information dealing with taxonomic names.
The function `clean_strings` get rid of them.

## Usage

``` r
clean_strings(x, ...)

# S4 method for class 'character'
clean_strings(x, from = "utf8", to = "utf8", ...)

# S4 method for class 'factor'
clean_strings(x, from = "utf8", to = "utf8", ...)

# S4 method for class 'data.frame'
clean_strings(x, from = "utf8", to = "utf8", ...)
```

## Arguments

- x:

  Object to be cleaned.

- ...:

  Further arguments passed among methods (not yet in use).

- from, to:

  Arguments passed to [`iconv()`](https://rdrr.io/r/base/iconv.html).

## Value

The same as input `x`.

## Details

This function automatically deletes leading, trailing and multiple white
spaces, either in strings (method `character`), levels (method `factor`
or in single columns (method `data.frame`).

## Author

Miguel Alvarez.

## Examples

``` r
## Leading, trailing and multiple spaces
clean_strings(" Cyperus    papyrus L.     ")
#> [1] "Cyperus papyrus L."
```
