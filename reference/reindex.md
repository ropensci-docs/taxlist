# Re-index elements of taxlist objects

The assignment of new identifiers must take into account all possible
occurrences of such indices in
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects in order to maintain their validity.

## Usage

``` r
reindex(object, ...)

# S3 method for class 'taxlist'
reindex(object, old, new, idx = "TaxonConceptID", ...)

reindex(object, ...) <- value

# S3 method for class 'taxlist'
reindex(object, ...) <- value
```

## Arguments

- object:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object.

- ...:

  Further arguments to be passed among methods.

- old:

  A vector with old identifiers to be re-indized. This may contain all
  identifiers or only a part of them. If only a part, the rest of
  indices will be preserved. If the changes insert duplicated
  identifiers, an error message will be retrieved. If missing, all
  identifiers in `'object'` will be considered.

- new, value:

  A vector with the new identifiers. It has to be of the same length as
  `'old'`.

- idx:

  Name of the index to be changed, which means `"TaxonConceptID"`,
  `"TaxonUsageID"`, or `"ViewID"` for taxon concepts, taxon usage names,
  or taxon views, respectively. You can also use the aliases
  `"concept"`, `"usage"`, and `"view"`.

## Value

An object of class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
with modified identifiers.

## Examples

``` r
## Copy taxonomic list
sp_list <- Easplist
summary(sp_list, "papyrus")
#> ------------------------------ 
#> concept ID: 206 
#> view ID: 1 
#> level: species 
#> parent: 54853 Cyperus L. 
#> 
#> # accepted name: 
#> 206 Cyperus papyrus L. 
#> 
#> # synonyms (2): 
#> 52612 Cyperus papyrus ssp. antiquorum (Willd.) Chiov. 
#> 52613 Cyperus papyrus ssp. nyassicus Chiov. 
#> ------------------------------

## Re-index taxon concepts
reindex(sp_list) <- id_generator(nrow(sp_list@taxonRelations),
    mode = "character")

## Re-index taxon usage names
reindex(sp_list, idx = "TaxonUsageID") <- id_generator(nrow(sp_list@taxonNames),
    mode = "character")

## Re-index taxon views
reindex(sp_list, idx = "ViewID") <- id_generator(nrow(sp_list@taxonViews),
    mode = "character")

## Check result
validObject(sp_list)
#> [1] TRUE
summary(sp_list, "papyrus")
#> ------------------------------ 
#> concept ID: rHXCwew44L 
#> view ID: N9aUiE0CqO 
#> level: species 
#> parent: g5SrYoV6Aa Cyperus L. 
#> 
#> # accepted name: 
#> 4QVLsD2o82 Cyperus papyrus L. 
#> 
#> # synonyms (2): 
#> bd312F8F1d Cyperus papyrus ssp. antiquorum (Willd.) Chiov. 
#> 2AoWYUWb4O Cyperus papyrus ssp. nyassicus Chiov. 
#> ------------------------------
```
