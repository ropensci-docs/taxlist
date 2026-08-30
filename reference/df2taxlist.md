# Convert data frames and strings into taxlist objects

Function converting template data frame into
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object. Also character vectors including taxonomic names will be
converted but without any information on taxonomic ranks and parental
taxa.

## Usage

``` r
df2taxlist(x, ...)

# S3 method for class 'data.frame'
df2taxlist(x, taxonTraits, taxonViews, levels, clean_strings = TRUE, ...)

# S3 method for class 'character'
df2taxlist(x, ...)
```

## Arguments

- x:

  A data frame or a character vector with taxonomic names. If x is a
  data frame, the columns **TaxonUsageID** (integer with IDs for each
  name), **TaxonConceptID** (integer with IDs for the respective taxon
  concepts), and **TaxonName** (character) are mandatory. Other optional
  columns are **AuthorName** (character with names' authorities),
  **AcceptedName** (logical indicating whether the name is an accepted
  name or a synonym and will be set as TRUE by default), **Level**
  (factor sorting taxonomic ranks in the bottom-up direction),
  **Parent** (integer, the taxon concept ID of the parental taxon), and
  **ViewID** (integer pointing to the ID of taxonomic view, usually a
  bibliographic reference, and will be used only if 'taxonViews' is
  provided. Any further column not included in the prototype of taxlist
  will be considered as names' attributes and inserted in slot
  **taxonNames**.

- ...:

  Further arguments passed among methods. For the `'character-method'`,
  arguments will be passed to the `'data.frame-method'`.

- taxonTraits:

  A data frame with attributes of taxonomic concepts (optional). If
  provided, the column **TaxonConceptID** is mandatorial.

- taxonViews:

  A data frame or
  [biblio::lib_df](https://kamapu.github.io/biblio/reference/lib_df-class.html)
  with references of taxonomic views (optional). If provided, the column
  **ViewID** is mandatorial and have to match the homonymous column at
  'x'.

- levels:

  A character vector setting the levels or taxonomic ranks from the
  bottom to the top. This argument is optional and if missing, the
  column **Level** will be preserved (if factor) or coerced to factor,
  except in the case that no column **Level** is provided.

- clean_strings:

  Logical value, whether function
  [`clean_strings()`](https://docs.ropensci.org/taxlist/reference/clean_strings.md)
  should be applied to 'x' or not.

## Value

A
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object.

## Author

Miguel Alvarez <kamapu78@gmail.com>.

## Examples

``` r
Cyperus <- read.csv(file = file.path(path.package("taxlist"), "cyperus",
  "names.csv"))
head(Cyperus)
#>   TaxonUsageID LETTERCODE           SHORTNAME           TaxonName NATIVENAME
#> 1          192    CYPEAUR Cyperus auriculatus Cyperus auriculatus         NA
#> 2          193    CYPECOR  Cyperus corymbosus  Cyperus corymbosus         NA
#> 3          194    CYPEDIF   Cyperus difformis   Cyperus difformis         NA
#> 4          195    CYPEDIG   Cyperus digitatus   Cyperus digitatus         NA
#> 5          196    CYPEDIS     Cyperus distans     Cyperus distans         NA
#> 6          197    CYPEDIV       Cyperus dives       Cyperus dives         NA
#>                     AuthorName SYNONYM TaxonConceptID
#> 1 (Nees & Meyen ex Kunth) Kük.   FALSE            192
#> 2                       Rottb.   FALSE            193
#> 3                           L.   FALSE            194
#> 4                        Roxb.   FALSE            195
#> 5                        L. f.   FALSE            196
#> 6                       Delile   FALSE            197

## Convert to 'taxlist' object
Cyperus$AcceptedName <- !Cyperus$SYNONYM
df2taxlist(Cyperus)
#> object size: 32.1 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 95 
#> number of taxon concepts: 42 
#> trait entries: 0 
#> number of trait variables: 0 
#> taxon views: 0 
#> 

## Create a 'taxlist' object from character vectors
Plants <- df2taxlist(c("Triticum aestivum", "Zea mays"), AuthorName = "L.")
#> Missing column 'TaxonConceptID' in 'x'. All names will be considered as accepted names.
summary(Plants, "all")
#> ------------------------------ 
#> concept ID: 1 
#> view ID: none 
#> level: none 
#> parent: none 
#> 
#> # accepted name: 
#> 1 Triticum aestivum NA 
#> ------------------------------ 
#> concept ID: 2 
#> view ID: none 
#> level: none 
#> parent: none 
#> 
#> # accepted name: 
#> 2 Zea mays NA 
#> ------------------------------
```
