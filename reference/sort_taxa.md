# Sort taxa for further print

Sorting taxa in slot **taxonRelations** will be reflected in printed
list by functions such as
[`summary()`](https://docs.ropensci.org/taxlist/reference/summary.md)
and
[`indented_list()`](https://docs.ropensci.org/taxlist/reference/indented_list.md).
This is a wrapper for [`order()`](https://rdrr.io/r/base/order.html).

## Usage

``` r
sort_taxa(object, ...)

# S3 method for class 'taxlist'
sort_taxa(object, by = "TaxonName", priority, ...)
```

## Arguments

- object:

  Object of class
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

- ...:

  Further arguments passed to
  [`order()`](https://rdrr.io/r/base/order.html).

- by:

  Character value indicating the column name in slot **taxonRelations**
  of `object` which will be used for the sorting. Additionally you can
  use `by = "TaxonName"` (the default) to get an alphabetical sorting by
  accepted names.

- priority:

  Optional vector with values to be set on top of the list. Its class
  have to match the class of the column `by`.

## Value

An object of class
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
with sorted relations.

## Examples

``` r
## Subset with Boraginaceae
tax <- subset(Easplist, TaxonName == "Boraginaceae",
    keep_children = TRUE, keep_parents = TRUE
)
indented_list(tax)
#> Boraginaceae working name
#>  Coldenia L.
#>    Coldenia procumbens L.
#>  Heliotropium L.
#>    Heliotropium benadirense Chiov.
#>    Heliotropium curassavicum L.
#>    Heliotropium indicum L.
#>    Heliotropium species 
#>    Heliotropium steudneri Vatke
#>     Heliotropium steudneri ssp. bullatum Verdc.
#>    Heliotropium bullockii Verdc.
#>    Heliotropium scotteae Rendle
#>    Heliotropium longiflorum (A. DC.) Jaub. & Spach
#>  Symphytum L.
#>    Symphytum officinale L.
#>  Trichodesma R. Br.
#>    Trichodesma zeylanicum (Burm. f.) R. Br.
#>  Cordia L.
#>    Cordia monoica Roxb.
#>    Cordia africana Lam.
#>    Cordia sinensis Lam.
#>    Cordia crenata Delile
#>  Cynoglossum L.
#>    Cynoglossum lanceolatum Forssk.
#>    Cynoglossum species 
#>    Cynoglossum coeruleum A. DC.
#>      Cynoglossum coeruleum var. mannii (Baker & C.H. Wright) Verdc.
#>  Ehretia P. Browne
#>    Ehretia cymosa Thonn.
#>      Ehretia cymosa var. silvatica (Gürke) Brenan
#>  Lithospermum L.
#>    Lithospermum afromontanum Weim.
#>  Myosotis L.
#>    Myosotis vestergrenii Stroh
#>  Echiochilon Desf.
#>    Echiochilon arenarium (I.M. Johnst.) I.M. Johnst.
#>  Euploca Nutt.
#>    Euploca strigosa (Willd.) Diane & Hilger
#>    Euploca ovalifolia (Forssk.) Diane & Hilger 

## Sorting names alphabetically
tax <- sort_taxa(tax)
indented_list(tax)
#> Boraginaceae working name
#>  Coldenia L.
#>    Coldenia procumbens L.
#>  Cordia L.
#>    Cordia africana Lam.
#>    Cordia crenata Delile
#>    Cordia monoica Roxb.
#>    Cordia sinensis Lam.
#>  Cynoglossum L.
#>    Cynoglossum coeruleum A. DC.
#>      Cynoglossum coeruleum var. mannii (Baker & C.H. Wright) Verdc.
#>    Cynoglossum lanceolatum Forssk.
#>    Cynoglossum species 
#>  Echiochilon Desf.
#>    Echiochilon arenarium (I.M. Johnst.) I.M. Johnst.
#>  Ehretia P. Browne
#>    Ehretia cymosa Thonn.
#>      Ehretia cymosa var. silvatica (Gürke) Brenan
#>  Euploca Nutt.
#>    Euploca ovalifolia (Forssk.) Diane & Hilger
#>    Euploca strigosa (Willd.) Diane & Hilger
#>  Heliotropium L.
#>    Heliotropium benadirense Chiov.
#>    Heliotropium bullockii Verdc.
#>    Heliotropium curassavicum L.
#>    Heliotropium indicum L.
#>    Heliotropium longiflorum (A. DC.) Jaub. & Spach
#>    Heliotropium scotteae Rendle
#>    Heliotropium species 
#>    Heliotropium steudneri Vatke
#>     Heliotropium steudneri ssp. bullatum Verdc.
#>  Lithospermum L.
#>    Lithospermum afromontanum Weim.
#>  Myosotis L.
#>    Myosotis vestergrenii Stroh
#>  Symphytum L.
#>    Symphytum officinale L.
#>  Trichodesma R. Br.
#>    Trichodesma zeylanicum (Burm. f.) R. Br. 

## Setting some names on top of the sorting
tax <- sort_taxa(tax, priority = c("Euploca", "Myosotis", "Cordia monoica"))
indented_list(tax)
#> Boraginaceae working name
#>  Euploca Nutt.
#>    Euploca ovalifolia (Forssk.) Diane & Hilger
#>    Euploca strigosa (Willd.) Diane & Hilger
#>  Myosotis L.
#>    Myosotis vestergrenii Stroh
#>  Coldenia L.
#>    Coldenia procumbens L.
#>  Cordia L.
#>    Cordia monoica Roxb.
#>    Cordia africana Lam.
#>    Cordia crenata Delile
#>    Cordia sinensis Lam.
#>  Cynoglossum L.
#>    Cynoglossum coeruleum A. DC.
#>      Cynoglossum coeruleum var. mannii (Baker & C.H. Wright) Verdc.
#>    Cynoglossum lanceolatum Forssk.
#>    Cynoglossum species 
#>  Echiochilon Desf.
#>    Echiochilon arenarium (I.M. Johnst.) I.M. Johnst.
#>  Ehretia P. Browne
#>    Ehretia cymosa Thonn.
#>      Ehretia cymosa var. silvatica (Gürke) Brenan
#>  Heliotropium L.
#>    Heliotropium benadirense Chiov.
#>    Heliotropium bullockii Verdc.
#>    Heliotropium curassavicum L.
#>    Heliotropium indicum L.
#>    Heliotropium longiflorum (A. DC.) Jaub. & Spach
#>    Heliotropium scotteae Rendle
#>    Heliotropium species 
#>    Heliotropium steudneri Vatke
#>     Heliotropium steudneri ssp. bullatum Verdc.
#>  Lithospermum L.
#>    Lithospermum afromontanum Weim.
#>  Symphytum L.
#>    Symphytum officinale L.
#>  Trichodesma R. Br.
#>    Trichodesma zeylanicum (Burm. f.) R. Br. 
```
