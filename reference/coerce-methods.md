# Coerce taxlist objects to lists.

Coercion of S4 objects to lists can be applied to explore their content,
avoiding errors caused by their validation.

## Usage

``` r
S4_to_list(x)
```

## Arguments

- x:

  An object of class
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  or any S4 class.

## Value

An object of class [list](https://rdrr.io/r/base/list.html).

## Details

Coerce
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects to lists.

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Coerce taxlist to list
tax_list <- as(Easplist, "list")

## Coerce data frame to taxlist
Cyperus <- read.csv(file = file.path(path.package("taxlist"), "cyperus",
        "names.csv"))
Cyperus$AcceptedName <- !Cyperus$SYNONYM
head(Cyperus)
#>   TaxonUsageID LETTERCODE           SHORTNAME           TaxonName NATIVENAME
#> 1          192    CYPEAUR Cyperus auriculatus Cyperus auriculatus         NA
#> 2          193    CYPECOR  Cyperus corymbosus  Cyperus corymbosus         NA
#> 3          194    CYPEDIF   Cyperus difformis   Cyperus difformis         NA
#> 4          195    CYPEDIG   Cyperus digitatus   Cyperus digitatus         NA
#> 5          196    CYPEDIS     Cyperus distans     Cyperus distans         NA
#> 6          197    CYPEDIV       Cyperus dives       Cyperus dives         NA
#>                     AuthorName SYNONYM TaxonConceptID AcceptedName
#> 1 (Nees & Meyen ex Kunth) Kük.   FALSE            192         TRUE
#> 2                       Rottb.   FALSE            193         TRUE
#> 3                           L.   FALSE            194         TRUE
#> 4                        Roxb.   FALSE            195         TRUE
#> 5                        L. f.   FALSE            196         TRUE
#> 6                       Delile   FALSE            197         TRUE

as(Cyperus, "taxlist")
#> object size: 32.1 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 95 
#> number of taxon concepts: 42 
#> trait entries: 0 
#> number of trait variables: 0 
#> taxon views: 0 
#> 
```
