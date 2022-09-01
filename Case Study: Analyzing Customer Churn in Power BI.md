# Case Study: Analyzing Customer Churn in Power BI

## Step 01: Data Check
The first step in any analysis is doing a data check. First, we will create **two measures** to check whether the count of customer ids is equal to the count of unique 
customer ids. This is to check if there are duplicate rows.

Create two new measures:
- No. of customers
- No. of unique customers

### Churn Rate
First convert the **Churn Label** column, containing Yes if customer churned otherwise No, into a new column called **Churned** that will contain 1 for Yes and 0 for No.
Apply IF-Statement to encode the Churn Label column. The easier way is to go to the Power Query Editor and add a conditional column.

Apply the following DAX formula to add a new measure **churn rate**:
The churn rate formula is: (Lost Customers ÷ Total Customers at the Start of Time Period) x 100

## Step 02: Investigating Churn Reasons
Investigate the different reasons why customers churned. Next, create a column chart of churn rate per different reasons of churn.

**Churn Reasons** are grouped together in the **Churn Category** column.
