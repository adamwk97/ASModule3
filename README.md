![Data table](https://i.gyazo.com/dbf0a8561dc44e6497fd09b126804657.png)
# Module 3 Assignment - Airport Screening Analysis

## What is the Association Between the Number of Airport Screeners and Security Violations?

The association between these two variables is the assumption that the number of airport security screeners influences, in one way or another, the amount of security violations that were detected. Each of these 20 cases is an independent study with different amounts of airport screeners as well as violations. The goal of this assignment is to conduct analysis on these two variables and determine if there is any correlation between the number of screeners and the amount of violations detected.
```{r importdata, echo=TRUE}
df <- read.csv("https://www.dropbox.com/s/e51igg1rcp40kub/Module%203%20data.csv?dl=1", row.names=NULL)


```



## Calculating Pearson's Correlation Coefficient

```{r pearsoncoef, echo=TRUE}
dfpearson = cor(x = df$pre.boarding.screeners,y = df$security.violations.detected, method="pearson")
dfpearson

```

Pearson's coefficient is a measure of the linear correlation of two values. When drawing a line of best fit on a scatterplot, Pearson's coefficient is the measure of how far the data points are from the line. In this case, the value of Pearson's coefficient, r, between the number of pre-boarding screeners and security violations is a value of 0.838. This implies that there is a very strong correlation between the number of pre-boarding screeners and the number of violations that were detected. This means that the number of violations detected is largely influenced by the number of screeners.


## Calculating Spearman's Rank Coefficient

```{r spearmancoef, echo=TRUE}
dfspearman = cor(x = df$pre.boarding.screeners,y = df$security.violations.detected, method="spearman")
dfspearman

```
While Spearman's coefficient on the other hand is also a measure of correlation, it does not take linearity into account. On a scatterplot, a line of best fit will be drawn, however it does not necessarily have to be linear, and how far the data points are from the line determines the correlation. In this case, the value of Spearman's coefficient is .758 indicating again that there is a heavy correlation between the number of pre-boarding screeners and the number of violations detected.

## Scatterplot

As we can see, the scaterplot is quite linear and the line of best fit is very plain to see. This plot shows us that there is indeed heavy correlation between the two variables tested and it agrees with our earlier inferences alongside Pearson and Spearman's coefficients.

```{r scatterplot, echo=TRUE}
library(ggplot2)

dfscatter2 = ggplot(df, aes(x = df$pre.boarding.screeners,y = df$security.violations.detected))+geom_point()+geom_smooth(method=lm,se=FALSE)+labs(x = "Pre-Boarding Screeners",y="Violations Detected")
dfscatter2


```
