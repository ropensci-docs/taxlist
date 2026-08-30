# Add a suffix when strings are identical

An integer will be added as suffix in `x` if an identical value is in
`y`. If a value with suffix is already in `y`, the function will search
for the highest suffix to avoid duplicated values.

## Usage

``` r
add_suffix(x, y, sep = "_")
```

## Arguments

- x:

  (`character` of length 1) The name to be compared.

- y:

  (`character`) Existing names, with or without suffixes.

- sep:

  (`character` of length 1) Symbol to be placed between the original
  name and the suffix.

## Value

A `character` value, either `x` or `x` with suffix if already in `y`.
