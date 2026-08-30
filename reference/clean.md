# Delete orphaned records

Manipulation of slots may generate orphaned entries in
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects. The function `clean` deletes such entries and restores the
consistency of the objects.

## Usage

``` r
clean(object, ...)

# S4 method for class 'taxlist'
clean(object, times = 2, ...)
```

## Arguments

- object:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object.

- ...:

  Further arguments passed from or to other methods.

- times:

  An integer indicating how many times the cleaning should be repeated.

## Value

A clean
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object.

## Details

Cleaning of objects will follow the deletion of orphaned names, orphaned
taxon trait entries, and orphaned parent entries.

## Author

Miguel Alvarez.

## Examples

``` r
## Direct manipulation of slot taxonRelations generates an invalid object
Easplist@taxonRelations <- Easplist@taxonRelations[1:5, ]

## Now apply cleaning
Easplist <- clean(Easplist)
summary(Easplist)
#> object size: 7.8 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 7 
#> number of taxon concepts: 5 
#> trait entries: 0 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with rank information: 5 
#> concepts without rank information: 0 
#> 
#> family: 0
#>   genus: 0
#>     complex: 0
#>       species: 5
#>         subspecies: 0
#>           variety: 0
#>             form: 0
#> 
#> 
```
