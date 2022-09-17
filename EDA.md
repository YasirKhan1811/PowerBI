# Exploratory Data Analysis
---
It's a method used to analyze and summarize data sets.

**Six steps to EDA:**

**1.** Understanding the data structure -> For example: knowing no. of rows, columns and dtypes

**2.** Identifying missing data -> it's important to know if the values are missing at random or there is a systematic pattern of missing data.

**3.** Describing the data: An important part of the Exploratory Data Analysis (EDA) process is simply describing the data. A great place to start is to 
**choose several variables of interest** and use basic descriptive statistics - minimum, median, mean, maximum, standard deviation - to learn more about how those 
variables range in values (e.g. their distributions).

The descriptive statistics is visualized with histograms and boxplots.
Normal distribution: Median = Mean. There is a symmetrical curve.
Skewed distributions:
  - Right-skewed - where the tail is to the right. Median < Mean
  - Left-skewed - where the tail is to the left. Median > Mean

**Imputation for missing data:** Missing data is a common occurrence when performing Exploratory Data Analysis on a new dataset. Rather than deleting missing records,
sometimes it's more useful to use an imputation technique to fill in values with an estimate of what they would be. This is especially true when the number of missing 
values is small.

To impute missing data (blank rows/observations), create a new column and use the following DAX formula to impute the missing value.

```dax
updated_price = IF(ISBLANK(column), median, column) 
```
  - Use **median** to replace missing data if numerical variable
  - Use **mode** to replace missing data if categorical variable

