# Make and load backups of R objects

When work with data becomes risky, the best practice is to produce
backup files. The function of `backup_object` is a wrapper of
[`save()`](https://rdrr.io/r/base/save.html), adding a time stamp and a
suffix to the name of the resulting file (an R image file with extension
**\*.rda**). The function `load_last` is adapted to this style, loading
the newest version to the session.

## Usage

``` r
backup_object(
  ...,
  objects = character(),
  file,
  stamp = TRUE,
  sep = "_",
  date_format = "%Y-%m-%d",
  time_format = "%H:%M:%S",
  overwrite = FALSE
)

sort_backups(
  name,
  path = ".",
  date_format = "%Y-%m-%d",
  fext = ".rda",
  sep = "_"
)

load_last(file, path, ..., choice)
```

## Arguments

- ...:

  Names of the objects to be saved (either symbols or character strings)
  in `backup_object()`. In `load_last()`, arguments passed to
  `sort_backups()`.

- objects:

  A character vector indicating the names of objects to be included in
  the backup file.

- file:

  A character value indicating the name of the backup file, without the
  extension.

- stamp:

  A logical value indicating whether time should be stamped in the
  backup name or not.

- sep:

  A character value used to separate backup's name from stamp and from
  the suffix.

- date_format:

  A character value indicating the format used for the file stamp. See
  [`strptime()`](https://rdrr.io/r/base/strptime.html).

- time_format:

  A character value indicating the format used for the the time (not
  including the date), which will be used for the invisible report in
  `backup_object()`. See
  [`strptime()`](https://rdrr.io/r/base/strptime.html).

- overwrite:

  A logical value indicating whether existing files must be overwritten
  or not.

- name:

  A character value indicating the root of the backup's name.

- path:

  A character value indicating the path to the folder containing the
  backup files.

- fext:

  A character value indicating the file extension (including the dot
  symbol).

- choice:

  An integer value indicating the backup file to be used for recovery.
  This value refers to the row in the output of `sort_backups()`. If not
  provided, `load_last()` will select the newest backup.

## Value

The function `backup_object()` writes an R-image with extension
**\*.rda** and an invisible vector with the name of the backup, its
absolute path and a time stamp.

The function `sort_backups()` returns a data frame including the sorted
names of backup files from the oldest to the newest.

## Details

In both functions the argument `file` may include either the path
relative to the working directory or the absolute path to the file,
excluding stamps and extension. For `overwrite=FALSE` (the default), a
numeric suffix will be added to the backup's name, if another backup was
produced at the same day. For `overwrite=TRUE` no suffix will be
included in the file and existing files will be overwritten.

The function `load_last()` will load the newest version among backups
stored in the same folder, provided that the backup name includes a time
stamp.

## See also

[`save()`](https://rdrr.io/r/base/save.html),
[`load()`](https://rdrr.io/r/base/load.html).

## Author

Miguel Alvarez <kamapu78@gmail.com>

## Examples

``` r
## A subset with Pseudognaphalium and relatives
Pseudognaphalium <- subset(x = Easplist, subset = grepl("Pseudognaphalium",
        TaxonName), slot = "names", keep_parents = TRUE)

## Create a backup with date stamp in tempdir
backup_object(Pseudognaphalium, file = file.path(tempdir(), "Pseudognaphalium"))
#> Error in save(..., list = objects, file = file.path(path, paste0(file2,     ".rda"))): object ‘Pseudognaphalium’ not found

## Retrieve paths of backup
info_back <- backup_object(Pseudognaphalium, file = file.path(tempdir(),
        "Pseudognaphalium"))
#> Error in save(..., list = objects, file = file.path(path, paste0(file2,     ".rda"))): object ‘Pseudognaphalium’ not found
info_back
#> Error: object 'info_back' not found

## Display all backups
sort_backups("Pseudognaphalium", tempdir())
#> Error in sort_backups("Pseudognaphalium", tempdir()): The requested backup is missing.

## Delete object
rm(list = "Pseudognaphalium")

## To load the last backup into a session
load_last("Pseudognaphalium", path = tempdir())
#> Error in sort_backups(name = file, path = path, ...): The requested backup is missing.

## Load pre-installed backup
load_last(file.path(path.package("taxlist"), "extdata", "Podocarpus"))
#> Loading file 'Podocarpus_2020-01-10.rda' to session.
```
