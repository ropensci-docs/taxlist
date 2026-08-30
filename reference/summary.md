# Print overviews for taxlist Objects and their content

A method to display either an overview of the content of
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects or an overview of selected taxa.

## Usage

``` r
# S4 method for class 'taxlist'
summary(
  object,
  ConceptID,
  units = "Kb",
  check_validity = TRUE,
  display = "both",
  maxsum = 5,
  secundum = NULL,
  exact = FALSE,
  ...
)

# S4 method for class 'taxlist'
show(object)

# S4 method for class 'taxlist'
print(x, ...)
```

## Arguments

- object, x:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object.

- ConceptID:

  IDs of concepts to be displayed in the summary.

- units:

  Character value indicating the units shown in the object's allocated
  space.

- check_validity:

  Logical value indicating whether the validity of `object` should be
  checked or not.

- display:

  Character value indicating the field to be displayed (see details).

- maxsum:

  Integer indicating the maximum number of displayed taxa.

- secundum:

  A character value indicating the column from slot`taxonViews` to be
  displayed in the summary.

- exact:

  A logical value indicating whether taxon names should match the exact
  argument in parameter 'ConceptID'. It works only if 'ConceptID' is
  provided as character value and is not the keyword 'all'.

- ...:

  Further arguments passed to or from another methods.

## Details

