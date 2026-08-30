# Changelog

## taxlist 0.3.6

#### Bug Fixes

- Error retrieving dates by
  [`sort_backups()`](https://docs.ropensci.org/taxlist/reference/backup_object.md)
  resolved.

## taxlist 0.3.5

CRAN release: 2025-11-28

#### New Features

- New function
  [`reindex()`](https://docs.ropensci.org/taxlist/reference/reindex.md)
  to reassign identifiers to taxon concepts, taxon names and taxon
  views.
- New function
  [`sort_taxa()`](https://docs.ropensci.org/taxlist/reference/sort_taxa.md)
  for sorting taxonomic lists before producing prints.

#### Improvements

- Summary provided by
  [`summary()`](https://docs.ropensci.org/taxlist/reference/summary.md)
  (and
  [`print()`](https://docs.ropensci.org/taxlist/reference/summary.md))
  produces an indented list for the hierarchical levels (taxonomic
  ranks). This list is now inverted (top to bottom). The hierarchical
  display of concepts also lists number of concepts per rank.
- Arrangement of parental chains now is done by an internal fucntion,
  namely `taxlist:::arrange_taxa()`.
- Function
  [`indented_list()`](https://docs.ropensci.org/taxlist/reference/indented_list.md)
  will follow the order of taxonomic concepts in slot **taxonRelations**
  when `alphabetical = FALSE`. This function was formely sorting
  according to **taxonConceptID** in the same situation.

#### Bug Fixes

- This package is now independent from `vegdata`.

## taxlist 0.3.0

CRAN release: 2024-07-03

#### New Features

- New function
  [`prune_levels()`](https://docs.ropensci.org/taxlist/reference/prune_levels.md)
  pruning levels that are not used in `taxlist` objects.
- New function
  [`merge_to_parent()`](https://docs.ropensci.org/taxlist/reference/merge_to_parent.md)
  merging multiple taxa to their respective parents.
- New function
  [`sort_backups()`](https://docs.ropensci.org/taxlist/reference/backup_object.md)
  retrieving a sorted list of backups written by
  [`backup_object()`](https://docs.ropensci.org/taxlist/reference/backup_object.md).
- New function
  [`taxlist2df()`](https://docs.ropensci.org/taxlist/reference/taxlist2df.md)
  for converting `taxlist` objects into data frames.
- New function
  [`parents()`](https://docs.ropensci.org/taxlist/reference/parents.md)
  retrieving parent taxa at a determined rank for selected taxon
  concepts.

#### Improvements

- Function
  [`merge_taxa()`](https://docs.ropensci.org/taxlist/reference/merge_taxa.md)
  can now be used to query a list of taxonomic ranks. This is enabled
  through the argument **level**.
- A new argument **delelte_nomatch** in function
  [`merge_taxa()`](https://docs.ropensci.org/taxlist/reference/merge_taxa.md)
  to delete top ranks and rankless taxa.
- Function
  [`backup_object()`](https://docs.ropensci.org/taxlist/reference/backup_object.md)
  retrieves an invisible vector with information about the written
  backup.
- Function
  [`load_last()`](https://docs.ropensci.org/taxlist/reference/backup_object.md)
  retrieves an invisible data frame with information about the imported
  backup. It also include a new argument `choice` to select a different
  backup from the list produced by
  [`sort_backups()`](https://docs.ropensci.org/taxlist/reference/backup_object.md).
- Function
  [`insert_rows()`](https://docs.ropensci.org/taxlist/reference/insert_rows.md)
  was redefined as a generic function.
- New arguments in function
  [`print_name()`](https://docs.ropensci.org/taxlist/reference/print_name.md):
  - **italics:** a logical value that allows to unset italic format of
    names. This can be usefull for taxonomic ranks that are not written
    in italics (e.g. Family names in plant and animals).
  - **collapse:** a character value (or vector of lengh 2), used to
    collapse strings of names, for instance to mention more than one
    taxa in the text.

## taxlist 0.2.4

CRAN release: 2023-03-12

#### New Features

- New S3 class `matched_names` inheriting data frame properties. This
  class will be used for an interactive selection of multiple choices,
  when a name matches more than one candidate.
- Character identifiers (primary keys) are enabled.
- New functions
  [`id_generator()`](https://docs.ropensci.org/taxlist/reference/id_generator.md)
  to create vectors of identifiers, either as numeric values (integers)
  or as character values by using random strings.
- New function
  [`id_solver()`](https://docs.ropensci.org/taxlist/reference/id_generator.md)
  to compare vectors of identifiers between a recipient database and a
  data set to be inserted into the mentioned database. This function
  will propose a modified vector for the new data to avoid conflicts by
  duplicated IDs.
- Coercion of `taxlist` objects to `data.frame` objects.

#### Improvements

- The validation for `taxlist` objects is also looking if Parent IDs are
  missing in the object.
- Function
  [`match_names()`](https://docs.ropensci.org/taxlist/reference/match_names.md)
  displays multiple matchings per name and also works comparing a string
  with itself.
- Simplified coercion in form of `to_class <- as(obj, from_class)`.
- Function
  [`tnrs()`](https://docs.ropensci.org/taxlist/reference/Deprecated-functions.md)
  deprecated.
- Simplified coercion in form of `to_class <- as(obj, from_class)`
- Function
  [`add_concept()`](https://docs.ropensci.org/taxlist/reference/add_concept.md)
  with a method for `data.frame` objects.

## taxlist 0.2.3

CRAN release: 2022-09-12

#### New Features

- New arguments `isolate` and `trim` to prevent parts of scientific
  names to be formatted in italics.

#### Improvements

- Function
  [`match_names()`](https://docs.ropensci.org/taxlist/reference/match_names.md)
  allows to sort output data frame in the `'character,taxlist-method'`.
- Slot **taxonViews** allowing class `lib_df` from package `biblio`.
- In function
  [`summary()`](https://docs.ropensci.org/taxlist/reference/summary.md),
  when using text as query, a new parameter `exact` allow for querying
  the exact name, which is usefull when querying genera.
- New style of scripts using the package `styler`.
- Name of taxon attribute **lf_behn_2018** changed to **life_form**.
- Function
  [`print_name()`](https://docs.ropensci.org/taxlist/reference/print_name.md)
  is now working with more than one name (vectorized) and reset to an S3
  method, including an option for character vectors.
- Function
  [`df2taxlist()`](https://docs.ropensci.org/taxlist/reference/df2taxlist.md)
  redefined to allow import from a single data frame.

## taxlist 0.2.2

CRAN release: 2021-07-15

#### Bug Fixes

- Functions
  [`taxlist2taxmap()`](https://docs.ropensci.org/taxlist/reference/Deprecated-functions.md)
  and
  [`taxmap2taxlist()`](https://docs.ropensci.org/taxlist/reference/Deprecated-functions.md)
  temporarily deprecated due to conflicts with release of [taxa v.
  0.4.0](https://github.com/ropensci/taxa/releases/tag/v0.4.0)

## taxlist 0.2.1

CRAN release: 2021-03-29

#### New Features

- New function
  [`indented_list()`](https://docs.ropensci.org/taxlist/reference/indented_list.md)
  to print taxonomic ranks in indented lists.

#### Improvements

- New argument `repaste` in function
  [`dissect_name()`](https://docs.ropensci.org/taxlist/reference/dissect_name.md)
  for re-pasting dissected names.
- Function
  [`replace_idx()`](https://docs.ropensci.org/taxlist/reference/replace_x.md)
  setting by default `idx1 = x`.
- Functions
  [`replace_idx()`](https://docs.ropensci.org/taxlist/reference/replace_x.md)
  and
  [`replace_na()`](https://docs.ropensci.org/taxlist/reference/replace_x.md)
  setting by default `idx2 = idx1`.
- Special characters corrected in data set *Cyperus*.
- Validation allowing taxa without rank but parents.

## taxlist 0.2.0

CRAN release: 2020-10-07

#### Improvements

- Several improvements to meet **ROpenSci** requirements documented
  [here](https://github.com/ropensci/software-review/issues/233#issuecomment-652846890).

## taxlist 0.1.9

CRAN release: 2020-05-31

#### Bug Fixes

- Problems with encoding of data set `Easplist`

## taxlist 0.1.8

CRAN release: 2020-04-29

#### New Features

- Function
  [`taxlist2taxmap()`](https://docs.ropensci.org/taxlist/reference/Deprecated-functions.md)
  for the interaction between packages `taxlist` and `taxmap`.
- Function
  [`taxmap2taxlist()`](https://docs.ropensci.org/taxlist/reference/Deprecated-functions.md)
  for the conversion of `Taxmap` objects into `taxlist` ones.

#### Improvements

- Roxygenized version.
- Method `formula` for function
  [`count_taxa()`](https://docs.ropensci.org/taxlist/reference/count_taxa.md).
- New argument `fext` in function
  [`backup_object()`](https://docs.ropensci.org/taxlist/reference/backup_object.md)
  setting the extension of the backup file.

## taxlist 0.1.7

CRAN release: 2020-01-10

#### New Features

- Method for character values in function
  [`match_names()`](https://docs.ropensci.org/taxlist/reference/match_names.md).
- Set of functions for data manipulation, namely
  [`replace_x()`](https://docs.ropensci.org/taxlist/reference/replace_x.md),
  [`replace_idx()`](https://docs.ropensci.org/taxlist/reference/replace_x.md),
  [`replace_na()`](https://docs.ropensci.org/taxlist/reference/replace_x.md),
  and
  [`insert_rows()`](https://docs.ropensci.org/taxlist/reference/insert_rows.md).
- Function
  [`clean()`](https://docs.ropensci.org/taxlist/reference/clean.md) with
  new argument **times** for repeat cleaning of `taxlist` objects.

#### Improvements

- Warning in function
  [`tax2traits()`](https://docs.ropensci.org/taxlist/reference/tax2traits.md)
  for objects without taxonomic ranks.
- Second argument in function `[` applies only to slot **taxonTraits**.
- Replacement method for functions `[` and `$` deprecated.
- Method for function `$` matches all taxon concepts when retrieving
  information from slot **taxonTraits**.
- Missing argument **idx2** will be set as **idx1** in functions
  [`replace_idx()`](https://docs.ropensci.org/taxlist/reference/replace_x.md)
  and
  [`replace_na()`](https://docs.ropensci.org/taxlist/reference/replace_x.md).
- Function
  [`replace_view()`](https://docs.ropensci.org/taxlist/reference/Deprecated-functions.md)
  deprecated.
- Example data set cleaned (specifically author names)

#### Bug Fixes

- Function
  [`match_names()`](https://docs.ropensci.org/taxlist/reference/match_names.md)
  was not properly working for the option `accepted_only=TRUE`.
- Function
  [`merge_taxa()`](https://docs.ropensci.org/taxlist/reference/merge_taxa.md)
  caused orphaned children of replaced taxon concepts.
- Function
  [`clean()`](https://docs.ropensci.org/taxlist/reference/clean.md) not
  working for deleted names.

## taxlist 0.1.6

CRAN release: 2019-01-21

#### New Features

- New function
  [`count_taxa()`](https://docs.ropensci.org/taxlist/reference/count_taxa.md)

#### Improvements

- A new option `style="knitr"` for function
  [`print_name()`](https://docs.ropensci.org/taxlist/reference/print_name.md)
  (See [this
  issue](https://stackoverflow.com/questions/51092103/formatted-scientific-names-from-r-to-latex-using-sweave-or-knitr)
  at **Stack Overflow**).
- In function
  [`backup_object()`](https://docs.ropensci.org/taxlist/reference/backup_object.md),
  the message will be done after successful saving and not before.
- New argument `accepted_only` in function
  [`match_names()`](https://docs.ropensci.org/taxlist/reference/match_names.md),
  for comparing strings only with accepted names.
- Error message for NA’s in argument `x` at function
  [`match_names()`](https://docs.ropensci.org/taxlist/reference/match_names.md)

#### Bugs Fixes

- Function
  [`add_synonym()`](https://docs.ropensci.org/taxlist/reference/taxon_names.md)
  was not properly working for incomplete entries (missing variables in
  the replacement values.)
- Function
  [`load_last()`](https://docs.ropensci.org/taxlist/reference/backup_object.md)
  was not properly working for values of `file` without mention of
  subfolder.
- Function
  [`accepted_name()`](https://docs.ropensci.org/taxlist/reference/accepted_name.md)
  with option `show_traits=TRUE` was not displaying taxa with no entries
  for taxon traits.
- Prototype for object `taxlist` wrongly included a slot **hierarchy.**

## taxlist 0.1.5

CRAN release: 2018-06-29

#### New Features

- A **CITATION** file is included in the installation.
- New method `replace_view`.
- New method `print_name` for formatting taxon names to italic style.
- New method `update_name`, for updating information in slot
  `taxonNames`.
- New method `synonyms` retrieving synonyms for indicated concepts.
- New method `delete_name` for deleting synonyms in `taxlist` objects.
- New method `basionym` for handling basionyms.

#### Improvements

- Function `accepted_name` retrieves also information on `Level`
  (taxonomic rank) and traits (optional in argument `show_traits`).
- Function `summary` for single taxon is displaying the name of the
  parent taxon (accepted name) and optional a string for the taxon view.
- Function `backup_object` prints a message in the console.
- Related functions will join documentation files.
- Data set `Easplist` adapted to new state of database **SWEA-Dataveg**.
- Function `match_names` counts multiple best matchings and includes a
  new argument `show_concepts` for displaying the respective accepted
  names and taxon concept ID.

#### Bugs Fixes

- Function `load_last` was not working for single files with suffix,
  neither for absolute path or paths with underscores.
- Function `summary` for single taxa was not displaying names that are
  homonyms to the accepted name.
- Re-organized documentation.

## taxlist 0.1.4

CRAN release: 2018-05-03

#### New Features

- New function `load_last` to load last backup in an R-session.
- File **inst/ChangeLog** replaced by **NEWS.md**.
- New function `dissect_name` for splitting names into their parts.
- New function `match_names` matching character vectors with names of a
  `taxlist` object.

#### Improvements

- Function `backup_object` is also working with relative paths.

#### Bugs Fixes

- Function `add_view` was not adding new columns in the respective slot.
- Function `tv2taxlist` does not modify slot `taxonViews` in prototype.
- Function `load_last` was not working with values of `filename` having
  underscores.

## taxlist 0.1.3

CRAN release: 2018-01-05

#### New Features

- New function: `add_trait`.
- New function: `tax2traits`.

#### Improvements

- Argument `level` inserted in function `merge_taxa`.
- Function `clean` also set keys to class `integer`.
- Validation checks for the existence of accepted names in names list.

#### Bugs Fixes

- Bug in `add_concept`: wrong assignment of `AcceptedName`.

## taxlist 0.1.2

CRAN release: 2017-08-06

#### New Features

- new function `merge_taxa`.

#### Improvements

- Argument `ConceptID` in `summary` (`taxlis-method`) can be a character
  vector matching `TaxonName`.

## taxlist 0.1.1

CRAN release: 2017-07-23

#### New Features

- New vignette `taxlist-intro`.

#### Improvements

- Package `vegdata` moved from Depends to Imports.
- Function `df2taxlist` adapted to species lists with duplicated names.
- Arguments `keep_parents` and `keep_children` implemented in function
  `subset`.

## taxlist 0.1.0

CRAN release: 2017-06-14

#### New Features

- Released to **CRAN** (<https://cran.r-project.org/package=taxlist>).
