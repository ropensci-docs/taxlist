# Import species lists from Turboveg databases

Importing species lists from [Turboveg
2](https://www.synbiosys.alterra.nl/turboveg/) databases into a
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object.

Internally the funcions
[`foreign::read.dbf()`](https://rdrr.io/pkg/foreign/man/read.dbf.html)
and
[`df2taxlist()`](https://docs.ropensci.org/taxlist/reference/df2taxlist.md)
are called.

## Usage

``` r
tv2taxlist(taxlist, tv_home = tv.home(), ...)
```

## Arguments

- taxlist:

  Character value indicating the name of a species list in Turboveg.

- tv_home:

  Character value indicating the path to the main Turboveg folder.

- ...:

  Further arguments passed to
  [`df2taxlist()`](https://docs.ropensci.org/taxlist/reference/df2taxlist.md).

## Value

A
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object.

## See also

[`df2taxlist()`](https://docs.ropensci.org/taxlist/reference/df2taxlist.md)

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Cyperus data set installed as Turboveg species list
Cyperus <- tv2taxlist(taxlist = "cyperus",
  tv_home = file.path(path.package("taxlist"), "tv_data"))
Cyperus
#> object size: 44.6 Kb 
#> validation of 'taxlist' object: TRUE 
#> 
#> number of taxon usage names: 95 
#> number of taxon concepts: 42 
#> trait entries: 42 
#> number of trait variables: 2 
#> taxon views: 0 
#> 
```
