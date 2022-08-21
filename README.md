# Power BI

## DAX

2018 Bikes Revenue = CALCULATE(SUM(Sales[LinePrice]), Sales[ProductCategory]="Bike", YEAR(Sales[OrderDate]) = 2018)

Goldvol21 = CALCULATE(SUM(Commodities[Volume]), Filter(Commodities, Commodities[Symbol] = 'Gold'), Filter(Commodities, YEAR(Commodities[Date] = 2021))

Gold21vs20 = 
VAR Goldvol20 = CALCULATE(SUM(Commodities[Volume]), Filter(Commodities, Commodities[Symbol] = 'Gold'), Filter(Commodities, YEAR(Commodities[Date] = 2020))
RETURN DIVIDE([Goldvol21] - Goldvol20, Goldvol20)

### Working with Dates
Dates = CALENDAR(MIN(Sales[OrderDate]), MAX(Sales[OrderDate])
Returns a column of dates

To return day of a date column (dd-mm-yyyy)
DayNo = DAY(<Date>)

To return a short name of a date (dd-mm-yyyy) -> Mon, Tue, Wed etc.
DayShortName = FORMAT(<Date>, "DDD")

**DATEDIFF**
Returns the number of units between two dates as defined in <interval>
DATEDIFF(<Date1>, <Date2>, <Interval>)

Quick Measures: Powerful measures in DAX that enables you to carry out complex calculations without needing to write the code from scratch ([source link](https://docs.microsoft.com/en-us/power-bi/transform-model/desktop-quick-measures))


  
  
  
  
  
  
  
