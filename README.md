# Power BI

## DAX

Profit Margin Ratio = An important financial metric. Profit margin ratio compares the total profit to the total sales. It's always expressed in %.

Distinct Count: Counts the number of distinct values in a column

Measure = DISTINCTCOUNT(ColumnName)

For Example: SalesCount = DISTINCTCOUNT(Sales[OrderNo])


### Context in DAX Formulas
There are 3 types of context; row, filter, and query.

Iterator functions:
1. SUMX(table, expression)
2. AvgProfit = AVERAGEX(Sales, Sales[LinePrice] - Sales[LineCost])


**Calculate function:**
metric = CALCULATE(expression, filter, filter, ...)
2018_Bikes_Revenue = CALCULATE(SUM(Sales[LinePrice]), Sales[ProductCategory]="Bike", YEAR(Sales[OrderDate]) = 2018)

It calculates Revenue (total sales) of the product category 'bike' in the year 2018.

Goldvol21 = CALCULATE(SUM(Commodities[Volume]), Filter(Commodities, Commodities[Symbol] = 'Gold'), Filter(Commodities, YEAR(Commodities[Date] = 2021))


**Variables**
Gold21vs20 = 
VAR Goldvol20 = CALCULATE(SUM(Commodities[Volume]), Filter(Commodities, Commodities[Symbol] = 'Gold'), Filter(Commodities, YEAR(Commodities[Date] = 2020))
RETURN DIVIDE([Goldvol21] - Goldvol20, Goldvol20)

### Working with Dates

For Example: 22/08/2022 09:34

Date and Time Functions:
- YEAR(date) -> 2022
- QUARTER(date) -> 3
- MONTH(datetime) -> 08
- DAY(datetime) -> 22

Format Function:
- Weekday: FORMAT(date, "dddd") -> Monday
- Time: Format(date, "h:nn:ss") -> "09:34:00"

Time Intelligence Functions:
- LASTDATE()
- DATESBETWEEN()
- DATEADD()

Creating a Dedicated Date Table:

Dates = CALENDAR(MIN(Date), MAX(Date])
Returns a column of dates from start day of the transaction table until the last day

To return day of a date column (dd-mm-yyyy)
DayNo = DAY(Date)

To return a short name of a day from date (dd-mm-yyyy) -> Mon, Tue, Wed etc.
DayShortName = FORMAT(<Date>, "DDD")
  
**The importance of a date table**
Issues of relying on only dates from transactional tables:
- Gaps in dates i.e no sales made on 20th September
- Returns wrong results when using time-intelligence functions
    - No error, wrong result
    - Difficult to troubleshoot

A dedicated date table is highly recommended for accurate reporting using time intelligence functions.

**DATEDIFF**
Returns the number of units between two dates as defined in <interval>
DATEDIFF(<Date1>, <Date2>, <Interval>)
  
**DATEADD**
DATEADD(<dates>, <number_of_intervals>, <interval>)
  
Quick Measures: Powerful feature in DAX that enables you to carry out complex calculations without needing to write the code from scratch ([source link](https://docs.microsoft.com/en-us/power-bi/transform-model/desktop-quick-measures))
