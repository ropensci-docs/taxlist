# Data manipulation.

This is a series of functions designed for a fast coding of replacements
both, as internal functions and in workflows dealing with information
stored in vectors. Such functions are especially useful when handling
with functional traits stored in
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects.

`replace_x()` is used to exchange values in vectors. `replace_idx()`
changes values in vectors by matching indices or conditions. The
function `replace_na()` works in the same way as `replace_idx()` but
will only insert values in empty elements (NAs).

## Usage

``` r
replace_x(x, old, new)

replace_idx(x, idx1 = x, idx2 = idx1, new)

replace_na(x, idx1, idx2 = idx1, new)
```

## Arguments

- x:

  A vector to be modified. In the case of
  [`insert_rows()`](https://docs.ropensci.org/taxlist/reference/insert_rows.md),
  `x` is a data frame.

- old:

  A vector with values to be replaced by `replace_x()` in a vector.

- new:

  A vector containing values to be inserted, either comparing values or
  using indices.

- idx1, idx2:

  Indices applied for value replacements to match `x` with `new`,
  respectively. If `idx2` is not provided, it will be assumed as
  equivalent to `idx1`.

## Value

A vector or data frame with the modified values.

## Author

Miguel Alvarez.

## Examples

``` r
## Replace values in vector
replace_x(x = letters, old = c("b", "p", "f"), new = c("bee", "pork", "fungus"))
#>  [1] "a"      "bee"    "c"      "d"      "e"      "fungus" "g"      "h"     
#>  [9] "i"      "j"      "k"      "l"      "m"      "n"      "o"      "pork"  
#> [17] "q"      "r"      "s"      "t"      "u"      "v"      "w"      "x"     
#> [25] "y"      "z"     

## Replace values using indices
replace_idx(x = letters, idx1 = 1:length(letters), idx2 = c(2, 7, 17),
  new = c("second", "seventh", "seventeenth"))
#>  [1] "a"           "second"      "c"           "d"           "e"          
#>  [6] "f"           "seventh"     "h"           "i"           "j"          
#> [11] "k"           "l"           "m"           "n"           "o"          
#> [16] "p"           "seventeenth" "r"           "s"           "t"          
#> [21] "u"           "v"           "w"           "x"           "y"          
#> [26] "z"          

## Replace values if they are NAs
letters[2] <- NA
replace_na(x = letters, idx1 = 1:length(letters), idx2 = c(1:3),
  new = c("alpha", "beta", "zeta"))
#>  [1] "a"    "beta" "c"    "d"    "e"    "f"    "g"    "h"    "i"    "j"   
#> [11] "k"    "l"    "m"    "n"    "o"    "p"    "q"    "r"    "s"    "t"   
#> [21] "u"    "v"    "w"    "x"    "y"    "z"   

## The same applications but this time for functional traits
summary(as.factor(Easplist$life_form))
#>   acropleustophyte        chamaephyte     climbing_plant facultative_annual 
#>                  8                 25                 25                 20 
#>    obligate_annual       phanerophyte   pleustohelophyte         reed_plant 
#>                114                 26                  8                 14 
#>      reptant_plant      tussock_plant                NAs 
#>                 19                 52               3576 

# Merge annuals
Easplist@taxonTraits$lifeform <- replace_x(x = Easplist@taxonTraits$life_form,
  old = c("obligate_annual", "facultative_annual"), new = c("annual", "annual"))
summary(as.factor(Easplist$lifeform))
#> acropleustophyte           annual      chamaephyte   climbing_plant 
#>                8              134               25               25 
#>     phanerophyte pleustohelophyte       reed_plant    reptant_plant 
#>               26                8               14               19 
#>    tussock_plant              NAs 
#>               52             3576 

# The same effect
Easplist@taxonTraits$lifeform <- replace_idx(x = Easplist@taxonTraits$life_form,
  idx1 = grepl("annual", Easplist@taxonTraits$life_form), idx2 = TRUE,
  new = "annual")
summary(as.factor(Easplist$lifeform))
#> acropleustophyte           annual      chamaephyte   climbing_plant 
#>                8              134               25               25 
#>     phanerophyte pleustohelophyte       reed_plant    reptant_plant 
#>               26                8               14               19 
#>    tussock_plant              NAs 
#>               52             3576 
```
