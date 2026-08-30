# Prune not used taxonomic ranks

Taxonomic ranks without taxon concepts will be pruned in
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects.

## Usage

``` r
prune_levels(object, ...)

# S3 method for class 'taxlist'
prune_levels(object, ...)
```

## Arguments

- object:

  An object of class
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

- ...:

  Further arguments passed among methods (not yet in use).

## Value

An object of class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
with pruned taxonomic ranks.

## See also

[levels()](https://docs.ropensci.org/taxlist/reference/levels.md)

## Examples

``` r
## Subset species belonging to Cyperus
Cyperus <- subset(Easplist, TaxonName == "Cyperus", slot = "taxonNames",
    keep_children = TRUE, keep_parents = TRUE)
Cyperus
#> object size: 21.8 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 99 
#> number of taxon concepts: 45 
#> trait entries: 16 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 44 
#> concepts with children: 6 
#> 
#> concepts with rank information: 45 
#> concepts without rank information: 0 
#> 
#> family: 1
#>   genus: 1
#>     complex: 0
#>       species: 38
#>         subspecies: 2
#>           variety: 3
#>             form: 0
#> 
#> 

## Prune not used ranks
prune_levels(Cyperus)
#> object size: 21.7 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 99 
#> number of taxon concepts: 45 
#> trait entries: 16 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 44 
#> concepts with children: 6 
#> 
#> concepts with rank information: 45 
#> concepts without rank information: 0 
#> 
#> family: 1
#>   genus: 1
#>     species: 38
#>       subspecies: 2
#>         variety: 3
#> 
#> 
```
