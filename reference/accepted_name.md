# Manage accepted names, synonyms and basionyms

Taxon usage names for a taxon concept can be divided into three
categories: accepted names, basionyms and synonyms. Each single taxon
concept may at least have an accepted name, while basionym and synonyms
are optional.

The function `accepted_name()` retrieves the accepted names for the
indicated taxon concepts or for the whole
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
object. By using `show_traits=TRUE`, the respective taxon traits will be
displayed as well, providing an overview of taxa included in the object.
The replacement method for this function will set the respective usage
name IDs as accepted names for the respective taxon concept, provided
that these names are already set as synonyms in the respective concepts.

The function `synonyms()` is working in a similar way as
`accepted_name()`, but this function does not include taxon traits in
the output. Alternatives for inserting new synonyms into a taxon concept
are either moving synonyms from other taxa by using change_concept\<- or
inserting new names in the object by using
[`add_synonym()`](https://docs.ropensci.org/taxlist/reference/taxon_names.md).

The function `basionym()` is retrieving and setting basionyms in the
respective taxon concepts similarly to `accepted_name`, but this
function does not retrieve any information on taxon traits, either.

The fucntion `change_concept<-` replace a taxon usage name (argument
`'UsageID'`) to a different taxonomic concept (argument `'value'`).

## Usage

``` r
accepted_name(taxlist, ...)

# S3 method for class 'taxlist'
accepted_name(taxlist, ConceptID, show_traits = FALSE, ...)

accepted_name(taxlist, ...) <- value

# S3 method for class 'taxlist'
accepted_name(taxlist, ConceptID, ...) <- value

synonyms(taxlist, ...)

# S3 method for class 'taxlist'
synonyms(taxlist, ConceptID, ...)

basionym(taxlist, ...)

# S3 method for class 'taxlist'
basionym(taxlist, ConceptID, ...)

basionym(taxlist, ...) <- value

# S3 method for class 'taxlist'
basionym(taxlist, ConceptID, ...) <- value

change_concept(taxlist, ...) <- value

# S3 method for class 'taxlist'
change_concept(taxlist, UsageID, ...) <- value
```

## Arguments

- taxlist:

  An object of class
  [taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md).

- ...:

  Further arguments passed among methods.

- ConceptID:

  Integer containing concept IDs where to request or set names for one
  category.

- show_traits:

  Logical value, whether traits should be included in the output of
  `accepted_name` or not.

- value:

  Integer containing usage IDs to be set to the respective category in
  the respective taxon concept.

- UsageID:

  Numeric vector with taxon usage IDs that will be changed to a
  different taxonomic concept.

## Value

Most of the methods return information in data frames, while replacement
methods do it as
[taxlist](https://docs.ropensci.org/taxlist/reference/taxlist-class.md)
objects.

## See also

[`add_synonym()`](https://docs.ropensci.org/taxlist/reference/taxon_names.md)
change_concept\<-

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## Set a different accepted name for Cyclosorus interruptus
summary(Easplist, "Cyclosorus interruptus")
#> ------------------------------ 
#> concept ID: 50074 
#> view ID: 1 
#> level: species 
#> parent: 55055 Cyclosorus Link 
#> 
#> # accepted name: 
#> 50074 Cyclosorus interruptus (Willd.) H. Itô 
#> 
#> # synonyms (13): 
#> 52002 Dryopteris gongylodes (Schkuhr) Kuntze 
#> 52008 Thelypteris interrupta (Willd.) K. Iwats. 
#> 52009 Cyclosorus striatus Ching 
#> 53097 Pteris interrupta Willd. 
#> 53098 Aspidium continuum Desv. 
#> 53099 Aspidium ecklonii Kunze 
#> 53100 Aspidium gongylodes Schkuhr 
#> 53101 Aspidium obtusatum Sw. 
#> 53102 Aspidium pteroides (Retz.) Sw. 
#> 53103 Aspidium serra (Sw.) Sw. 
#> 53104 Aspidium serratum Sw. 
#> 53105 Aspidium unitum (L.) Sw. 
#> 53106 Nephrodium propinquum R. Br. 
#> ------------------------------
accepted_name(Easplist, 50074) <- 53097
summary(Easplist, 50074)
#> ------------------------------ 
#> concept ID: 50074 
#> view ID: 1 
#> level: species 
#> parent: 55055 Cyclosorus Link 
#> 
#> # accepted name: 
#> 53097 Pteris interrupta Willd. 
#> 
#> # synonyms (13): 
#> 50074 Cyclosorus interruptus (Willd.) H. Itô 
#> 52002 Dryopteris gongylodes (Schkuhr) Kuntze 
#> 52008 Thelypteris interrupta (Willd.) K. Iwats. 
#> 52009 Cyclosorus striatus Ching 
#> 53098 Aspidium continuum Desv. 
#> 53099 Aspidium ecklonii Kunze 
#> 53100 Aspidium gongylodes Schkuhr 
#> 53101 Aspidium obtusatum Sw. 
#> 53102 Aspidium pteroides (Retz.) Sw. 
#> 53103 Aspidium serra (Sw.) Sw. 
#> 53104 Aspidium serratum Sw. 
#> 53105 Aspidium unitum (L.) Sw. 
#> 53106 Nephrodium propinquum R. Br. 
#> ------------------------------

## Inserting a new name first
summary(Easplist, "Basella alba")
#> ------------------------------ 
#> concept ID: 68 
#> view ID: 1 
#> level: species 
#> parent: 54790 Basella L. 
#> 
#> # accepted name: 
#> 68 Basella alba L. 
#> ------------------------------
Easplist <- add_synonym(taxlist = Easplist, ConceptID = 68,
    TaxonName = "Basella cordifolia", AuthorName = "Lam.")
summary(Easplist, 68)
#> ------------------------------ 
#> concept ID: 68 
#> view ID: 1 
#> level: species 
#> parent: 54790 Basella L. 
#> 
#> # accepted name: 
#> 68 Basella alba L. 
#> 
#> # synonyms (1): 
#> 56139 Basella cordifolia Lam. 
#> ------------------------------
accepted_name(Easplist, 68) <- 56139
summary(Easplist, 68)
#> ------------------------------ 
#> concept ID: 68 
#> view ID: 1 
#> level: species 
#> parent: 54790 Basella L. 
#> 
#> # accepted name: 
#> 56139 Basella cordifolia Lam. 
#> 
#> # synonyms (1): 
#> 68 Basella alba L. 
#> ------------------------------

## Display synonyms
head(synonyms(taxlist = Easplist))
#>    TaxonUsageID TaxonConceptID               TaxonName              AuthorName
#> 2         52313              1     Hibiscus esculentus                      L.
#> 5         50361              3          Pavonia patens        (Andrews) Chiov.
#> 23        50001             20   Spilanthes mauritiana (A. Rich. ex Pers.) DC.
#> 25        50002             21    Spilanthes uliginosa                     Sw.
#> 29        50003             24 Podocarpus usambarensis                   Pilg.
#> 44        50004             38     Amaranthus cruentus                      L.
#>                         AcceptedName AuthorAcceptedName
#> 2             Abelmoschus esculentus        (L.) Moench
#> 5               Abutilon mauritianum     (Jacq.) Medik.
#> 23                Acmella caulirhiza             Delile
#> 25                 Acmella uliginosa        (Sw.) Cass.
#> 29           Afrocarpus usambarensis (Pilg.) C. N. Page
#> 44 Amaranthus hybridus ssp. cruentus        (L.) Thell.

## Synonyms for an specific concept
synonyms(taxlist = Easplist, ConceptID = 20)
#>      TaxonUsageID TaxonConceptID                                   TaxonName
#> 23          50001             20                       Spilanthes mauritiana
#> 2889        52448             20                       Spilanthes caulirhiza
#> 2890        52449             20                          Acmella mauritiana
#> 2891        52450             20                         Spilanthes africana
#> 2892        52451             20                       Spilanthes abyssinica
#> 2893        52452             20                          Eclipta filicaulis
#> 2894        52453             20                       Spilanthes filicaulis
#> 2895        52454             20             Spilanthes acmella var. acmella
#> 2896        52455             20                           Verbesina acmella
#> 2897        52456             20                          Spilanthes acmella
#> 2898        52457             20                         Blainvillea acmella
#> 2899        52458             20                           Eclipta latifolia
#> 2900        52459             20                       Blainvillea latifolia
#> 2901        52460             20                      Blainvillea rhomboidea
#> 2902        52461             20                   Blainvillea dalla-vedovae
#> 2903        52462             20                         Verbesina dichotoma
#> 2904        52463             20                       Blainvillea dichotoma
#> 2905        52464             20 Spilanthes caulirhiza var. madagascariensis
#> 2906        52465             20   Spilanthes mauritiana f. madagascariensis
#>                            AuthorName       AcceptedName AuthorAcceptedName
#> 23            (A. Rich. ex Pers.) DC. Acmella caulirhiza             Delile
#> 2889                     (Delile) DC. Acmella caulirhiza             Delile
#> 2890                A. Rich. ex Pers. Acmella caulirhiza             Delile
#> 2891                              DC. Acmella caulirhiza             Delile
#> 2892            Sch. Bip. ex A. Rich. Acmella caulirhiza             Delile
#> 2893               Schumach. & Thonn. Acmella caulirhiza             Delile
#> 2894 (Schumach. & Thonn.) C. D. Adams Acmella caulirhiza             Delile
#> 2895                      (L.) Murray Acmella caulirhiza             Delile
#> 2896                               L. Acmella caulirhiza             Delile
#> 2897                      (L.) Murray Acmella caulirhiza             Delile
#> 2898                   (L.) Philipson Acmella caulirhiza             Delile
#> 2899                            L. f. Acmella caulirhiza             Delile
#> 2900                      (L. f.) DC. Acmella caulirhiza             Delile
#> 2901                            Cass. Acmella caulirhiza             Delile
#> 2902                      A. Terracc. Acmella caulirhiza             Delile
#> 2903                           Murray Acmella caulirhiza             Delile
#> 2904                 (Murray) Stewart Acmella caulirhiza             Delile
#> 2905                              DC. Acmella caulirhiza             Delile
#> 2906                (DC.) A. H. Moore Acmella caulirhiza             Delile

## Basionym for Cyclosrus interruptus
summary(Easplist, 50074)
#> ------------------------------ 
#> concept ID: 50074 
#> view ID: 1 
#> level: species 
#> parent: 55055 Cyclosorus Link 
#> 
#> # accepted name: 
#> 53097 Pteris interrupta Willd. 
#> 
#> # synonyms (13): 
#> 50074 Cyclosorus interruptus (Willd.) H. Itô 
#> 52002 Dryopteris gongylodes (Schkuhr) Kuntze 
#> 52008 Thelypteris interrupta (Willd.) K. Iwats. 
#> 52009 Cyclosorus striatus Ching 
#> 53098 Aspidium continuum Desv. 
#> 53099 Aspidium ecklonii Kunze 
#> 53100 Aspidium gongylodes Schkuhr 
#> 53101 Aspidium obtusatum Sw. 
#> 53102 Aspidium pteroides (Retz.) Sw. 
#> 53103 Aspidium serra (Sw.) Sw. 
#> 53104 Aspidium serratum Sw. 
#> 53105 Aspidium unitum (L.) Sw. 
#> 53106 Nephrodium propinquum R. Br. 
#> ------------------------------
basionym(Easplist, 50074) <- 53097

summary(Easplist, 50074)
#> ------------------------------ 
#> concept ID: 50074 
#> view ID: 1 
#> level: species 
#> parent: 55055 Cyclosorus Link 
#> 
#> # accepted name: 
#> 53097 Pteris interrupta Willd. 
#> 
#> # basionym: 
#> numeric(0) character(0) character(0) 
#> 
#> # synonyms (13): 
#> 50074 Cyclosorus interruptus (Willd.) H. Itô 
#> 52002 Dryopteris gongylodes (Schkuhr) Kuntze 
#> 52008 Thelypteris interrupta (Willd.) K. Iwats. 
#> 52009 Cyclosorus striatus Ching 
#> 53098 Aspidium continuum Desv. 
#> 53099 Aspidium ecklonii Kunze 
#> 53100 Aspidium gongylodes Schkuhr 
#> 53101 Aspidium obtusatum Sw. 
#> 53102 Aspidium pteroides (Retz.) Sw. 
#> 53103 Aspidium serra (Sw.) Sw. 
#> 53104 Aspidium serratum Sw. 
#> 53105 Aspidium unitum (L.) Sw. 
#> 53106 Nephrodium propinquum R. Br. 
#> ------------------------------
basionym(Easplist, 50074)
#>     TaxonConceptID Basionym      BasionymName BasionymAuthor
#> 601          50074    53097 Pteris interrupta         Willd.

## Move the name Typha aethiopica to concept 573 (T. latifolia)
summary(Easplist, c(50105, 573))
#> ------------------------------ 
#> concept ID: 50105 
#> view ID: 1 
#> level: species 
#> parent: 55040 Typha L. 
#> 
#> # accepted name: 
#> 50105 Typha domingensis Pers. 
#> 
#> # synonyms (9): 
#> 51999 Typha australis Schumach. 
#> 53124 Typha angustifolia ssp. australis (Schumach.) Graebn. 
#> 53125 Typha aequalis Schnizl. 
#> 53126 Typha angustata Bory & Chaub. 
#> 53127 Typha angustifolia ssp. angustata (Bory & Chaub.) Briq. 
#> 53128 Typha angustata var. abyssinica Graebn. 
#> 53129 Typha angustata var. aethiopica Rohrb. 
#> 53130 Typha aethiopica (Rohrb.) Kronfeldt 
#> 53131 Typha schimperi Rohrb. 
#> ------------------------------ 
#> concept ID: 573 
#> view ID: 1 
#> level: species 
#> parent: 55040 Typha L. 
#> 
#> # accepted name: 
#> 573 Typha latifolia L. 
#> ------------------------------
change_concept(Easplist, 53130) <- 573
summary(Easplist, c(50105, 573))
#> ------------------------------ 
#> concept ID: 50105 
#> view ID: 1 
#> level: species 
#> parent: 55040 Typha L. 
#> 
#> # accepted name: 
#> 50105 Typha domingensis Pers. 
#> 
#> # synonyms (8): 
#> 51999 Typha australis Schumach. 
#> 53124 Typha angustifolia ssp. australis (Schumach.) Graebn. 
#> 53125 Typha aequalis Schnizl. 
#> 53126 Typha angustata Bory & Chaub. 
#> 53127 Typha angustifolia ssp. angustata (Bory & Chaub.) Briq. 
#> 53128 Typha angustata var. abyssinica Graebn. 
#> 53129 Typha angustata var. aethiopica Rohrb. 
#> 53131 Typha schimperi Rohrb. 
#> ------------------------------ 
#> concept ID: 573 
#> view ID: 1 
#> level: species 
#> parent: 55040 Typha L. 
#> 
#> # accepted name: 
#> 573 Typha latifolia L. 
#> 
#> # synonyms (1): 
#> 53130 Typha aethiopica (Rohrb.) Kronfeldt 
#> ------------------------------
```
