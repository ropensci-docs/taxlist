# Count taxa within a taxlist object.

Counting number of taxa within
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects or character vectors containing taxon names.

## Usage

``` r
count_taxa(object, data, ...)

# S4 method for class 'character,missing'
count_taxa(object, na.rm = TRUE, ...)

# S4 method for class 'factor,missing'
count_taxa(object, na.rm = TRUE, ...)

# S4 method for class 'taxlist,missing'
count_taxa(object, level, ...)

# S4 method for class 'formula,taxlist'
count_taxa(object, data, include_na = FALSE, suffix = "_count", ...)
```

## Arguments

- object:

  An object containing a taxonomic list or a formula.

- data:

  An object of class
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  in the `formula` method.

- ...:

  further arguments passed among methods.

- na.rm:

  Logical value, whether NAs have to be removed from the input vector or
  not.

- level:

  Character value indicating the taxonomic rank of counted taxa.

- include_na:

  Logical value indicating whether `NA` values in a taxon trait should
  be considered for counting taxa or just ignored (only used in
  `formula` method).

- suffix:

  Character value used as suffix for the counted rank in the output data
  frame (only used in `formula` method).

## Value

An integer with the number of taxa.

## Details

This function is written by convenience in order to reduce code for
counting taxa within
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects and it is just a wrapper of
[`length()`](https://rdrr.io/r/base/length.html).

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## factor method
count_taxa(iris$Species)
#> [1] 3

## taxlist method
count_taxa(Easplist)
#> [1] 3887

## count only species
count_taxa(Easplist, level = "species")
#> [1] 2521

## using a formula
count_taxa(~life_form, Easplist, include_na = TRUE)
#>             life_form taxa_count
#> 1                 NAs       3576
#> 2    acropleustophyte          8
#> 3         chamaephyte         25
#> 4      climbing_plant         25
#> 5  facultative_annual         20
#> 6     obligate_annual        114
#> 7        phanerophyte         26
#> 8    pleustohelophyte          8
#> 9          reed_plant         14
#> 10      reptant_plant         19
#> 11      tussock_plant         52
```
