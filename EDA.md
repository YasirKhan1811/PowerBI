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

### Distributions and Outliers
What are distributions?
"Set of all possible values of the variable and the associated frequencies. OR the number of times each observation/measurement of a varaible appears in the set of values."

Histograms are used for visualizing distributions. The bins of the histogram are represented as bars or intervals of values.

There are formulas for calculating the optimal number of bins. Starting with **25** bins for datasets with more than 100 observations is a good place to start.

  - Histograms: mean = median is a normal distribution
  - Histograms: if tail of the distribution is towards right - Right-skewed distribution
  - Histograms: if tail of the distribution is towards left - Left-skewed distribution

How wide the distribution is indicates the spread of data around those central points.
  - If the distribution is wide/flat, there is a larger variability (std deviation) from the average
  - If the spread is narrow, the variability and std are smaller

**Percentiles**
Percentiles are values at which a percentage of observations fall at or below. For example: the **50th** percentile (i.e. median) means that the point/value in the observations where 50% of the values lie below it.
- 25th percentile is the first quartile
- 50th percentile is the second quartile
- 75th percentile is the third quartile
- The difference between the 75th percentile and 25th percentile make up the IQR.

Finding outliers: There are two common methods for quantitatively finding outliers in the dataset.
1. Using std deviation (this method is suited for normal distributions):
    lower = -3 * std
    uppwer = +3 * std
    outlier when: value < lower OR upper < value

2. Using IQR (the most robust and common way):
    lower = 25th - (1.5*IQR)
    upper = 75th + (1.5*IQR)
    outlier when: value < lower OR upper < value

**Addressing Outliers**
  - Remove the observations
  - Imputations
  - Winsorizing: 
    - if value < 5th percentile THEN value = 5th percentile 
    - if value > 95th percentile THEN value = 95th percentile
 
**EDA with Categorical Variables**
- The first place to start is visualizing frequencies of categorical variables. For example: No. of Participants by Age Group. It depicts observations per value of a categorical variable via **column/bar** chart.
- OR visualizing percentage of values/observations by categories, for example, plotting %age of participants by age group via a **donut** chart.
- Another way is to view proportions of values across multiple categorical variables, for example, through 100% **stacked column charts**.
- Categorical variables with descriptive statistics.
- Using **box plots** for analyzing the distribution of a continuous variable. Also it can be used to plot continuous variable across categories.
- Creating new variables - An important part, or result, of EDA is creating new variables, both continuous and categorical. Doing so can help further refine an analysis or visualization. This process is often referred to as **data transformation or mutation**. For example, converting the age column into four "Age Group" categories - Teen, Early Adult, Adult, and Middle Age.

**Histograms vs. box plots**
Histograms and box plots are both great for visualizing distributions of a continuous variable. Each has their strengths. Therefore, which one we choose for our EDA depends on the question being asked.

| **Box Plot** | **Histograms** |
| :----: | :----: |
| Better view of distribution statistics | Better view of underlying distribution |
| Indicates Median | Frequency of values |
| Outlines 1st, 2nd, and 3rd Quartiles | Intervals/bins of values |
| Lines indicating lower and upper bounds for outliers | Most commonly occuring value(s) |

### Relationship b/w Continuous Variables
Scatter plots are fantastic tools for visualizing relationships between variables. They also provide insights into the direction (i.e., +, -, or neutral) and potential strength (-1 -> 0 -> 1) of the relationship.

---

## Trend Analysis

### Decomposition Tree:
    A method for breaking down a target variable by multiple dimensions or variables to determine resulting influence.
    Use cases:
             - Ad Hoc exploration
             - Root cause analysis
             - Identifying influential variables



























