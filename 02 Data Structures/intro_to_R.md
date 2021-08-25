# Data Structures

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

    ## [1] "/Users/joaopaulo/Documents/Codes/R Scripts/VEME_2021"

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

### Character

Strings are known as “character” in R. Use the double quotes `"` 
to wrap around the string

``` r
myname <- "João"
```

We can use the `class()` function to see what data type it is

``` r
class(myname)
```

    ## [1] "character"

### Numbers
``` r
1 + 1
3000000
class(0.00001)
```

    ## [1] "numeric"

### Logical (True/False)
``` r
class(TRUE)
```

    ## [1] "logical"

``` r
3 > 4
```

    ## [1] FALSE

### Vectors

We can create 1D data structures called vectors. A vector is a sequence of data elements of the same basic type. 
Here is a vector containing numeric values
``` r
1:10
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10

``` r
seq(0, 10, 2)
```

    ## [1]  0  2  4  6  8 10
    
A vector can contain character strings.
``` r
directions <- c("North", "North", "West", "South")
class(directions)
``` 
    ## [1] "character"

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

``` r
#install.packages("tidyverse")
```
``` r
library(tidyverse)
```
``` r
data(starwars)
starwars
```

    # A tibble: 87 x 14
    name               height  mass hair_color    skin_color  eye_color birth_year sex    gender    homeworld species films     vehicles  starships
    <chr>               <int> <dbl> <chr>         <chr>       <chr>          <dbl> <chr>  <chr>     <chr>     <chr>   <list>    <list>    <list>   
    1 Luke Skywalker        172    77 blond         fair        blue            19   male   masculine Tatooine  Human   <chr [5]> <chr [2]> <chr [2]>
    2 C-3PO                 167    75 NA            gold        yellow         112   none   masculine Tatooine  Droid   <chr [6]> <chr [0]> <chr [0]>
    3 R2-D2                  96    32 NA            white, blue red             33   none   masculine Naboo     Droid   <chr [7]> <chr [0]> <chr [0]>
    4 Darth Vader           202   136 none          white       yellow          41.9 male   masculine Tatooine  Human   <chr [4]> <chr [0]> <chr [1]>
    5 Leia Organa           150    49 brown         light       brown           19   female feminine  Alderaan  Human   <chr [5]> <chr [1]> <chr [0]>
    6 Owen Lars             178   120 brown, grey   light       blue            52   male   masculine Tatooine  Human   <chr [3]> <chr [0]> <chr [0]>
    7 Beru Whitesun lars    165    75 brown         light       blue            47   female feminine  Tatooine  Human   <chr [3]> <chr [0]> <chr [0]>
    8 R5-D4                  97    32 NA            white, red  red             NA   none   masculine Tatooine  Droid   <chr [1]> <chr [0]> <chr [0]>
    9 Biggs Darklighter     183    84 black         light       brown           24   male   masculine Tatooine  Human   <chr [1]> <chr [0]> <chr [1]>
    10 Obi-Wan Kenobi       182    77 auburn, white fair        blue-gray       57   male   masculine Stewjon   Human   <chr [6]> <chr [1]> <chr [5]>

#### Filter rows with `filter()`

`filter()` allows you to select a subset of rows in a data frame. Like all single verbs, the first argument is the tibble (or data frame). The second and subsequent arguments refer to variables within that data frame, selecting rows where the expression is `TRUE`.

For example, we can select all character with light skin color and brown eyes with:

```{r}
starwars %>% filter(skin_color == "light", eye_color == "brown")
```
    ## A tibble: 7 x 14
    name              height  mass hair_color skin_color eye_color birth_year sex    gender    homeworld species films     vehicles  starships
     <chr>              <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr>  <chr>     <chr>     <chr>   <list>    <list>    <list>   
    1 Leia Organa          150    49 brown      light      brown             19 female feminine  Alderaan  Human   <chr [5]> <chr [1]> <chr [0]>
    2 Biggs Darklighter    183    84 black      light      brown             24 male   masculine Tatooine  Human   <chr [1]> <chr [0]> <chr [1]>
    3 Cordé                157    NA brown      light      brown             NA female feminine  Naboo     Human   <chr [1]> <chr [0]> <chr [0]>
    4 Dormé                165    NA brown      light      brown             NA female feminine  Naboo     Human   <chr [1]> <chr [0]> <chr [0]>
    5 Raymus Antilles      188    79 brown      light      brown             NA male   masculine Alderaan  Human   <chr [2]> <chr [0]> <chr [0]>
    6 Poe Dameron           NA    NA brown      light      brown             NA male   masculine NA        Human   <chr [1]> <chr [0]> <chr [1]>
    7 Padmé Amidala        165    45 brown      light      brown             46 female feminine  Naboo     Human   <chr [3]> <chr [0]> <chr [3]>

This is roughly equivalent to this base R code:

```{r, eval = FALSE}
starwars[starwars$skin_color == "light" & starwars$eye_color == "brown", ]
```
We can also select a Jedi Hunter:

``` r 
starwars %>% filter(homeworld == "Dathomir")
```
    # A tibble: 1 x 14
    name       height  mass hair_color skin_color eye_color birth_year sex   gender    homeworld species films     vehicles  starships
    <chr>       <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr>     <chr>     <chr>   <list>    <list>    <list>   
    1 Darth Maul    175    80 none       red        yellow            54 male  masculine Dathomir  Zabrak  <chr [1]> <chr [1]> <chr [1]>

<p align="center">
  <img src="https://raw.githubusercontent.com/XimenezJP/into_to_R/main/02%20Data%20Structures/figures/darth_maul.png" width="400" height="500">
</p>

#### Arrange rows with `arrange()`

`arrange()` works similarly to `filter()` except that instead of filtering or selecting rows, it reorders them. It takes a data frame, and a set of column names (or more complicated expressions) to order by. If you provide more than one column name, each additional column will be used to break ties in the values of preceding columns:

``` r
starwars %>% arrange(height, mass)
```
    # A tibble: 87 x 14
    name                  height  mass hair_color skin_color  eye_color birth_year sex   gender    homeworld   species        films     vehicles  starships
    <chr>                  <int> <dbl> <chr>      <chr>       <chr>          <dbl> <chr> <chr>     <chr>       <chr>          <list>    <list>    <list>   
    1 Yoda                      66    17 white      green       brown            896 male  masculine NA          Yoda's species <chr [5]> <chr [0]> <chr [0]>
    2 Ratts Tyerell             79    15 none       grey, blue  unknown           NA male  masculine Aleen Minor Aleena         <chr [1]> <chr [0]> <chr [0]>
    3 Wicket Systri Warrick     88    20 brown      brown       brown              8 male  masculine Endor       Ewok           <chr [1]> <chr [0]> <chr [0]>
    4 Dud Bolt                  94    45 none       blue, grey  yellow            NA male  masculine Vulpter     Vulptereen     <chr [1]> <chr [0]> <chr [0]>
    5 R2-D2                     96    32 NA         white, blue red               33 none  masculine Naboo       Droid          <chr [7]> <chr [0]> <chr [0]>
    6 R4-P17                    96    NA none       silver, red red, blue         NA none  feminine  NA          Droid          <chr [2]> <chr [0]> <chr [0]>
    7 R5-D4                     97    32 NA         white, red  red               NA none  masculine Tatooine    Droid          <chr [1]> <chr [0]> <chr [0]>
    8 Sebulba                  112    40 none       grey, red   orange            NA male  masculine Malastare   Dug            <chr [1]> <chr [0]> <chr [0]>
    9 Gasgano                  122    NA none       white, blue black             NA male  masculine Troiken     Xexto          <chr [1]> <chr [0]> <chr [0]>
    10 Watto                   137    NA black      blue, grey  yellow            NA male  masculine Toydaria    Toydarian      <chr [2]> <chr [0]> <chr [0]>

Use `desc()` to order a column in descending order:

``` r
starwars %>% arrange(desc(mass))
```
    # A tibble: 87 x 14
    name              height  mass hair_color  skin_color      eye_color    birth_year sex          gender    homeworld species   films   vehicles starships
    <chr>              <int> <dbl> <chr>       <chr>           <chr>             <dbl> <chr>        <chr>     <chr>     <chr>     <list>  <list>   <list>   
    1 Jabba Desilijic …    175  1358 NA          green-tan, bro… orange            600   hermaphrodi… masculine Nal Hutta Hutt      <chr [… <chr [0… <chr [0]>
    2 Grievous             216   159 none        brown, white    green, yell…       NA   male         masculine Kalee     Kaleesh   <chr [… <chr [1… <chr [1]>
    3 IG-88                200   140 none        metal           red                15   none         masculine NA        Droid     <chr [… <chr [0… <chr [0]>
    4 Darth Vader          202   136 none        white           yellow             41.9 male         masculine Tatooine  Human     <chr [… <chr [0… <chr [1]>
    5 Tarfful              234   136 brown       brown           blue               NA   male         masculine Kashyyyk  Wookiee   <chr [… <chr [0… <chr [0]>
    6 Owen Lars            178   120 brown, grey light           blue               52   male         masculine Tatooine  Human     <chr [… <chr [0… <chr [0]>
    7 Bossk                190   113 none        green           red                53   male         masculine Trandosha Trandosh… <chr [… <chr [0… <chr [0]>
    8 Chewbacca            228   112 brown       unknown         blue              200   male         masculine Kashyyyk  Wookiee   <chr [… <chr [1… <chr [2]>
    9 Jek Tono Porkins     180   110 brown       fair            blue               NA   male         masculine Bestine … Human     <chr [… <chr [0… <chr [1]>
    10 Dexter Jettster     198   102 none        brown           yellow             NA   male         masculine Ojom      Besalisk  <chr [… <chr [0… <chr [0]>

#### Select columns with `select()`

Often you work with large datasets with many columns but only a few are actually of interest to you. `select()` allows you to rapidly zoom in on a useful subset using operations that usually only work on numeric variable positions:

``` r
# Select columns by name
starwars %>% select(name, height, mass)
```
    # A tibble: 87 x 3
    name               height  mass
    <chr>               <int> <dbl>
    1 Luke Skywalker        172    77
    2 C-3PO                 167    75
    3 R2-D2                  96    32
    4 Darth Vader           202   136
    5 Leia Organa           150    49
    6 Owen Lars             178   120
    7 Beru Whitesun lars    165    75
    8 R5-D4                  97    32
    9 Biggs Darklighter     183    84
    10 Obi-Wan Kenobi       182    77

#### Rename columns with `rename()`

You can rename variables with `rename()` by using named arguments:

``` r
starwars %>% rename(home_world = homeworld)
```
    # A tibble: 87 x 14
    name               height  mass hair_color    skin_color  eye_color birth_year sex    gender    home_world species films     vehicles  starships
    <chr>               <int> <dbl> <chr>         <chr>       <chr>          <dbl> <chr>  <chr>     <chr>      <chr>   <list>    <list>    <list>   
    1 Luke Skywalker        172    77 blond         fair        blue            19   male   masculine Tatooine   Human   <chr [5]> <chr [2]> <chr [2]>
    2 C-3PO                 167    75 NA            gold        yellow         112   none   masculine Tatooine   Droid   <chr [6]> <chr [0]> <chr [0]>
    3 R2-D2                  96    32 NA            white, blue red             33   none   masculine Naboo      Droid   <chr [7]> <chr [0]> <chr [0]>
    4 Darth Vader           202   136 none          white       yellow          41.9 male   masculine Tatooine   Human   <chr [4]> <chr [0]> <chr [1]>
    5 Leia Organa           150    49 brown         light       brown           19   female feminine  Alderaan   Human   <chr [5]> <chr [1]> <chr [0]>
    6 Owen Lars             178   120 brown, grey   light       blue            52   male   masculine Tatooine   Human   <chr [3]> <chr [0]> <chr [0]>
    7 Beru Whitesun lars    165    75 brown         light       blue            47   female feminine  Tatooine   Human   <chr [3]> <chr [0]> <chr [0]>
    8 R5-D4                  97    32 NA            white, red  red             NA   none   masculine Tatooine   Droid   <chr [1]> <chr [0]> <chr [0]>
    9 Biggs Darklighter     183    84 black         light       brown           24   male   masculine Tatooine   Human   <chr [1]> <chr [0]> <chr [1]>
    10 Obi-Wan Kenobi       182    77 auburn, white fair        blue-gray       57   male   masculine Stewjon    Human   <chr [6]> <chr [1]> <chr [5]>

#### Add new columns with `mutate()`

Besides selecting sets of existing columns, it's often useful to add new columns that are functions of existing columns. This is the job of `mutate()`:

``` r
starwars %>% mutate(height_m = height / 100)
```

We can't see the height in meters we just calculated, but we can fix that using a select command.

``` r
starwars %>%
  mutate(height_m = height / 100) %>%
  select(name, height_m, height, everything())
