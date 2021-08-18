Introduction to R
================

## R Programming

R is an open source programming language and software environment for
statistical computing and graphics that is supported by the R Foundation
for Statistical Computing. Today, it is one of the most popular
languages, being used all across the world in a wide variety of domains
and fields.

RStudio is an integrated development environment (IDE) for R. It
includes a console, syntax-highlighting editor that supports direct code
execution, as well as tools for plotting, history, debugging and
workspace management. This tutorial was adapted from **Sydney Informatics Hub's** tutorial at https://github.com/Sydney-Informatics-Hub.

## Working directory

``` r
getwd()
```

    ## [1] "/Users/joaopaulo/Dropbox/João Paulo/R script/Introduction_to_R"

## Calculating things in R

``` r
3+3
```

    ## [1] 6

``` r
1/100
```

    ## [1] 0.01

``` r
sqrt(4)
```

    ## [1] 2

## Variable and Data Types

There are several different types of data you can use in R. We’ll
examine a few common ones in a little more detail.

### Text

Strings are known as “character” in R. Use the double quotes `"` or
single quotes `'` to wrap around the string

``` r
myname <- "João"
```

We can use the `class()` function to see what data type it is

``` r
class(myname)
```

    ## [1] "character"

### Numbers

Numbers have different classes. The most common two are `integer` and
`numeric`. Integers are whole numbers:

``` r
favourite.integer <- as.integer(8)
print(favourite.integer)
```

    ## [1] 8

``` r
class(favourite.integer)
```

    ## [1] "integer"

Numbers can be `numeric` which are decimals:

``` r
favourite.numeric <- as.numeric(8.8)
print(favourite.numeric)
```

    ## [1] 8.8

``` r
class(favourite.numeric)
```

    ## [1] "numeric"

### Logical (True/False)

We use the `==` to test for equality in R

``` r
class(TRUE)
```

    ## [1] "logical"

``` r
favourite.numeric == 8.8
```

    ## [1] TRUE

``` r
favourite.numeric == 9.9
```

    ## [1] FALSE

### Factors

In order to categorise the categorical variables and store it on
multiple levels, we use the data object called R factor.

``` r
directions <- as.factor(c("North", "North", "West", "South"))
class(directions)
```

    ## [1] "factor"

How many categories are there for disorders and what are they?

``` r
levels(directions)
```

    ## [1] "North" "South" "West"

``` r
nlevels(directions)
```

    ## [1] 3

A factor can be ordered. This makes sense in the context of a ranking
such as a survey response, e.g. from ‘Strongly agree’ to ‘Strong
disagree’.

``` r
myorderedfactor <- factor(directions, levels = c("South", "West", "North"), ordered = TRUE)

levels(myorderedfactor)
```

    ## [1] "South" "West"  "North"

### Vectors

We can create 1D data structures called “vectors”.

``` r
1:10
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10

``` r
2*(1:10)
```

    ##  [1]  2  4  6  8 10 12 14 16 18 20

``` r
seq(0, 10, 2)
```

    ## [1]  0  2  4  6  8 10

``` r
directions <- c("North", "North", "West", "South")
class(directions)
```

    ## [1] "character"

### Matriz

A matrix in R is a two-dimensional rectangular data set and thus it can
be created using vector input to the matrix function

``` r
mat <- matrix (
c(2, 4, 3, 1, 5, 7),        # the data elements
nrow = 2,                   # no. of rows
ncol = 3,                   # no. of columns
byrow = TRUE)               # arranging it by row

print(mat)
```

    ##      [,1] [,2] [,3]
    ## [1,]    2    4    3
    ## [2,]    1    5    7

How to Access Elements of Matrix in R?

``` r
mat[2, 3]
```

    ## [1] 7

``` r
mat[2, ]
```

    ## [1] 1 5 7

``` r
mat[ ,3]
```

    ## [1] 3 7

### Dataframe

A data frame is being used for storing data tables, the vectors that are
contained in the form of a list in a data frame are of equal length.
