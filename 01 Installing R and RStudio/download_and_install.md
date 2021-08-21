# Installing R and RStudio
To get started with R, you need to acquire your own copy. 
This appendix will show you how to download R as well as RStudio, a software application that makes R easier to use. 
You’ll go from downloading R to opening your first R session.
Both R and RStudio are free and easy to download.

## How to Download and Install R
R is maintained by an international team of developers who make the language available through the web page of 
[The Comprehensive R Archive Network](https://cran.r-project.org/). The top of the web page provides three links for downloading R. 

## Using R
R isn’t a program that you can open and start using, like Microsoft Word or Internet Explorer. 
Instead, R is a computer language, like C, C++, or UNIX. You use R by writing commands in the R language and asking your computer to interpret them. 
In the old days, people ran R code in a UNIX terminal window—as if they were hackers in a movie from the 1980s. 
Now almost everyone uses R with an application called RStudio.

![R](https://raw.githubusercontent.com/XimenezJP/into_to_R/main/01%20Installing%20R%20and%20RStudio/figures/R.png)<!-- -->

## RStudio
RStudio is an application like Microsoft Word—except that instead of helping you write in English, RStudio helps you write in R. 
The RStudio interface looks the same for Windows, Mac OS, and Linux. That will help me match the book to your personal experience.

You can [download RStudio](http://www.rstudio.com/ide) for free. Just click the `Download RStudio` 
button and follow the simple instructions that follow. 
Once you’ve installed RStudio, you can open it like any other program on your computer—usually by clicking an icon on your desktop.

When you open RStudio, a window appears with three panes in it, as in Figure A.1. The largest pane is a console window. 
This is where you’ll run your R code and see results. 
The console window is exactly what you’d see if you ran R from a UNIX console or the Windows or Mac GUIs. 
Everything else you see is unique to RStudio. 
Hidden in the other panes are a text editor, a graphics window, a debugger, a file manager, and much more. 
You’ll learn about these panes as they become useful throughout the course of this book.

![RStudio](https://raw.githubusercontent.com/XimenezJP/into_to_R/main/01%20Installing%20R%20and%20RStudio/figures/RStudio.png)<!-- -->

## R Packages
Many of R’s most useful functions do not come preloaded when you start R, but reside in packages that can be installed on top of R.
Usually the contents of an R package are all related to a single type of task, which the package helps solve. 
The real power driving the popularity of R today is the huge number of contributed packages providing algorithms and data types 
for a myriad of application realms.

### Installing Packages
To use an R package, you must first install it on your computer and then load it in your current R session. 
The easiest way to install an R package is with the `install.packages` R function. 
Open R and type the following into the command line:

``` r
install.packages("<package name>")
```

This will search for the specified package in the collection of packages hosted on the CRAN site. 
When R finds the package, it will download it into a libraries folder on your computer. 
R can access the package here in future R sessions without reinstalling it.

``` r
install.packages("ggplot2")
```

#### Loading Packages
Installing a package doesn’t immediately place its functions at your fingertips. 
It just places them on your computer. 
To use an R package, you next have to load it in your R session with the command:

``` r
library(<package name>)
```
Notice that the quotation marks have disappeared. You can use them if you like, but quotation marks are optional for the `library` command. 
(This is not true for the `install.packages` command).

`library` will make all of the package’s functions, data sets, and help files available to you until you close your current R session. 
The next time you begin an R session, you’ll have to reload the package with `library` if you want to use it, 
but you won’t have to reinstall it. You only have to install each package once.

``` r
library(ggplot2)
```
