# An S4 class to represent taxonomic lists.

Class for taxonomic lists including synonyms, hierarchical ranks,
parent-child relationships, taxon views and taxon traits.

Note that each taxon becomes an identifier, represented by the column
**TaxonConceptID** in the slot **taxonRelations**, analogous to a
primary key in a relational database. This identifier is restricted to
an integer in `taxlist` and is specific for the object.

In the same way, each taxon usage name has an identifier in the column
**TaxonUsageID**, slot **taxonNames**. The column **ViewID** in slot
**taxonViews** is the identifier of the taxon view.

## Slots

- `taxonNames`:

  (`data.frame`) Table of taxon usage names (accepted names and
  synonyms).

- `taxonRelations`:

  (`data.frame`) Relations between concepts, accepted names, basionyms,
  parents and hierarchical level.

- `taxonTraits`:

  Table of taxon traits.

- `taxonViews`:

  References used to determine the respective concept circumscription.

## References

**Alvarez M, Luebert F (2018).** The taxlist package: managing plant
taxonomic lists in R. *Biodiversity Data Journal* 6: e23635.
[doi:10.3897/bdj.6.e23635](https://doi.org/10.3897/bdj.6.e23635)

## Author

Miguel Alvarez

## Examples

``` r
## Class 'taxlist'
showClass("taxlist")
#> Class "taxlist" [package "taxlist"]
#> 
#> Slots:
#>                                                                   
#> Name:      taxonNames taxonRelations     taxonViews    taxonTraits
#> Class:     data.frame     data.frame      df.lib_df     data.frame

## Create an empty object
sp_list <- new("taxlist")
sp_list
#> object size: 5.1 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 0 
#> number of taxon concepts: 0 
#> trait entries: 0 
#> number of trait variables: 0 
#> taxon views: 0 
#> 
```
