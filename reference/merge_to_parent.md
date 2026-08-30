# Merge taxa to their respective parents

Aggregation of taxon concepts to their respective parents. All names of
aggregated concepts will become synonyms in the target parent.

## Usage

``` r
merge_to_parent(object, ...)

# S3 method for class 'taxlist'
merge_to_parent(object, concept_id, ...)
```

## Arguments

- object:

  An object of class
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

- ...:

  Further arguments passed among methods.

- concept_id:

  A vector of IDs (TaxonConceptID) of taxa that will be aggregated into
  their respective parents. Note that if one of the IDs is
  simultaneously the parent of another ID in the vector, this function
  will retrieve an error message.

## Value

An object of class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
with merged taxa.

## See also

[`merge_taxa()`](https://docs.ropensci.org/taxlist/reference/merge_taxa.md)

## Examples

``` r
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

## Merge two species with the genus
summary(ky, c(346, 50400))
#> ------------------------------ 
#> concept ID: 346 
#> view ID: 1 
#> level: species 
#> parent: 54919 Kyllinga Rottb. 
#> 
#> # accepted name: 
#> 346 Kyllinga alata Nees 
#> ------------------------------ 
#> concept ID: 50400 
#> view ID: 1 
#> level: species 
#> parent: 54919 Kyllinga Rottb. 
#> 
#> # accepted name: 
#> 50400 Kyllinga elatior Kunth 
#> 
#> # synonyms (2): 
#> 50401 Cyperus pinguis (C.B. Clarke) Mattf. & Kük. 
#> 54152 Cyperus aromaticus var. elatior (Kunth) Kük. 
#> ------------------------------
summary(ky, "Kyllinga", exact = TRUE)
#> ------------------------------ 
#> concept ID: 54919 
#> view ID: 2 
#> level: genus 
#> parent: 55959 Cyperaceae Juss. 
#> 
#> # accepted name: 
#> 54921 Kyllinga Rottb. 
#> ------------------------------
ky <- merge_to_parent(ky, c(346, 50400))

summary(ky, "Kyllinga", exact = TRUE)
#> ------------------------------ 
#> concept ID: 54919 
#> view ID: 2 
#> level: genus 
#> parent: 55959 Cyperaceae Juss. 
#> 
#> # accepted name: 
#> 54921 Kyllinga Rottb. 
#> 
#> # synonyms (4): 
#> 346 Kyllinga alata Nees 
#> 50400 Kyllinga elatior Kunth 
#> 50401 Cyperus pinguis (C.B. Clarke) Mattf. & Kük. 
#> 54152 Cyperus aromaticus var. elatior (Kunth) Kük. 
#> ------------------------------
```
