# Data Visualization

In this tutorial we will demonstrate some of the many options the
`ggplot2` package has for creating and customising graphs. We will use
R’s airquality dataset in the datasets package. This tutorial was adapted from **The Hitchhiker's Guide to Ggplot2**.

## Hello ggplot2

`ggplot2` is tidyverse's data visualization package. The gg in `ggplot2` stands for Grammar of Graphics.
It is inspired by the book Grammar of Graphics by **Leland Wilkinson**. A grammar of graphics is a tool 
that enables us to concisely describe the components of a graphic 

![tidyverse](https://raw.githubusercontent.com/XimenezJP/into_to_R/main/03%20Data%20Visualization/figures/tidyverse.png)<!-- -->

`ggplot()` is the main function in `ggplot2` and plots are constructed in layers. 
The structure of the code for plots can often be summarized as

``` r
ggplot(data = [dataset], mapping = aes(x = [x-variable], y = [y-variable])) +
   geom_xxx() +
   other options
```
For help with the ggplot2, see https://ggplot2.tidyverse.org

## Prerequisites
``` r
library(tidyverse)
```

## Dataset
``` r
data(airquality)
airquality$Month <- factor(airquality$Month,
                           labels = c("May", "Jun", "Jul", "Aug", "Sep"))
```

## Boxplot
``` r
boxplot <- ggplot(airquality, aes(x = Month, y = Ozone)) +
  geom_boxplot(colour = "darkblue", fill = "blue", size = 1, alpha = 0.2) +
  labs(y = "Mean ozone in\nparts per billion",
       title = "Boxplot of mean ozone by month") +
  theme_bw()

boxplot

ggsave("boxplot.pdf", width = 25, height = 25, units="cm", dpi = 300)
```
![Boxplot](https://raw.githubusercontent.com/XimenezJP/into_to_R/main/03%20Data%20Visualization/figures/boxplot.png)<!-- -->

## Histogram
``` r
histogram <- ggplot(airquality, aes(x = Ozone)) +
  geom_histogram(aes(y = ..count..), colour = "black", fill = "darkgreen", alpha = 0.4, binwidth = 5) +
  theme_bw() +
  labs(x = "Mean ozone in\nparts per billion",
       title = "Frequency histogram of mean ozone") 
histogram

ggsave("histogram.pdf", width = 25, height = 25, units="cm", dpi = 300)
``` 
![Histogram](https://raw.githubusercontent.com/XimenezJP/into_to_R/main/03%20Data%20Visualization/figures/histogram.png)<!-- -->

## Density Plot
``` r
density <- ggplot(airquality, aes(x = Ozone, fill = Month)) +
  geom_density(position = "stack", alpha = 0.6) +
  scale_x_continuous(breaks = seq(0, 200, 25),
                     limits=c(0, 200)) +
  labs(y = "Density",
       x = "Mean ozone in\nparts per billion",
       title = "Density plot of mean ozone") +
  theme_bw() +
  scale_fill_brewer(palette="Accent")
density

ggsave("density.pdf", width = 25, height = 25, units="cm", dpi = 300)
```
![Density Plot](https://raw.githubusercontent.com/XimenezJP/into_to_R/main/03%20Data%20Visualization/figures/density.png)<!-- -->

## Scatterplot
``` r
scatterplot <- ggplot(airquality, aes(x = Day, y = Ozone, size = Wind, fill = Month)) + 
  geom_point(shape = 21) +
  scale_x_continuous(breaks = seq(1, 31, 5)) + 
  scale_size(range = c(1, 10)) +
  theme_bw() +
  theme(legend.position = "bottom", legend.direction = "horizontal",
        legend.box = "vertical",
        legend.key.size = unit(0.5, "cm")) +
  labs(title = "Air Quality in New York by Day",
       subtitle = "Source: New York State Department of Conservation",
       x = "Day of the month", y = "Ozone (ppb)",
       size = "Wind Speed (mph) ", fill = "Months ")
scatterplot

ggsave("scatterplot.pdf", width = 25, height = 25, units="cm", dpi = 300)
```
![Scatterplot](https://raw.githubusercontent.com/XimenezJP/into_to_R/main/03%20Data%20Visualization/figures/scatterplot.png)<!-- -->

# Love
Love, true love, is why we’re here today. This is how the people at `VEME2021` show our love – **with statistical graphs**. 
This heart scatterplot was made in `R` using the `ggplot2` and `animation` packages

<p align="center">
  <img src="https://raw.githubusercontent.com/XimenezJP/into_to_R/main/03%20Data%20Visualization/figures/valentine.gif">
</p>

The code for this is [available here](https://cdn2.hubspot.net/hub/355318/file-2490959249-r/heart_graph.r), in an R file. 
Let us know if you use it for anything cool!
