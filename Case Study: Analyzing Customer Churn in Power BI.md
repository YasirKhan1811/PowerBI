# Case Study: Analyzing Customer Churn in Power BI

Disclaimer: This repository project is for my own practice and a reference for later use. For the real experience and certificate, get this hands-on course on [DataCamp](https://app.datacamp.com/learn/courses/case-study-analyzing-customer-churn-in-power-bi).

## Step 01: Data Check
The first step in any analysis is doing a data check. First, we will create **two measures** to check whether the count of customer ids is equal to the count of unique 
customer ids. This is to check if there are duplicate rows.

Create two new measures:
- No. of customers
- No. of unique customers

### Churn Rate
First convert the **Churn Label** column, containing Yes if customer churned otherwise No, into a new column called **Churned** that will contain 1 for Yes and 0 for No.
Apply IF-Statement to encode the Churn Label column with 1 and 0. The easiest way is to go to the Power Query Editor and add a conditional column.

Apply the following DAX formula to add a new measure **churn rate**:
The churn rate formula is: (Lost Customers ÷ Total Customers at the Start of Time Period) x 100

### Investigating Churn Reasons
Investigate the different reasons why customers churned. Next, create a column chart of number of customers churned per different reasons of churn.

**Churn Reasons** are grouped together in the **Churn Category** column. Create a bar chart to visualize churn category as % of grand total for count of churn label.

### Use maps to your advantage
Investigate the churn rate by state. The competitors launched aggressive promos in certain states, and Databel is wondering if it has impacted their customers. So use the map visual to view the churn rate by state.

Add churn rate, number of customers, and number of churned customers to the tooltip of the map visual. Add state to the location field. Use gradient color to easily identify the highest churn rate in a state by that color. 
It turns out that California has the highest churn rate of 63.24%.

## Step 02: Analyzing Demographics
Create a new column **Demographics** by categorizing **Senior**, **Under 30**, and **Other** into this one column using the following DAX:

**Demographics = IF('Databel - Data'[Senior] = "Yes", "Senior", IF('Databel - Data'[Under 30] = "Yes", "Under 30", "Other"))**

Create the following visuals to analyze the churn rate based on age demographics.
- Clustered Bar Chart
- Donut Chart
- Metrix Table

It turns out that the churn rate is significantly high among the senior customers, which is **38.22%**, higher than the overall churn rate. This suggests that it might be a good idea to analyze the customer age in general. Now lets create different age bins and make a **combo** chart visualizing the number of customers per bracket and their respective churn rates.

Add a conditional column for **Age Bins**

### Inspecting Groups
Databel offers group contracts to customers from same household. Benefit to the customers is that they have discounted rates. This is a great way for databel to grow their customer base. Analyze the customers that are part of the group if they really have lower phone bill and how it effects the churn rate?

Add a combo stacked column chart and include **No. of customers**, **Churn rate** as a line, and **Average of Monthly Charge**. It turns out that the bigger customer group has lower monthly phone bill and lower churn rate.

### SWITCH Function
Let's analyze the churn rate by type of subscription. There are 3 different contract types i.e. Month-to-Month, One Year, and Two Year in the contract type column.
Use the **SWITCH** function to convert the contract type column into contract category column where the subscription categories are like this: Month-to-Month -> **Monthly**, One Year and Two Year -> **Yearly**

By this, we are going to analyze the effect of subscription type on churn rate, and then the impact of gender and subscription type on churn rate.

How to use the **SWITCH Function**?
**SWITCH(expression, value, result, value, result, ...,else])**

From the multi-card visual of the churn rate by contract category, it turns out that customers with monthly contract churn at 46%, however, the yearly contract customers have significantly lower churn rate (6.6%).

The cluster-column chart of churn rate shows the role played by the customer gender in subscription type.

For example: Contract Category = SWITCH('Databel - Data'[Contract Type], "One Year", "Yearly", "Two Year", "Yearly", "Monthly")

### Unlimited Data Plan
It is believed that customers who are not on unlimited data plan are most likely to churn. So let's analyze this hypothesis by investigating how **Unlimited Data Plan** influences the churn rate.

### Analyze International Activity of Customers


### Contract Type
Databel also wants to improve its customer service since there have been some reported issues. Investigate three important topics related to customer service: the payment method, contract type, and how many months a person is a customer.

## Step 03: Dashboard
Creating a Cohesive Story





