```
    # A tibble: 87 x 15
    name               height_m height  mass hair_color    skin_color  eye_color birth_year sex    gender    homeworld species films     vehicles  starships
    <chr>                 <dbl>  <int> <dbl> <chr>         <chr>       <chr>          <dbl> <chr>  <chr>     <chr>     <chr>   <list>    <list>    <list>   
    1 Luke Skywalker         1.72    172    77 blond         fair        blue            19   male   masculine Tatooine  Human   <chr [5]> <chr [2]> <chr [2]>
    2 C-3PO                  1.67    167    75 NA            gold        yellow         112   none   masculine Tatooine  Droid   <chr [6]> <chr [0]> <chr [0]>
    3 R2-D2                  0.96     96    32 NA            white, blue red             33   none   masculine Naboo     Droid   <chr [7]> <chr [0]> <chr [0]>
    4 Darth Vader            2.02    202   136 none          white       yellow          41.9 male   masculine Tatooine  Human   <chr [4]> <chr [0]> <chr [1]>
    5 Leia Organa            1.5     150    49 brown         light       brown           19   female feminine  Alderaan  Human   <chr [5]> <chr [1]> <chr [0]>
    6 Owen Lars              1.78    178   120 brown, grey   light       blue            52   male   masculine Tatooine  Human   <chr [3]> <chr [0]> <chr [0]>
    7 Beru Whitesun lars     1.65    165    75 brown         light       blue            47   female feminine  Tatooine  Human   <chr [3]> <chr [0]> <chr [0]>
    8 R5-D4                  0.97     97    32 NA            white, red  red             NA   none   masculine Tatooine  Droid   <chr [1]> <chr [0]> <chr [0]>
    9 Biggs Darklighter      1.83    183    84 black         light       brown           24   male   masculine Tatooine  Human   <chr [1]> <chr [0]> <chr [1]>
    10 Obi-Wan Kenobi        1.82    182    77 auburn, white fair        blue-gray       57   male   masculine Stewjon   Human   <chr [6]> <chr [1]> <chr [5]>

#### Summarise values with `summarise()`

The last verb is `summarise()`. It collapses a data frame to a single row.

``` r
starwars %>% summarise(height = mean(height, na.rm = TRUE))
```

It's not that useful until we learn the `group_by()` verb below.

``` r
starwars %>%
  group_by(species, sex) %>%
  select(height, mass) %>%
  summarise(
    height = mean(height, na.rm = TRUE),
    mass = mean(mass, na.rm = TRUE))
