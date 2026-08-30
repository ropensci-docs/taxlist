# Dissect Scientific Names into their Elements

Depending the degree of resolution and specific roles of nomenclature,
strings containing taxon usage names (scientific names) are constructed
with different parts. A string with names can be consequently split into
those elements, meanwhile the number of elements may suggest the
taxonomic ranks.

This function is a wrapper of
[`strsplit()`](https://rdrr.io/r/base/strsplit.html), while name element
can be re-pasted if indicated in argument `repaste`.

## Usage

``` r
dissect_name(x, split = " ", fixed = TRUE, repaste, ...)
```

## Arguments

- x:

  A character vector containing taxon names.

- split, fixed, ...:

  Arguments passed to
  [`strsplit()`](https://rdrr.io/r/base/strsplit.html).

- repaste:

  An integer vector indicating the elements of the name selected for the
  output.

## Value

A character matrix with as many rows as names in the input vector. If
`repaste` is indicated, then the output will be a character vector.

## See also

[`strsplit()`](https://rdrr.io/r/base/strsplit.html)

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
# A list of variety names
sp_list <- subset(x = Easplist, subset = Level == "variety", slot = "relations")
sp_list <- accepted_name(sp_list)[c(1:10), "TaxonName"]

# split name
dissect_name(sp_list)
#>       [,1]          [,2]            [,3]   [,4]               
#>  [1,] "Euphorbia"   "inaequilatera" "var." "dentata"          
#>  [2,] "Oldenlandia" "corymbosa"     "var." "caespitosa"       
#>  [3,] "Pilea"       "usambarensis"  "var." "veronicifolia"    
#>  [4,] "Trifolium"   "semipilosum"   "var." "glabrescens"      
#>  [5,] "Pentas"      "lanceolata"    "var." "nemorosa"         
#>  [6,] "Stachys"     "aculeolata"    "var." "aculeolata"       
#>  [7,] "Pimpinella"  "oreophila"     "var." "kilimandscharica" 
#>  [8,] "Cyperus"     "denudatus"     "var." "lucenti-nigricans"
#>  [9,] "Achyranthes" "aspera"        "var." "sicula"           
#> [10,] "Digitaria"   "diagonalis"    "var." "uniglumis"        

# re-paste the two first words (species name)
dissect_name(sp_list, repaste = c(1:2))
#>  [1] "Euphorbia inaequilatera" "Oldenlandia corymbosa"  
#>  [3] "Pilea usambarensis"      "Trifolium semipilosum"  
#>  [5] "Pentas lanceolata"       "Stachys aculeolata"     
#>  [7] "Pimpinella oreophila"    "Cyperus denudatus"      
#>  [9] "Achyranthes aspera"      "Digitaria diagonalis"   
```
