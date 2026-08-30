# Merge concepts or move names

Merge taxon concepts form a
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object into single ones.

## Usage

``` r
merge_taxa(object, ...)

# S3 method for class 'taxlist'
merge_taxa(
  object,
  concepts,
  level = NULL,
  delete_nomatch = FALSE,
  print_output = FALSE,
  ...
)
```

## Arguments

- object, taxlist:

  Object of class
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

- ...:

  Further arguments to be passed to or from other methods.

- concepts:

  Numeric (integer) vector including taxon concepts to be merged.

- level:

  Character vector with queried taxonomic ranks. This setting works only
  if `concepts` are missing. ranks in between will be merged to their
  respective parents by
  [`merge_to_parent()`](https://docs.ropensci.org/taxlist/reference/merge_to_parent.md).
  Non queried ranks as well as rankless concepts will be deleted from
  the output.

- delete_nomatch:

  A logical value indicating whether no matched ranks (i.e. top rank and
  rankless concepts) should be deleted from the output or not.

- print_output:

  Logical value indicating whether the merged concept should be
  displayed in the console. Thi works only if a vector is provided at
  `concepts`.

## Value

An object of class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

## Details

Taxon concepts indicated in argument `concepts` will be merged into a
single concept. The new concept inherits the ID and respective
attributes from slots `taxonRelations` and `taxonTraits` from the first
taxon concept indicated in argument `concepts`.

For convenience the resulting concept can be displayed by setting
`print_output=TRUE` but only when using argument `concepts`.

An alternative application of this function is implemented through the
argument `level`, where all lower rank taxa will be merged to the
indicated level or higher (if parent of merged taxa are at a higher
rank).

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Merge Cyperus papyrus and Cyperus dives
summary(Easplist, c(206, 197))
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
#> concept ID: 197 
#> view ID: 1 
#> level: species 
#> parent: 54853 Cyperus L. 
#> 
#> # accepted name: 
#> 197 Cyperus dives Delile 
#> 
#> # synonyms (5): 
#> 52000 Cyperus immensus C.B. Clarke 
#> 52600 Cyperus exaltatus var. dives (Delile) C.B. Clarke 
#> 52601 Cyperus alopecuroides var. dives Boeckeler 
#> 52602 Cyperus immensus var. petherickii (C.B. Clarke) Kük. 
#> 52603 Cyperus petherickii C.B. Clarke 
#> ------------------------------

merged_cyperus <- merge_taxa(object = Easplist, concepts = c(206, 197),
    print_output = TRUE)
#> ------------------------------ 
#> concept ID: 206 
#> view ID: 1 
#> level: species 
#> parent: 54853 Cyperus L. 
#> 
#> # accepted name: 
#> 206 Cyperus papyrus L. 
#> 
#> # synonyms (8): 
#> 197 Cyperus dives Delile 
#> 52000 Cyperus immensus C.B. Clarke 
#> 52600 Cyperus exaltatus var. dives (Delile) C.B. Clarke 
#> 52601 Cyperus alopecuroides var. dives Boeckeler 
#> 52602 Cyperus immensus var. petherickii (C.B. Clarke) Kük. 
#> 52603 Cyperus petherickii C.B. Clarke 
#> 52612 Cyperus papyrus ssp. antiquorum (Willd.) Chiov. 
#> 52613 Cyperus papyrus ssp. nyassicus Chiov. 
#> ------------------------------

## Subset with Kyllinga species
ky <- subset(Easplist, TaxonName == "Kyllinga", keep_children = TRUE,
    keep_parents = TRUE)
ky
#> object size: 14.3 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 45 
#> number of taxon concepts: 14 
#> trait entries: 8 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 13 
#> concepts with children: 3 
#> 
#> concepts with rank information: 14 
#> concepts without rank information: 0 
#> 
#> family: 1
#>   genus: 1
#>     complex: 0
#>       species: 10
#>         subspecies: 0
#>           variety: 2
#>             form: 0
#> 
#> 
indented_list(ky)
#> Cyperaceae Juss.
#>  Kyllinga Rottb.
#>    Kyllinga alata Nees
#>    Kyllinga brevifolia Rottb.
#>    Kyllinga nemoralis (J.R. Forst. & G. Forst.) Dandy ex Hutch. & Dalziel
#>    Kyllinga pumila Michx.
#>    Kyllinga erecta Schumach.
#>      Kyllinga erecta var. erecta Schumach.
#>      Kyllinga erecta var. africana (Kük.) S.S. Hooper
#>    Kyllinga crassipes Boeckeler
#>    Kyllinga elatior Kunth
#>    Kyllinga odorata Vahl
#>    Kyllinga species 
#>    Kyllinga bulbosa P. Beauv. 

## Merge to species and family
merge_taxa(ky, level = c("species", "family"))
#> object size: 14.2 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 45 
#> number of taxon concepts: 11 
#> trait entries: 8 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 10 
#> concepts with children: 1 
#> 
#> concepts with rank information: 11 
#> concepts without rank information: 0 
#> 
#> family: 1
#>   genus: 0
#>     complex: 0
#>       species: 10
#>         subspecies: 0
#>           variety: 0
#>             form: 0
#> 
#> 

## Merge to variety and genus
merge_taxa(ky, level = c("variety", "genus"))
#> object size: 13.7 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 45 
#> number of taxon concepts: 4 
#> trait entries: 0 
#> number of trait variables: 1 
#> taxon views: 3 
#> 
#> concepts with parents: 3 
#> concepts with children: 2 
#> 
#> concepts with rank information: 4 
#> concepts without rank information: 0 
#> 
#> family: 1
#>   genus: 1
#>     complex: 0
#>       species: 0
#>         subspecies: 0
#>           variety: 2
#>             form: 0
#> 
#> 
```
