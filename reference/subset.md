# Subset method for taxlist objects

Subset of
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects will be done applying either logical operations or pattern
matchings. Subsets can be referred to information contained either in
the slot `taxonNames`, `taxonRelations` or `taxonTraits`.

## Usage

``` r
# S4 method for class 'taxlist'
subset(
  x,
  subset,
  slot = "names",
  keep_children = FALSE,
  keep_parents = FALSE,
  ...
)
```

## Arguments

- x:

  Object of class
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

- subset:

  Logical vector or logical operation to apply as subset.

- slot:

  Character value indicating the slot to be used for the subset.

- keep_children:

  Logical value applied to hierarchical structures.

- keep_parents:

  Logical value applied to hierarchical structures.

- ...:

  Further arguments to be passed to or from other methods.

## Value

An object of class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

## Details

The argument `subset` will be applied to the slot specified in argument
`slot`. This argument also allows partial matchings.

Arguments `keep_children` and `keep_parents` are applied to objects
including parent-child relationships. When those arguments are set as
`FALSE` (the default), children or parents of selected taxon concepts
will not be included in the subset.

Be aware that `subset()` won't work properly inside of function
definitions.

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Produce a data set with only reed plants
sp_list <- subset(x = Easplist, subset = life_form == "reed_plant",
    slot = "taxonTraits", keep_parents = TRUE)
sp_list
#> object size: 22.3 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 100 
#> number of taxon concepts: 27 
#> trait entries: 14 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 24 
#> concepts with children: 13 
#> 
#> concepts with rank information: 27 
#> concepts without rank information: 0 
#> 
#> family: 3
#>   genus: 10
#>     complex: 0
#>       species: 14
#>         subspecies: 0
#>           variety: 0
#>             form: 0
#> 
#> 

summary(as.factor(sp_list$life_form))
#> reed_plant        NAs 
#>         14         13 
```
