# Search matchings between character and taxlist objects

Names provided in a character vector will be compared with names stored
in slot `taxonNames` within an object of class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
by using the function
[`stringdist::stringsim()`](https://rdrr.io/pkg/stringdist/man/stringsim.html).

## Usage

``` r
match_names(x, object, ...)

# S4 method for class 'character,character'
match_names(
  x,
  object,
  UsageID,
  best = 1,
  nomatch = TRUE,
  method = "lcs",
  cutlevel = NULL,
  ...
)

# S4 method for class 'character,missing'
match_names(x, best, cutlevel, nomatch = TRUE, ...)

# S4 method for class 'character,taxlist'
match_names(
  x,
  object,
  show_concepts = FALSE,
  accepted_only = FALSE,
  include_author = FALSE,
  ...
)
```

## Arguments

- x:

  A character vector with names to be compared.

- object:

  Either a character vector or a
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object containing the taxonomic list for comparison. If missing, the
  similarity of each name in 'x' will be compared with the rest of the
  names in the same vector.

- ...:

  Further arguments passed among methods.

- UsageID:

  A vector with IDs for single usage names in the compared list. If the
  IDs are duplicated or not as much as names in 'object', the function
  retrieves an error message. If missing, this function will number
  every name anew (see column 'TaxonUsageID' in the output object).

- best:

  Integer value indicating how many matches should be displayed in the
  output. Matches with the same value of similarity will be considered
  as one. Note that this argument will be overrode by 'cutlevel'.

- nomatch:

  A logical value indicating wheter names without matches should be
  included in the output (`'nomatch = TRUE'`) or not
  (`'nomatch = FALSE'`).

- method:

  Further arguments passed to
  [`stringdist::stringsim()`](https://rdrr.io/pkg/stringdist/man/stringsim.html).

- cutlevel:

  A numeric value indicating a cut level of similarity, considering as
  match names with similarities equal or bigger than the cut value. This
  argument overrides 'best'.

- show_concepts:

  Logical value indicating whether the respective taxon concepts should
  be displayed in output or not.

- accepted_only:

  Logical value indicating whether only accepted names should be matched
  or all usage names (including synonyms).

- include_author:

  A logical value indicating whether the author name in object (method
  for
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md))
  should be included in the matching list or not.

## See also

[`stringdist::stringsim()`](https://rdrr.io/pkg/stringdist/man/stringsim.html)

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Names to be compared
species <- c("Cyperus papyrus", "Typha australis", "Luke Skywalker")

## Comparing character vectors
match_names(c("Cyperus paper", "TIE fighter"), species)
#>   idx submittedname TaxonUsageID       TaxonName match similarity
#> 1   1 Cyperus paper            1 Cyperus papyrus     1  0.8571429
#> 2   2   TIE fighter            2 Typha australis     1  0.3076923

## Retrieve taxon usage names
match_names(species, Easplist)
#>   idx   submittedname TaxonUsageID           TaxonName
#> 1   1 Cyperus papyrus          206     Cyperus papyrus
#> 2   2 Typha australis        51999     Typha australis
#> 3   3  Luke Skywalker        51565 Loudetia kagerensis
#>                         AuthorName match similarity
#> 1                               L.     1  1.0000000
#> 2                        Schumach.     1  1.0000000
#> 3 (K. Schum.) C.E. Hubb. ex Hutch.     1  0.4848485

## Display accepted names in output
match_names(x = species, object = Easplist, show_concepts = TRUE)
#>   idx   submittedname TaxonUsageID           TaxonName
#> 1   1 Cyperus papyrus          206     Cyperus papyrus
#> 2   2 Typha australis        51999     Typha australis
#> 3   3  Luke Skywalker        51565 Loudetia kagerensis
#>                         AuthorName match similarity TaxonConceptID
#> 1                               L.     1  1.0000000            206
#> 2                        Schumach.     1  1.0000000          50105
#> 3 (K. Schum.) C.E. Hubb. ex Hutch.     1  0.4848485          51565
#>     AcceptedTaxonName               AcceptedAuthorName   Level
#> 1     Cyperus papyrus                               L. species
#> 2   Typha domingensis                            Pers. species
#> 3 Loudetia kagerensis (K. Schum.) C.E. Hubb. ex Hutch. species

# Using cut value for similarity
match_names(x = species, object = Easplist, cutlevel = 0.8)
#>   idx   submittedname TaxonUsageID       TaxonName AuthorName match similarity
#> 1   1 Cyperus papyrus          206 Cyperus papyrus         L.     1  1.0000000
#> 2   2 Typha australis        51999 Typha australis  Schumach.     1  1.0000000
#> 3   2 Typha australis        53125  Typha aequalis   Schnizl.     2  0.8275862
#> 4   3  Luke Skywalker           NA            <NA>       <NA>     0         NA
```