A general overview indicating number of names, concepts and taxon views
included in
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects. If argument `ConceptID` is a vector with concept IDs or names
to be matched by [`grepl()`](https://rdrr.io/r/base/grep.html), then a
display of all names included in each concept will be produced.
Alternative you can use `taxon="all"` in order to get the listing of
names for all concepts included in the object (truncated to the input
number of `maxsum`).

For summaries applied to concepts, there are three alternative displays
of names using the argument `display`. Use `display="name"` to show the
value `TaxonName`, `display="author"` to show the value `AuthorName` or
`display="both"` to show both values. Such values are taken from slot
`taxonNames`.

For big objects it will be recommended to set `units="Mb"` (see also
[`object.size()`](https://rdrr.io/r/utils/object.size.html) for further
alternatives).

## See also

[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## summary of the object
summary(Easplist, units = "Mb")
#> object size: 0.7 Mb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 5393 
#> number of taxon concepts: 3887 
#> trait entries: 311 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 3698 
#> concepts with children: 1343 
#> 
#> concepts with rank information: 3887 
#> concepts without rank information: 0 
#> 
#> family: 186
#>   genus: 1011
#>     complex: 1
#>       species: 2521
#>         subspecies: 71
#>           variety: 95
#>             form: 2
#> 
#> 

## the same output
summary(Easplist)
#> object size: 761.4 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 5393 
#> number of taxon concepts: 3887 
#> trait entries: 311 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 3698 
#> concepts with children: 1343 
#> 
#> concepts with rank information: 3887 
#> concepts without rank information: 0 
#> 
#> family: 186
#>   genus: 1011
#>     complex: 1
#>       species: 2521
#>         subspecies: 71
#>           variety: 95
#>             form: 2
#> 
#> 
show(Easplist)
#> object size: 761.4 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 5393 
#> number of taxon concepts: 3887 
#> trait entries: 311 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 3698 
#> concepts with children: 1343 
#> 
#> concepts with rank information: 3887 
#> concepts without rank information: 0 
#> 
#> family: 186
#>   genus: 1011
#>     complex: 1
#>       species: 2521
#>         subspecies: 71
#>           variety: 95
#>             form: 2
#> 
#> 
print(Easplist)
#> object size: 761.4 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 5393 
#> number of taxon concepts: 3887 
#> trait entries: 311 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 3698 
#> concepts with children: 1343 
#> 
#> concepts with rank information: 3887 
#> concepts without rank information: 0 
#> 
#> family: 186
#>   genus: 1011
#>     complex: 1
#>       species: 2521
#>         subspecies: 71
#>           variety: 95
#>             form: 2
#> 
#> 
Easplist
#> object size: 761.4 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 5393 
#> number of taxon concepts: 3887 
#> trait entries: 311 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 3698 
#> concepts with children: 1343 
#> 
#> concepts with rank information: 3887 
#> concepts without rank information: 0 
#> 
#> family: 186
#>   genus: 1011
#>     complex: 1
#>       species: 2521
#>         subspecies: 71
#>           variety: 95
#>             form: 2
#> 
#> 

## summary for two taxa
summary(Easplist, c(51128, 51140))
#> ------------------------------ 
#> concept ID: 51128 
#> view ID: 1 
#> level: species 
#> parent: 54818 Cheilanthes Sw. 
#> 
#> # accepted name: 
#> 51128 Cheilanthes quadripinnata Kuhn 
#> 
#> # synonyms (1): 
#> 51129 Pellaea quadripinnata (Forssk.) Prantl 
#> ------------------------------ 
#> concept ID: 51140 
#> view ID: 1 
#> level: species 
#> parent: 55364 Haplopteris C. Presl 
#> 
#> # accepted name: 
#> 51140 Haplopteris volkensii (Hieron.) E.H. Crane 
#> 
#> # synonyms (1): 
#> 51141 Vittaria volkensii Hieron. 
#> ------------------------------

## summary by matching a name
summary(Easplist, "Acmella")
#> ------------------------------ 
#> concept ID: 20 
#> view ID: 1 
#> level: species 
#> parent: 54760 Acmella Pers. 
#> 
#> # accepted name: 
#> 20 Acmella caulirhiza Delile 
#> 
#> # synonyms (19): 
#> 50001 Spilanthes mauritiana (A. Rich. ex Pers.) DC. 
#> 52448 Spilanthes caulirhiza (Delile) DC. 
#> 52449 Acmella mauritiana A. Rich. ex Pers. 
#> 52450 Spilanthes africana DC. 
#> 52451 Spilanthes abyssinica Sch. Bip. ex A. Rich. 
#> 52452 Eclipta filicaulis Schumach. & Thonn. 
#> 52453 Spilanthes filicaulis (Schumach. & Thonn.) C. D. Adams 
#> 52454 Spilanthes acmella var. acmella (L.) Murray 
#> 52455 Verbesina acmella L. 
#> 52456 Spilanthes acmella (L.) Murray 
#> 52457 Blainvillea acmella (L.) Philipson 
#> 52458 Eclipta latifolia L. f. 
#> 52459 Blainvillea latifolia (L. f.) DC. 
#> 52460 Blainvillea rhomboidea Cass. 
#> 52461 Blainvillea dalla-vedovae A. Terracc. 
#> 52462 Verbesina dichotoma Murray 
#> 52463 Blainvillea dichotoma (Murray) Stewart 
#> 52464 Spilanthes caulirhiza var. madagascariensis DC. 
#> 52465 Spilanthes mauritiana f. madagascariensis (DC.) A. H. Moore 
#> ------------------------------ 
#> concept ID: 21 
#> view ID: 1 
#> level: species 
#> parent: 54760 Acmella Pers. 
#> 
#> # accepted name: 
#> 21 Acmella uliginosa (Sw.) Cass. 
#> 
#> # synonyms (1): 
#> 50002 Spilanthes uliginosa Sw. 
#> ------------------------------ 
#> concept ID: 54760 
#> view ID: 2 
#> level: genus 
#> parent: 55936 Compositae Giseke 
#> 
#> # accepted name: 
#> 54762 Acmella Pers. 
#> ------------------------------

## summary for the first 10 taxa
summary(object = Easplist, ConceptID = "all", maxsum = 10)
#> ------------------------------ 
#> concept ID: 1 
#> view ID: 1 
#> level: species 
#> parent: 54753 Abelmoschus Medik. 
#> 
#> # accepted name: 
#> 1 Abelmoschus esculentus (L.) Moench 
#> 
#> # synonyms (1): 
#> 52313 Hibiscus esculentus L. 
#> ------------------------------ 
#> concept ID: 2 
#> view ID: 1 
#> level: species 
#> parent: 54754 Abutilon Mill. 
#> 
#> # accepted name: 
#> 2 Abutilon indicum (L.) 
#> ------------------------------ 
#> concept ID: 3 
#> view ID: 1 
#> level: species 
#> parent: 54754 Abutilon Mill. 
#> 
#> # accepted name: 
#> 3 Abutilon mauritianum (Jacq.) Medik. 
#> 
#> # synonyms (1): 
#> 50361 Pavonia patens (Andrews) Chiov. 
#> ------------------------------ 
#> concept ID: 4 
#> view ID: 1 
#> level: species 
#> parent: 54755 Acacia Mill. 
#> 
#> # accepted name: 
#> 4 Acacia drepanolobium Harms ex Y. Sjöstedt 
#> ------------------------------ 
#> concept ID: 5 
#> view ID: 1 
#> level: species 
#> parent: 54755 Acacia Mill. 
#> 
#> # accepted name: 
#> 5 Acacia elatior Brenan 
#> ------------------------------ 
#> concept ID: 6 
#> view ID: 1 
#> level: species 
#> parent: 54755 Acacia Mill. 
#> 
#> # accepted name: 
#> 6 Acacia kirkii Oliv. 
#> ------------------------------ 
#> concept ID: 7 
#> view ID: 1 
#> level: species 
#> parent: 54755 Acacia Mill. 
#> 
#> # accepted name: 
#> 7 Acacia mearnsii De Wild. 
#> ------------------------------ 
#> concept ID: 8 
#> view ID: 1 
#> level: species 
#> parent: 54755 Acacia Mill. 
#> 
#> # accepted name: 
#> 8 Acacia mellifera (Vahl) Benth. 
#> ------------------------------ 
#> concept ID: 9 
#> view ID: 1 
#> level: species 
#> parent: 54755 Acacia Mill. 
#> 
#> # accepted name: 
#> 9 Acacia polyacantha Willd. 
#> ------------------------------ 
#> concept ID: 10 
#> view ID: 1 
#> level: species 
#> parent: 54755 Acacia Mill. 
#> 
#> # accepted name: 
#> 10 Acacia reficiens Wawra 
#> ------------------------------
```
