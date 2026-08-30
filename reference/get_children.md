# Retrieve children or parents of taxon concepts

Retrieve all children or all parents of a queried taxon concept.

## Usage

``` r
get_children(taxlist, ...)

# S3 method for class 'taxlist'
get_children(taxlist, ConceptID, ...)

get_parents(taxlist, ...)

# S3 method for class 'taxlist'
get_parents(taxlist, ConceptID, ...)
```

## Arguments

- taxlist:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object.

- ...:

  Further arguments passed among methods.

- ConceptID:

  Concept IDs for selecting parents or children or a subset of
  `taxlist`.

## Value

A
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object with a subset including requested concepts with children or
parents.

## Details

This function produces subsets of
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects including all children or parents of queried taxon concepts.
Multiple concepts can be queried in these function. The argument
`ConceptID` can be a vector of concept IDs or a subset of the input
`taxlist` object.

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Subset with family Ebenaceae and children
Ebenaceae <- subset(x = Easplist, subset = TaxonName == "Ebenaceae")
Ebenaceae
#> object size: 6.7 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 1 
#> number of taxon concepts: 1 
#> trait entries: 0 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with rank information: 1 
#> concepts without rank information: 0 
#> 
#> family: 1
#>   genus: 0
#>     complex: 0
#>       species: 0
#>         subspecies: 0
#>           variety: 0
#>             form: 0
#> 
#> 

Ebenaceae <- get_children(Easplist, Ebenaceae)
Ebenaceae
#> object size: 8.5 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 10 
#> number of taxon concepts: 9 
#> trait entries: 0 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 8 
#> concepts with children: 3 
#> 
#> concepts with rank information: 9 
#> concepts without rank information: 0 
#> 
#> family: 1
#>   genus: 2
#>     complex: 0
#>       species: 6
#>         subspecies: 0
#>           variety: 0
#>             form: 0
#> 
#> 

## Get parents of Diospyros tricolor
Diostri <- subset(x = Easplist, subset = TaxonConceptID == 52403,
    slot = "relations")
Diostri
#> object size: 6.7 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 1 
#> number of taxon concepts: 1 
#> trait entries: 0 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with rank information: 1 
#> concepts without rank information: 0 
#> 
#> family: 0
#>   genus: 0
#>     complex: 0
#>       species: 1
#>         subspecies: 0
#>           variety: 0
#>             form: 0
#> 
#> 

Diostri <- get_parents(Easplist, Diostri)
Diostri
#> object size: 7.1 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 3 
#> number of taxon concepts: 3 
#> trait entries: 0 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 2 
#> concepts with children: 2 
#> 
#> concepts with rank information: 3 
#> concepts without rank information: 0 
#> 
#> family: 1
#>   genus: 1
#>     complex: 0
#>       species: 1
#>         subspecies: 0
#>           variety: 0
#>             form: 0
#> 
#> 
```
