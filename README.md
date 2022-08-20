# Power BI

## DAX
Goldvol21 = CALCULATE(SUM(Commodities[Volume]), Filter(Commodities, Commodities[Symbol] = 'Gold'), Filter(Commodities, YEAR(Commodities[Date] = 2021))

Gold21vs20 = 
VAR Goldvol20 = CALCULATE(SUM(Commodities[Volume]), Filter(Commodities, Commodities[Symbol] = 'Gold'), Filter(Commodities, YEAR(Commodities[Date] = 2020))
RETURN DIVIDE([Goldvol21] - Goldvol20, Goldvol20)
