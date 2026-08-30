# Insert additional rows to a data frame.

Adding new rows from data frame sharing some columns. Data contained in
`y` is assumed to be additional data and will be appended.

Columns occurring in only one of the data frames will be added to the
output.

## Usage

``` r
insert_rows(x, y, ...)

# S4 method for class 'data.frame,data.frame'
insert_rows(x, y, ...)
```

## Arguments

- x:

  A data frame.

- y:

  A data frame including rows (and columns) to be inserted in `x`.

- ...:

  Addicional arguments passed among methods.

## Value

A data frame.

## Examples

``` r
## Merge data frames including new columns
data(iris)
iris$Species <- paste(iris$Species)
new_iris <- data.frame(Species = rep("humilis", 2), Height = c(15, 20),
    stringsAsFactors = FALSE)
insert_rows(iris, new_iris)
#>     Sepal.Length Sepal.Width Petal.Length Petal.Width    Species Height
#> 1            5.1         3.5          1.4         0.2     setosa     NA
#> 2            4.9         3.0          1.4         0.2     setosa     NA
#> 3            4.7         3.2          1.3         0.2     setosa     NA
#> 4            4.6         3.1          1.5         0.2     setosa     NA
#> 5            5.0         3.6          1.4         0.2     setosa     NA
#> 6            5.4         3.9          1.7         0.4     setosa     NA
#> 7            4.6         3.4          1.4         0.3     setosa     NA
#> 8            5.0         3.4          1.5         0.2     setosa     NA
#> 9            4.4         2.9          1.4         0.2     setosa     NA
#> 10           4.9         3.1          1.5         0.1     setosa     NA
#> 11           5.4         3.7          1.5         0.2     setosa     NA
#> 12           4.8         3.4          1.6         0.2     setosa     NA
#> 13           4.8         3.0          1.4         0.1     setosa     NA
#> 14           4.3         3.0          1.1         0.1     setosa     NA
#> 15           5.8         4.0          1.2         0.2     setosa     NA
#> 16           5.7         4.4          1.5         0.4     setosa     NA
#> 17           5.4         3.9          1.3         0.4     setosa     NA
#> 18           5.1         3.5          1.4         0.3     setosa     NA
#> 19           5.7         3.8          1.7         0.3     setosa     NA
#> 20           5.1         3.8          1.5         0.3     setosa     NA
#> 21           5.4         3.4          1.7         0.2     setosa     NA
#> 22           5.1         3.7          1.5         0.4     setosa     NA
#> 23           4.6         3.6          1.0         0.2     setosa     NA
#> 24           5.1         3.3          1.7         0.5     setosa     NA
#> 25           4.8         3.4          1.9         0.2     setosa     NA
#> 26           5.0         3.0          1.6         0.2     setosa     NA
#> 27           5.0         3.4          1.6         0.4     setosa     NA
#> 28           5.2         3.5          1.5         0.2     setosa     NA
#> 29           5.2         3.4          1.4         0.2     setosa     NA
#> 30           4.7         3.2          1.6         0.2     setosa     NA
#> 31           4.8         3.1          1.6         0.2     setosa     NA
#> 32           5.4         3.4          1.5         0.4     setosa     NA
#> 33           5.2         4.1          1.5         0.1     setosa     NA
#> 34           5.5         4.2          1.4         0.2     setosa     NA
#> 35           4.9         3.1          1.5         0.2     setosa     NA
#> 36           5.0         3.2          1.2         0.2     setosa     NA
#> 37           5.5         3.5          1.3         0.2     setosa     NA
#> 38           4.9         3.6          1.4         0.1     setosa     NA
#> 39           4.4         3.0          1.3         0.2     setosa     NA
#> 40           5.1         3.4          1.5         0.2     setosa     NA
#> 41           5.0         3.5          1.3         0.3     setosa     NA
#> 42           4.5         2.3          1.3         0.3     setosa     NA
#> 43           4.4         3.2          1.3         0.2     setosa     NA
#> 44           5.0         3.5          1.6         0.6     setosa     NA
#> 45           5.1         3.8          1.9         0.4     setosa     NA
#> 46           4.8         3.0          1.4         0.3     setosa     NA
#> 47           5.1         3.8          1.6         0.2     setosa     NA
#> 48           4.6         3.2          1.4         0.2     setosa     NA
#> 49           5.3         3.7          1.5         0.2     setosa     NA
#> 50           5.0         3.3          1.4         0.2     setosa     NA
#> 51           7.0         3.2          4.7         1.4 versicolor     NA
#> 52           6.4         3.2          4.5         1.5 versicolor     NA
#> 53           6.9         3.1          4.9         1.5 versicolor     NA
#> 54           5.5         2.3          4.0         1.3 versicolor     NA
#> 55           6.5         2.8          4.6         1.5 versicolor     NA
#> 56           5.7         2.8          4.5         1.3 versicolor     NA
#> 57           6.3         3.3          4.7         1.6 versicolor     NA
#> 58           4.9         2.4          3.3         1.0 versicolor     NA
#> 59           6.6         2.9          4.6         1.3 versicolor     NA
#> 60           5.2         2.7          3.9         1.4 versicolor     NA
#> 61           5.0         2.0          3.5         1.0 versicolor     NA
#> 62           5.9         3.0          4.2         1.5 versicolor     NA
#> 63           6.0         2.2          4.0         1.0 versicolor     NA
#> 64           6.1         2.9          4.7         1.4 versicolor     NA
#> 65           5.6         2.9          3.6         1.3 versicolor     NA
#> 66           6.7         3.1          4.4         1.4 versicolor     NA
#> 67           5.6         3.0          4.5         1.5 versicolor     NA
#> 68           5.8         2.7          4.1         1.0 versicolor     NA
#> 69           6.2         2.2          4.5         1.5 versicolor     NA
#> 70           5.6         2.5          3.9         1.1 versicolor     NA
#> 71           5.9         3.2          4.8         1.8 versicolor     NA
#> 72           6.1         2.8          4.0         1.3 versicolor     NA
#> 73           6.3         2.5          4.9         1.5 versicolor     NA
#> 74           6.1         2.8          4.7         1.2 versicolor     NA
#> 75           6.4         2.9          4.3         1.3 versicolor     NA
#> 76           6.6         3.0          4.4         1.4 versicolor     NA
#> 77           6.8         2.8          4.8         1.4 versicolor     NA
#> 78           6.7         3.0          5.0         1.7 versicolor     NA
#> 79           6.0         2.9          4.5         1.5 versicolor     NA
#> 80           5.7         2.6          3.5         1.0 versicolor     NA
#> 81           5.5         2.4          3.8         1.1 versicolor     NA
#> 82           5.5         2.4          3.7         1.0 versicolor     NA
#> 83           5.8         2.7          3.9         1.2 versicolor     NA
#> 84           6.0         2.7          5.1         1.6 versicolor     NA
#> 85           5.4         3.0          4.5         1.5 versicolor     NA
#> 86           6.0         3.4          4.5         1.6 versicolor     NA
#> 87           6.7         3.1          4.7         1.5 versicolor     NA
#> 88           6.3         2.3          4.4         1.3 versicolor     NA
#> 89           5.6         3.0          4.1         1.3 versicolor     NA
#> 90           5.5         2.5          4.0         1.3 versicolor     NA
#> 91           5.5         2.6          4.4         1.2 versicolor     NA
#> 92           6.1         3.0          4.6         1.4 versicolor     NA
#> 93           5.8         2.6          4.0         1.2 versicolor     NA
#> 94           5.0         2.3          3.3         1.0 versicolor     NA
#> 95           5.6         2.7          4.2         1.3 versicolor     NA
#> 96           5.7         3.0          4.2         1.2 versicolor     NA
#> 97           5.7         2.9          4.2         1.3 versicolor     NA
#> 98           6.2         2.9          4.3         1.3 versicolor     NA
#> 99           5.1         2.5          3.0         1.1 versicolor     NA
#> 100          5.7         2.8          4.1         1.3 versicolor     NA
#> 101          6.3         3.3          6.0         2.5  virginica     NA
#> 102          5.8         2.7          5.1         1.9  virginica     NA
#> 103          7.1         3.0          5.9         2.1  virginica     NA
#> 104          6.3         2.9          5.6         1.8  virginica     NA
#> 105          6.5         3.0          5.8         2.2  virginica     NA
#> 106          7.6         3.0          6.6         2.1  virginica     NA
#> 107          4.9         2.5          4.5         1.7  virginica     NA
#> 108          7.3         2.9          6.3         1.8  virginica     NA
#> 109          6.7         2.5          5.8         1.8  virginica     NA
#> 110          7.2         3.6          6.1         2.5  virginica     NA
#> 111          6.5         3.2          5.1         2.0  virginica     NA
#> 112          6.4         2.7          5.3         1.9  virginica     NA
#> 113          6.8         3.0          5.5         2.1  virginica     NA
#> 114          5.7         2.5          5.0         2.0  virginica     NA
#> 115          5.8         2.8          5.1         2.4  virginica     NA
#> 116          6.4         3.2          5.3         2.3  virginica     NA
#> 117          6.5         3.0          5.5         1.8  virginica     NA
#> 118          7.7         3.8          6.7         2.2  virginica     NA
#> 119          7.7         2.6          6.9         2.3  virginica     NA
#> 120          6.0         2.2          5.0         1.5  virginica     NA
#> 121          6.9         3.2          5.7         2.3  virginica     NA
#> 122          5.6         2.8          4.9         2.0  virginica     NA
#> 123          7.7         2.8          6.7         2.0  virginica     NA
#> 124          6.3         2.7          4.9         1.8  virginica     NA
#> 125          6.7         3.3          5.7         2.1  virginica     NA
#> 126          7.2         3.2          6.0         1.8  virginica     NA
#> 127          6.2         2.8          4.8         1.8  virginica     NA
#> 128          6.1         3.0          4.9         1.8  virginica     NA
#> 129          6.4         2.8          5.6         2.1  virginica     NA
#> 130          7.2         3.0          5.8         1.6  virginica     NA
#> 131          7.4         2.8          6.1         1.9  virginica     NA
#> 132          7.9         3.8          6.4         2.0  virginica     NA
#> 133          6.4         2.8          5.6         2.2  virginica     NA
#> 134          6.3         2.8          5.1         1.5  virginica     NA
#> 135          6.1         2.6          5.6         1.4  virginica     NA
#> 136          7.7         3.0          6.1         2.3  virginica     NA
#> 137          6.3         3.4          5.6         2.4  virginica     NA
#> 138          6.4         3.1          5.5         1.8  virginica     NA
#> 139          6.0         3.0          4.8         1.8  virginica     NA
#> 140          6.9         3.1          5.4         2.1  virginica     NA
#> 141          6.7         3.1          5.6         2.4  virginica     NA
#> 142          6.9         3.1          5.1         2.3  virginica     NA
#> 143          5.8         2.7          5.1         1.9  virginica     NA
#> 144          6.8         3.2          5.9         2.3  virginica     NA
#> 145          6.7         3.3          5.7         2.5  virginica     NA
#> 146          6.7         3.0          5.2         2.3  virginica     NA
#> 147          6.3         2.5          5.0         1.9  virginica     NA
#> 148          6.5         3.0          5.2         2.0  virginica     NA
#> 149          6.2         3.4          5.4         2.3  virginica     NA
#> 150          5.9         3.0          5.1         1.8  virginica     NA
#> 151           NA          NA           NA          NA    humilis     15
#> 152           NA          NA           NA          NA    humilis     20
```
