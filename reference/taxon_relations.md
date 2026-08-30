# Retrieve or replace slot taxonRelations in taxlist objects

Retrieve the content of slot `taxonRelations` from a
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object or replace it by a new data frame.

## Usage

``` r
taxon_relations(taxlist, ...)

# S3 method for class 'taxlist'
taxon_relations(taxlist, ...)

taxon_relations(taxlist, ...) <- value

# S3 method for class 'taxlist'
taxon_relations(taxlist, ...) <- value

# S4 method for class 'taxlist,numeric'
update_concept(taxlist, ConceptID, ...)
```

## Arguments

- taxlist:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object.

- ...:

  Further arguments passed among methods.

- value:

  A `data.frame` object to be set as slot `taxonRelations`.

- ConceptID:

  Concept IDs to be updated.

## Value

An object of class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
with added names and concepts.

## Details

The replacement method `taxon_relations<-` should be only used when
constructing
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects from an empty one (prototype).

New concepts should be first added to a
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object using their respective accepted names. Synonyms can be further
provided using the function
[`add_synonym()`](https://docs.ropensci.org/taxlist/reference/taxon_names.md).

Additional named vectors can be provided to be included in slot
`taxonNames`, in the cases where those variables already exist,
otherwise they will be ignored.

It is recommended also to provide a concept view as `ViewID` (see
[`taxon_views()`](https://docs.ropensci.org/taxlist/reference/taxon_views.md)).
For adding a new view, use
[`add_view()`](https://docs.ropensci.org/taxlist/reference/taxon_views.md).

## See also

[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Subset for the genus Euclea and display of slot 'taxonNames'
Euclea <- subset(x = Easplist, subset = charmatch("Euclea", TaxonName),
  slot = "names", keep_children = TRUE)
Euclea
#> object size: 7 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 3 
#> number of taxon concepts: 2 
#> trait entries: 0 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 1 
#> concepts with children: 1 
#> 
#> concepts with rank information: 2 
#> concepts without rank information: 0 
#> 
#> family: 0
#>   genus: 1
#>     complex: 0
#>       species: 1
#>         subspecies: 0
#>           variety: 0
#>             form: 0
#> 
#> 
taxon_relations(Euclea)
#>      TaxonConceptID AcceptedName Basionym Parent   Level ViewID
#> 267             269          269       NA  55707 species      1
#> 3537          55707        55709       NA     NA   genus     NA
```
