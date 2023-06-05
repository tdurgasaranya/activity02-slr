---
Durga Saranya Tummalapalli
---

---
title: "Activity 2"
output: github_document
---

```{r global-options, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

- The data is obtained from this following site:
[Datasite](https://vitalflux.com/linear-regression-datasets-csv-excel/)
- I chose this Medical Cost Personal Dataset
[URL](https://raw.githubusercontent.com/stedy/Machine-Learning-with-R-datasets/master/insurance.csv)

- Description: Predicting medical costs based on patient information

```{r global-options, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

- The data is obtained from this following site:
![Datasite](https://vitalflux.com/linear-regression-datasets-csv-excel/)
- I chose this Medical Cost Personal Dataset
[URL](https://raw.githubusercontent.com/stedy/Machine-Learning-with-R-datasets/master/insurance.csv)

- Description: Predicting medical costs based on patient information
- Load the packages and check libraries
- Load the dataset from local machine after downloading from a site as the link provided from above
- Read the csv file accordingly
- Determine the dimensions of the dataset with below mentioned code

## Load the packages and Libraries

```{r}
library(tidyverse)
library(tidymodels)
library(ggplot2)
library(stats)
library(dplyr)

```

## Load the datasets csv file and read the file

```{r}
library(readr)
Test= read_csv("https://raw.githubusercontent.com/stedy/Machine-Learning-with-R-datasets/master/insurance.csv")


```

## Dimensions of the dataset

```{r}

dimensions <- dim(data)
head(Test)


```
> statsr::plot_ss(x = bmi, y = charges , data = Test)
                                
##Call: lm(formula = y ~ x, data = pts)

##Coefficients:
##(Intercept)            x  
##    41878.5        -26.5  

- Sum of Squares:  1.230869e+12

> statsr::plot_ss(x = bmi, y = age , data = Test)
                                
## Call: lm(formula = y ~ x, data = pts)

## Coefficients:
## (Intercept)            x  
##    125.007       -2.703  

- Sum of Squares:  706230.6

### smallest sum of squares

```{r}

# Fitting a linear regression model
Reg <- lm(age ~ bmi, data = Test)

# Obtain the smallest sum of squares (residual sum of squares)
smallest_ss <- sum(Reg$residuals^2)
smallest_ss


```
- The smallest sum of squares can be found using a linear regression model and with help of lm functionality.

### Largest sum of squares

```{r}

# Fitting a linear regression model
Reg <- lm(age ~ bmi, data = Test)

# Calculate the total sum of squares (TSS)
tss <- sum((Test$bmi - mean(Test$bmi))^2)

# Obtain the largest sum of squares (explained sum of squares)
largest_ss <- sum(Reg$fitted.values^2)

# Calculate the residual sum of squares (RSS)
rss <- sum(Reg$residuals^2)

# Calculate the unexplained sum of squares (ESS)
ess <- largest_ss - rss

# Calculate the proportion of explained variance (R-squared)
r_squared <- ess / tss

largest_ss

```

### summary of LR model of the data

```{r}
# Fit our specification to our data
slr_mod <- lm_spec %>% 
  fit(bmi ~ charges, data = Test)

# View the summary of the model
summary(slr_mod)

```
