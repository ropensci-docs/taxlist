# Generate Identifiers

Creating identifiers for new elements in a database.

The function `id_solver()` wil compare to set of identifiers and modify
the second to avoid duplicated IDs.

## Usage

``` r
id_generator(
  len,
  minvalue = 1,
  nchar = 10,
  mode = c("numeric", "character"),
  ...
)

id_solver(insert, to, suffix = c("numeric", "character"), sep = "")
```

## Arguments

- len:

  Numeric value indicating the length of the retrieved vector with
  identifiers.

- minvalue:

  Numeric value indicating the minimum value in the vector of
  identifiers. Used only for `'mode = "numeric"'`.

- nchar:

  Numeric value indicating the number of characters included in the
  retrieved identifiers. Used only for `'mode = "character"'`.

- mode:

  Character value indicating the type of identifier created, which is
  either numeric (the default) or charcter.

- ...:

  Further parameters passed to
  [`stringi::stri_rand_strings()`](https://rdrr.io/pkg/stringi/man/stri_rand_strings.html),
  actually to the argument `'pattern'`.

- insert:

  A vector (either numeric or character) containing IDs of elements that
  will be inserted in a database.

- to:

  A vector (either numeric or character) containing IDs of elements thar
  already exist in target database.

- suffix:

  A character vector indicating the mode used for the suffix. Only
  'numeric' or 'character' and partial matchings are accepted here. This
  argument is only used for character IDs. If `'suffix = "character"'`,
  a letter of the alphabet (vector `'letters'`) will be appended to
  duplicated IDs.

- sep:

  A character value used as separator between original character ID and
  the appended suffix.

## Value

A vector with IDs created by `id_generator()`, either as numeric or
character. In the case of `id_solver()`, a vector, which is either
identical to `'insert'` (if no conflicts) or a vector witht he same
properties but with resolved IDs.

## Examples

``` r
## Creating numeric IDs
id_generator(len = 10, minvalue = 5)
#>  [1]  5  6  7  8  9 10 11 12 13 14

## Creating character IDs
id_generator(len = 10, mode = "character")
#>  [1] "5pb90SUHjl" "sA2JOCP3Oy" "HgjCyj3Whg" "1DIdTQhwBD" "gUde5llzyO"
#>  [6] "SJAWUmCi4L" "pGZKaBwXXH" "RN1SO1NYrN" "WbGHTvODf3" "z9WqiEXp1T"

## Solving duplicates in numeric identifiers
id_solver(insert = c(3, 7, 5, 10), to = c(1:5))
#> [1] 11  7 12 10

## Solving duplicates in bibtexkeys
db_refs <- c("Alvarez2003", "Schmitz1988", "Li2023")
new_refs <- c("Alvarez2003", "Li2023", "Mueller1953", "Alvarez2003a")
any(duplicated(c(db_refs, new_refs)))
#> [1] TRUE

solved_refs <- id_solver(insert = new_refs, to = db_refs, suffix = "character")
solved_refs
#> [1] "Alvarez2003b" "Li2023a"      "Mueller1953"  "Alvarez2003a"
any(duplicated(c(db_refs, solved_refs)))
#> [1] FALSE
```
