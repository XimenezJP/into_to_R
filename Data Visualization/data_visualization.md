# Data Visualization

In this tutorial we will demonstrate some of the many options the
**ggplot2** package has for creating and customising graphs. We will use
R’s airquality dataset in the datasets package. This tutorial was adapted from **The Hitchhiker's Guide to Ggplot2**.

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

## Density
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