```

#### Save and Open Dataframe

We will create a new dataframe. 

``` r
starwars_df <- starwars %>%
  mutate(height_m = height / 100,
         BMI = mass / (height_m^2)) %>%
  select(name, BMI, height_m, everything(), -c(films, vehicles, starships)) 
``` 
Now let’s try saving this data set as a csv to our computer. We will do this using the `write_csv` function. This function has two main arguments: `x` and `path`. The `x` argument is the data set that you want to save, which in this case is the `starwars_df` data set that we just saved to our environment. The `path` argument is the file path where you want to save the file. The end of the `path` argument is the name that you want to use for the file.

``` r
write_csv(starwars_df, file = "starwars_df.csv")
```

Now let’s practice with `read_csv` by reading this file back into R. The `read_csv` has one main argument: file. The file argument is the file path to the file that you are wanting to read into R.

``` r
df_full <- read_csv("starwars_df.csv")
```

### Data visualization
"The simple graph has brought more information to the data analyst’s mind than any other device." — **John Tukey**
Data visualization is the creation and study of the visual representation of data. 
There are many tools for visualizing data (R is one of them), and many approaches/systems within R for making data visualizations.
`ggplot2` is the one we will use

``` r
ggplot(data = starwars, mapping = aes(x = height, y = mass)) +
  geom_point()
``` 
![Jabba](https://raw.githubusercontent.com/XimenezJP/into_to_R/main/02%20Data%20Structures/figures/jabba.png)<!-- -->
