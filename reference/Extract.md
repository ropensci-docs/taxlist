# Extract or Replace Parts of taxlist Objects

Quick access to slots `taxonTraits` and `taxonRelations` within
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects.

## Usage

``` r
# S4 method for class 'taxlist'
x[i, j, drop = FALSE]

# S4 method for class 'taxlist'
x$name
```

## Arguments

- x:

  Object of class
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

- i:

  Integer or logical vector used as index for access to taxon concepts,
  referring to the rows in slot 'taxonRelations'. These indices can be
  used to produce a object with a subset of taxon concepts. It is not
  recommended to use character values for this index.

- j:

  Integer, logical or character vector used as index for access to
  variables in slot 'taxonTraits'. These indices can be used to reduce
  the number of variables in the mentioned slot.

- drop:

  A logical value passed to
  [`Extract`](https://rdrr.io/r/base/Extract.html).

- name:

  A symbol or character value for the method `$`, corresponding to a
  variable either at slot 'taxonTraits' or slot 'taxonRelations'.

## Value

The method `$` retrieves a vector, while `[` retrieves a subset of the
input
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object.

## See also

[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
[`subset`](https://docs.ropensci.org/taxlist/reference/subset.md)

## Author

Miguel Alvarez <kamapu78@gmail.com>.

## Examples

``` r
## Statistics on life forms
summary(as.factor(Easplist$life_form))
#>   acropleustophyte        chamaephyte     climbing_plant facultative_annual 
#>                  8                 25                 25                 20 
#>    obligate_annual       phanerophyte   pleustohelophyte         reed_plant 
#>                114                 26                  8                 14 
#>      reptant_plant      tussock_plant                NAs 
#>                 19                 52               3576 

## First concepts in this list
summary(Easplist[1:5, ], "all")
#> ------------------------------ 
#> concept ID: 1 
#> view ID: 1 
#> level: species 
#> parent: none 
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
#> parent: none 
#> 
#> # accepted name: 
#> 2 Abutilon indicum (L.) 
#> ------------------------------ 
#> concept ID: 3 
#> view ID: 1 
#> level: species 
#> parent: none 
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
#> parent: none 
#> 
#> # accepted name: 
#> 4 Acacia drepanolobium Harms ex Y. Sjöstedt 
#> ------------------------------ 
#> concept ID: 5 
#> view ID: 1 
#> level: species 
#> parent: none 
#> 
#> # accepted name: 
#> 5 Acacia elatior Brenan 
#> ------------------------------
```
