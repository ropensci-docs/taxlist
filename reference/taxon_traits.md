# Manipulation of taxon traits in taxlist objects.

The slot `taxonTraits` in
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects contains attributes of taxon concepts (e.g. functional traits).
These functions are suitable for replacing, retrieving and appending
trait information in taxonomic lists.

## Usage

``` r
taxon_traits(taxlist, ...)

# S3 method for class 'taxlist'
taxon_traits(taxlist, ...)

taxon_traits(taxlist, ...) <- value

# S3 method for class 'taxlist'
taxon_traits(taxlist, ...) <- value

update_trait(taxlist, ...)

# S3 method for class 'taxlist'
update_trait(taxlist, taxonTraits, ...)
```

## Arguments

- taxlist:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object.

- ...:

  Further arguments to be passed among methods.

- value:

  Data frame to be set as slot `taxonTraits`.

- taxonTraits:

  a data frame with taxon traits to be inserted in `'taxlist'`. A column
  `'TaxonConceptID'` is mandatory in this table. If some taxon concept
  IDs are not occurring in `'taxlist'`, an error message is retrieved by
  `update_trait()`.

## Details

Taxon traits are contained in a data frame at the slot `taxonTraits` in
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects. To optimise space, this data frame contain only entries for
those concepts with information, while taxa with no information are
skipped from this table. Thus appending new variables may also have to
include new rows in this slot, which is automatically carried out by
this function.

The replacement method `taxon_traits<-` should be only used when
constructing
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects from an empty one.

## See also

[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Displaying taxon traits
head(taxon_traits(Easplist))
#>   TaxonConceptID          life_form
#> 1              7       phanerophyte
#> 2              9       phanerophyte
#> 3             18 facultative_annual
#> 4             20 facultative_annual
#> 5             21    obligate_annual
#> 6             22        chamaephyte

## Updating traits for Launaea cornuta
summary(Easplist, "Launaea cornuta")
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
accepted_name(taxlist = Easplist, ConceptID = 355, show_traits = TRUE)
#>   TaxonConceptID TaxonUsageID       TaxonName
#> 1            355          355 Launaea cornuta
#>                              AuthorName ViewID   Level     life_form
#> 1 (Hochst. ex Oliv. & Hiern) C. Jeffrey      1 species tussock_plant

sp_list <- update_trait(taxlist = Easplist, taxonTraits = data.frame(
        TaxonConceptID = 355,
        life_form = "annual"))
accepted_name(taxlist = sp_list, ConceptID = 355, show_traits = TRUE)
#>   TaxonConceptID TaxonUsageID       TaxonName
#> 1            355          355 Launaea cornuta
#>                              AuthorName ViewID   Level life_form
#> 1 (Hochst. ex Oliv. & Hiern) C. Jeffrey      1 species    annual
```
