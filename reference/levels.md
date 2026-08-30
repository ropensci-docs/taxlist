# Set and retrieves hierarchical levels

Taxonomic hierarchies can be set as levels in
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects, ordered from lower to higher levels.

Add taxonomic levels for specific taxon concepts in a
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object. Also changes in concept circumscription may implicate changes in
its taxonomic hierarchy.

## Usage

``` r
levels(x)

# S3 method for class 'taxlist'
levels(x)

levels(x) <- value

# S3 method for class 'taxlist'
levels(x) <- value
```

## Arguments

- x:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object.

- value:

  A character vector with replacement values for levels o `x`.

## Value

A `character` vector or a
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object with added or modified taxonomic levels.

## Details

Taxonomic levels will be handled as factors in the
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects. Those levels are useful for creating subsets of related groups
(e.g. by functions
[`get_children()`](https://docs.ropensci.org/taxlist/reference/get_children.md)
or
[`get_parents()`](https://docs.ropensci.org/taxlist/reference/get_children.md)).

Levels in combination to parent-child relationships will be further used
for checking consistency of taxonomic lists.

A replacement method of the form `levels(x) <- value` it is also
implemented.

## See also

[`prune_levels()`](https://docs.ropensci.org/taxlist/reference/prune_levels.md)

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Get levels of species list
levels(Easplist)
#> [1] "form"       "variety"    "subspecies" "species"    "complex"   
#> [6] "genus"      "family"    

## Add aggregate as new taxonomic level
levels(Easplist) <- c("form", "variety", "subspecies", "species", "complex",
    "aggregate", "genus", "family")
summary(Easplist)
#> object size: 761.5 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 5393 
#> number of taxon concepts: 3887 
#> trait entries: 311 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 3698 
#> concepts with children: 1343 
#> 
#> concepts with rank information: 3887 
#> concepts without rank information: 0 
#> 
#> family: 186
#>   genus: 1011
#>     aggregate: 0
#>       complex: 1
#>         species: 2521
#>           subspecies: 71
#>             variety: 95
#>               form: 2
#> 
#> 
```
