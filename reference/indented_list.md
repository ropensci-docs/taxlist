# Print hierarchical structure in indented lists

Print taxonomic hierarchies (ranks and parent-child relationships) from
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects in an indented list.

## Usage

``` r
indented_list(object, ...)

# S4 method for class 'taxlist'
indented_list(
  object,
  filter,
  keep_children = TRUE,
  keep_parents = TRUE,
  rankless_as,
  indent = " ",
  lead_br = "",
  print = TRUE,
  author = TRUE,
  level = FALSE,
  synonyms = FALSE,
  syn_encl = c("= ", ""),
  secundum,
  alphabetical = FALSE,
  ...
)
```

## Arguments

- object:

  A
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  object containing taxonomic concepts.

- ...:

  Further arguments (not used yet).

- filter:

  A character value (optional) that will be matched with the taxon usage
  names to produce a subset of 'object'. Note that this filter will be
  also applied to synonyms, independent of the argument applied in
  parameter 'synonyms'.

- keep_children:

  A logical value indicating whether children of matched concept should
  be included in the result.

- keep_parents:

  A logical value indicating whether parents of matched concept should
  be included in the result.

- rankless_as:

  A character vector indicating a level (taxonomic rank) to which
  rankless taxa may be set before doing the list.

- indent:

  Symbol used for indentation. This symbol will be multiplied by the
  depth of the taxonomic rank. The default is a blank space. This can be
  also provided as a named vector, with a different indentation symbol
  for the respective taxonomic ranks.

- lead_br:

  Optional line break symbol leading before the indentation. It may be
  required for r-markdown documents.

- print:

  A logical value indicating whether the indented list should be printed
  in the console or not (default = TRUE).

- author:

  A logical value indicating whether the author should be printed with
  the name (default = TRUE).

- level:

  A logical value indicating whether the name of the level (taxonomic
  rank) should be included before the name or not (default = FALSE).

- synonyms:

  A logical value indicating whether the synonyms should be included
  after accepted names or not (default = FALSE).

- syn_encl:

  A character vector of length 2 including the symbols used to enclose
  synonyms. First value will be set before the synonyms and second
  value, after the synonyms.

- secundum:

  A character value matching a name in slot 'taxonViews', which will be
  printed as secundum (taxon view). It is not printed by default.

- alphabetical:

  A logical value indicating whether taxa may be sorted by names or by
  IDs. The default is FALSE, thus taxa are sorted by IDs. Note that
  argument TRUE may not work properly if the object contains homonymous
  taxa.

## Value

If 'print = TRUE', the indented list is printed in the console. The
result, which is a data frame with the elements used to format the
names, can be also assigned to an object.

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Show taxonomy of papyrus
indented_list(Easplist, "papyrus")
#> Cyperaceae Juss.
#>  Cyperus L.
#>    Cyperus papyrus L. 

## Include synonyms and taxon views
indented_list(Easplist, "papyrus", level = TRUE, synonyms = TRUE,
    secundum = "secundum")
#> family Cyperaceae Juss. sec. The Plant List (2013)
#>  genus Cyperus L. sec. Taxonomic Name Resolution Service (2018)
#>    species Cyperus papyrus L. sec. African Plant Database (2012)
#>    = Cyperus papyrus ssp. antiquorum (Willd.) Chiov.
#>    = Cyperus papyrus ssp. nyassicus Chiov. 
```
