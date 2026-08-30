# Management of concept views in taxonomic lists.

Retrieve or replace slot `taxonViews` in an object of class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)

## Usage

``` r
taxon_views(taxlist, ...)

# S3 method for class 'taxlist'
taxon_views(taxlist, ...)

taxon_views(taxlist, ...) <- value

# S3 method for class 'taxlist'
taxon_views(taxlist, ...) <- value

add_view(taxlist, taxonViews, ...)

# S4 method for class 'taxlist,data.frame'
add_view(taxlist, taxonViews, ...)
```

## Arguments

- taxlist:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object.

- ...:

  Further arguments to be passed among methods.

- value:

  An object of class
  [data.frame](https://rdrr.io/r/base/data.frame.html) containing the
  references used to define the circumscription of taxon concepts
  included in `taxlist`.

- taxonViews:

  A data frame with taxon views to be inserted in `'taxlist'`.

## Value

An object of class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
with added views.

## Details

Taxon views indicate in
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects the references determining the circumscription of the respective
taxon concepts. When adding a new concept (see
[`add_concept()`](https://docs.ropensci.org/taxlist/reference/add_concept.md)),
the respective reference may not yet occur in the input
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object.

The term taxon view was introduced by **Zhong et al. (1996)** and
corresponds to the reference used for the definition of a concept.

This function retrieves the slot `taxonViews` from objects of the class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

The replacement method `taxon_views<-` replaces the whole content of
slot `taxonViews` and it is only recommended to use when constructing a
new
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object from an empty prototype.

## References

**Zhong Y, Jung S, Pramanik S, Beaman JH (1996).** Data model and
comparison and query methods for interacting classifications in a
taxonomic database. *Taxon* 45: 223–241.
[doi:10.1093/bioinformatics/15.2.149](https://doi.org/10.1093/bioinformatics/15.2.149)

## See also

[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## See existing views
taxon_views(Easplist)
#>   ViewID                                 secundum view_bibtexkey
#> 1      1            African Plant Database (2012)  CJBGSANBI2012
#> 2      2 Taxonomic Name Resolution Service (2018)       TNRS2018
#> 3      3                    The Plant List (2013)        TPL2013

## Add a new view
sp_list <- add_view(taxlist = Easplist, taxonViews = data.frame(
        secundum = "Beentje et al. (1952)",
        Title = "Flora of Tropical East Africa",
        URL = "http://www.kew.org/science/directory/projects/FloraTropEAfrica.html"))

taxon_views(sp_list)
#>   ViewID                                 secundum view_bibtexkey
#> 1      1            African Plant Database (2012)  CJBGSANBI2012
#> 2      2 Taxonomic Name Resolution Service (2018)       TNRS2018
#> 3      3                    The Plant List (2013)        TPL2013
#> 4      4                    Beentje et al. (1952)           <NA>
#>                           Title
#> 1                          <NA>
#> 2                          <NA>
#> 3                          <NA>
#> 4 Flora of Tropical East Africa
#>                                                                   URL
#> 1                                                                <NA>
#> 2                                                                <NA>
#> 3                                                                <NA>
#> 4 http://www.kew.org/science/directory/projects/FloraTropEAfrica.html
```
