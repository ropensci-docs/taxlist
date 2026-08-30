# Handle information on taxon usage names.

The slot `taxonNames` in
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects contains taxon usage names for the respective taxon. These
functions assist on the access and modification of entries for names.

## Usage

``` r
taxon_names(taxlist, ...)

# S3 method for class 'taxlist'
taxon_names(taxlist, ...)

taxon_names(taxlist, ...) <- value

# S3 method for class 'taxlist'
taxon_names(taxlist, ...) <- value

add_synonym(taxlist, ...)

# S3 method for class 'taxlist'
add_synonym(taxlist, ConceptID, TaxonName, AuthorName, ...)

update_name(taxlist, ...)

# S3 method for class 'taxlist'
update_name(taxlist, UsageID, ...)

delete_name(taxlist, ...)

# S3 method for class 'taxlist'
delete_name(taxlist, UsageID, ...)
```

## Arguments

- taxlist:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object to be modified.

- ...:

  Further arguments passed among methods. In `update_name` are vectors
  including the variables to be updated for the respective taxon usage
  ID.

- value:

  A data frame used as new slot `taxonNames` in `taxlist`.

- ConceptID:

  Numeric vector indicating the concept ID to which the synonyms will be
  added.

- TaxonName, AuthorName:

  Character values used for the new names (synonyms).

- UsageID:

  Numeric vector indicating the taxon usage IDs to be updated.

## Value

A data frame or, in the case of the replacement method, a
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object with modified slot `taxonNames`.

## Details

The replacement method `taxon_names<-` is a quick alternative to include
names in empty
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects.

The function `add_synonym()` works only for adding names to existing
taxon concepts. For adding new taxon concepts as well you should use
[`add_concept()`](https://docs.ropensci.org/taxlist/reference/add_concept.md).

## See also

[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Display of slot 'taxonNames'
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
taxon_names(Euclea)
#>      TaxonUsageID TaxonConceptID                       TaxonName
#> 297           269            269                Euclea divinorum
#> 298         50787            269 Euclea divinorum ssp. keniensis
#> 5043        55709          55707                          Euclea
#>              AuthorName
#> 297               Hiern
#> 298  (R. E. Fr.) de Wit
#> 5043                   

## Insert a synonym to Diospyros scabra
summary(Easplist, "Diospyros scabra")
#> ------------------------------ 
#> concept ID: 51793 
#> view ID: 1 
#> level: species 
#> parent: 55171 Diospyros L. 
#> 
#> # accepted name: 
#> 51793 Diospyros scabra (Chiov.) Cufod. 
#> ------------------------------
sp_list <- add_synonym(taxlist = Easplist, ConceptID = 51793,
  TaxonName = "Maba scabra", AuthorName = "Chiov.")
summary(sp_list, "Diospyros scabra")
#> ------------------------------ 
#> concept ID: 51793 
#> view ID: 1 
#> level: species 
#> parent: 55171 Diospyros L. 
#> 
#> # accepted name: 
#> 51793 Diospyros scabra (Chiov.) Cufod. 
#> 
#> # synonyms (1): 
#> 56139 Maba scabra Chiov. 
#> ------------------------------

## Delete a synonym of Launaea cornuta
summary(sp_list, "Launaea cornuta")
#> ------------------------------ 
#> concept ID: 355 
#> view ID: 1 
#> level: species 
#> parent: 54923 Launaea Cass. 
#> 
#> # accepted name: 
#> 355 Launaea cornuta (Hochst. ex Oliv. & Hiern) C. Jeffrey 
#> 
#> # synonyms (2): 
#> 53821 Sonchus exauriculatus (Oliv. & Hiern) O. Hoffm. 
#> 53843 Sonchus bipontini var. pinnatifidus Oliv. & Hiern 
#> ------------------------------
sp_list <- delete_name(sp_list, 53821)
summary(sp_list, "Launaea cornuta")
#> ------------------------------ 
#> concept ID: 355 
#> view ID: 1 
#> level: species 
#> parent: 54923 Launaea Cass. 
#> 
#> # accepted name: 
#> 355 Launaea cornuta (Hochst. ex Oliv. & Hiern) C. Jeffrey 
#> 
#> # synonyms (1): 
#> 53843 Sonchus bipontini var. pinnatifidus Oliv. & Hiern 
#> ------------------------------

## Hypothetical correction in author name in Launaea cornuta
sp_list <- update_name(taxlist = sp_list, UsageID = 355, AuthorName = "L.")
summary(sp_list, "Launaea cornuta")
#> ------------------------------ 
#> concept ID: 355 
#> view ID: 1 
#> level: species 
#> parent: 54923 Launaea Cass. 
#> 
#> # accepted name: 
#> 355 Launaea cornuta L. 
#> 
#> # synonyms (1): 
#> 53843 Sonchus bipontini var. pinnatifidus Oliv. & Hiern 
#> ------------------------------
```
