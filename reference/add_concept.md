# Add new taxonomic concepts into taxlist objects

Alternative methods to add new concepts into existing `taxlist` objects.

## Usage

``` r
add_concept(taxlist, TaxonName, ...)

# S4 method for class 'taxlist,data.frame'
add_concept(taxlist, TaxonName, ...)

# S4 method for class 'taxlist,character'
add_concept(taxlist, TaxonName, ...)

# S4 method for class 'taxlist,taxlist'
add_concept(taxlist, TaxonName, insert_view = FALSE, ...)

update_concept(taxlist, ConceptID, ...)
```

## Arguments

- taxlist:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object.

- TaxonName:

  Character vector with the accepted name for the new taxon concepts.

- ...:

  Further arguments passed among methods.

- insert_view:

  A numeric (integer) vector, indicating the views to be inserted in
  `taxlist` or the value `TRUE` (see details).

- ConceptID:

  Concept IDs to be updated.
