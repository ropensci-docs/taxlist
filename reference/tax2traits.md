# Set taxonomic information as taxon traits

Taxonomic classification can be included in
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects within the information provided at slot `taxonRelations`.
Nevertheless, for statistical analyses it may be more convenient to
insert such information in the slot `taxonTraits`.

## Usage

``` r
tax2traits(object, ...)

# S3 method for class 'taxlist'
tax2traits(object, get_names = FALSE, ...)
```

## Arguments

- object:

  An object of class
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

- ...:

  Further arguments to be passed among methods.

- get_names:

  Logical value indicating whether taxon names should be retrieved
  instead of taxon IDs.

## Value

An object of class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
with taxonomy added as traits.

## Details

This function can only be applied to objects containing parent-child
relationships and information on taxonomic levels.

## Author

Miguel Alvarez <kamapu78@gmail.com>.

## Examples

``` r
## Family Acanthaceae with children
Acanthaceae <- subset(x = Easplist, subset = TaxonName == "Acanthaceae",
  slot = "names", keep_children = TRUE)
summary(Acanthaceae)
#> object size: 29.9 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 143 
#> number of taxon concepts: 113 
#> trait entries: 9 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 112 
#> concepts with children: 28 
#> 
#> concepts with rank information: 113 
#> concepts without rank information: 0 
#> 
#> family: 1
#>   genus: 23
#>     complex: 0
#>       species: 84
#>         subspecies: 3
#>           variety: 2
#>             form: 0
#> 
#> 

## Insert taxonomy to taxon traits
Acanthaceae <- tax2traits(Acanthaceae, get_names = TRUE)
head(taxon_traits(Acanthaceae))
#>     TaxonConceptID       life_form variety subspecies               species
#> 14              59 obligate_annual    <NA>       <NA>   Asystasia gangetica
#> 15              60 obligate_annual    <NA>       <NA>  Asystasia mysurensis
#> 97             319 obligate_annual    <NA>       <NA> Hygrophila auriculata
#> 108            341    phanerophyte    <NA>       <NA>     Justicia betonica
#> 238          50264  climbing_plant    <NA>       <NA>      Thunbergia alata
#> 241          50423    phanerophyte    <NA>       <NA>    Hypoestes aristata
#>          genus      family
#> 14   Asystasia Acanthaceae
#> 15   Asystasia Acanthaceae
#> 97  Hygrophila Acanthaceae
#> 108   Justicia Acanthaceae
#> 238 Thunbergia Acanthaceae
#> 241  Hypoestes Acanthaceae
```
