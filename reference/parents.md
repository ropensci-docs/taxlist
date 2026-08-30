# Retrieve parents for specific concepts

Retrieve IDs of parents for selected taxa in a taxonomic list.

## Usage

``` r
parents(taxlist, level, ...)

# S4 method for class 'taxlist,character'
parents(taxlist, level, concept, ...)
```

## Arguments

- taxlist:

  An object of class
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
  containing a taxonomic list.

- level:

  A character value indicating the level at which the parents will be
  extracted (upwards in the taxonomic ranks).

- ...:

  Further arguments passed among methods.

- concept:

  A vector containing concept IDs. The taxa for which the parents will
  be retrieved. If not provided, parents for every single taxon concept
  in 'taxlist' will be retrieved.

## Examples

``` r
# Random selection of 5 taxa
IDs <- sample(Easplist@taxonRelations$TaxonConceptID, 5)

# Print names and names of parents
print_name(Easplist, IDs)
#> [1] "*Crabbea* "                         "*Cassia petersiana* Bolle"         
#> [3] "*Myrothamnus flabellifolius* Welw." "*Pittosporum viridiflorum* Sims"   
#> [5] "*Hibiscus* L."                     
print_name(Easplist, parents(Easplist, "genus", IDs))
#> [1] "*Crabbea* "                     "*Cassia* L."                   
#> [3] "*Myrothamnus* Welw."            "*Pittosporum* Banks ex Gaertn."
#> [5] "*Hibiscus* L."                 
print_name(Easplist, parents(Easplist, "family", IDs))
#> [1] "*Acanthaceae* Juss." "*Leguminosae* Juss." "*Myrothamnaceae* "  
#> [4] "*Pittosporaceae* "   "*Malvaceae* Juss."  
```
